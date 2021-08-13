# Akıllı Kontrat Yazma

Yazdığımız akıllı sözleşme, temel bir otomatik aboneliktir. Kullanıcı, belirli sayıda bloktan sonra otomatik olarak kullanılacak fonları yatırabilir. Kullanıcı her "yeniden abone olduğunda", onlara bazı jetonlar verilir. Bir kullanıcı ne kadar çok kez yeniden abone olursa, her yeniden abone olduğunda o kadar çok jeton verilir.

"Contracts" klasörünün içine "Scheduler.sol" dosyasını oluşturun ve aşağıdaki kodu yapıştırın:

```text
pragma solidity ^0.6.0;

abstract contract Scheduler {
    // Schedule a contract call.
    function scheduleCall(
        address contract_address, // The contract address to be called in future.
        uint256 value, // How much native token to send alone with the call.
        uint256 gas_limit, // The gas limit for the call. Corresponding fee will be reserved upfront and refunded after call.
        uint256 storage_limit, // The storage limit for the call. Corresponding fee will be reserved upfront and refunded after call.
        uint256 min_delay, // Minimum number of blocks before the scheduled call will be called.
        bytes memory input_data // The input data to the call.
    )
    virtual
    public
    returns (uint256, uint256); // Returns a task id that can be used to cancel or reschedule call.
}
```

Bu dosya, zamanlayıcı akıllı sözleşmesini ve onu kullanmak için ona hangi argümanları sağlamanız gerektiğini açıklar. Ancak zamanlayıcı nasıl çalışır?

Acala EVM, zincir düzeyinde Acala ile etkileşime giren önceden derlenmiş akıllı sözleşmeler kullanarak benzersiz zincir üstü özelliklerini EVM'ye entegre eder. Bu, Ethereum'da imkansız olacak yeni özellikler eklememize izin verirken, geliştiricilerin bu özelliklerden yararlanan dapp'ler oluşturmak için mevcut kodu ve araçları kullanmasına izin verir. Bu da, önceden derlenmiş akıllı sözleşmeler, Acala EVM'de statik, bilinen adreslere sahiptir ve bunları kodunuzda kullanmayı inanılmaz derecede kolaylaştırır.

## Yeni Sözleşme Oluşturma

`Contracts` klasörümüz içerisinde `Subscription.sol` dosyası oluşturarak akıllı sözleşme dosyamızı oluşturalım. İçinde aşağıdaki kodu ekleyin:

```text
pragma solidity ^0.6.0;

import "./Scheduler.sol";

contract SubscriptionToken {
  Scheduler constant scheduler = Scheduler(0x0000000000000000000000000000000000000808);
}
```

Burada, 'Scheduler' akıllı sözleşmesini tanımlayan ve 'scheduler'ımızı onun adresine yönlendiren soyut sınıfı içe aktardığımızı görebilirsiniz. Yine, bu, statik bir adrese sahip önceden derlenmiş bir akıllı sözleşmedir. Bu adreste her zaman zincirde yaşayacak, kendi sürümünüzü dağıtmanıza gerek yok.

Ardından, bazı durum değişkenlerini ayarlayalım ve bir kurucu oluşturalım. Sözleşmeye aşağıdakileri ekleyin:

```text
contract SubscriptionToken {
  contract SubscriptionToken {
    Scheduler constant scheduler = Scheduler(0x0000000000000000000000000000000000000808);

  address payable public owner;
  uint public subscriptionPrice;
  uint public subscriptionPeriod;

  mapping (address => uint) public balanceOf;
  mapping (address => uint) public subTokensOf;
  mapping (address => uint) public periodSubscribed;

  constructor(uint _subscriptionPrice, uint _subscriptionPeriod) public payable {
    owner = msg.sender;
    subscriptionPrice = _subscriptionPrice;
    subscriptionPeriod = _subscriptionPeriod;
  }
}
```

Burada 6 durum değişkeni ekledik. Bunları tek tek inceleyelim:

1. `sahip`: Abonelikleri alacak sözleşmenin sahibi
2. `subscriptionPrice`: Abone olma/yeniden abone olma fiyatı
3. `subscriptionPeriod`: Bir kullanıcının otomatik olarak yeniden abone olmasından önceki blok sayısı
4. "balanceOf": Bir kullanıcının bakiyesindeki yeniden abonelik maliyeti için kullanılacak yerel jeton sayısı
5. `subTokensOf`: Bir kullanıcının aldığı abonelik jetonlarının sayısı
6. 'periodSubscribed': Bir kullanıcının abone olduğu 'subscriptionPeriod' sayısı. Bu, bir kullanıcının yeniden abone olduktan sonra kaç tane abonelik jetonu alacağını etkiler.

Yapıcı kendini açıklayıcıdır, tek yaptığı sözleşme için ilk üç durum değişkenini ayarlamaktır.

Ardından "abone ol" ve "abonelikten çık" işlevlerini ekleyelim:

```text
contract Subscription {
  ...

  function subscribe() public payable {
    require(periodSubscribed[msg.sender] == 0, "Already subscribed");
    require(msg.value > subscriptionPrice, "Not enough to subscribe");

    uint256 _depositAmount = msg.value - subscriptionPrice;

    balanceOf[msg.sender] = _depositAmount;
    periodSubscribed[msg.sender] = 1;
    subTokensOf[msg.sender] = 1;

    owner.transfer(subscriptionPrice);

    scheduler.scheduleCall(address(this), 0, 50000, 100, 10, abi.encodeWithSignature("pay(address)", msg.sender));
  }

  function unsubscribe() public {
    periodSubscribed[msg.sender] = 0;
  }
}
```

Burada, "abone ol" işlevi, kullanıcının en az bir kez abone olmak için akıllı sözleşmeye yeterli para yatırmasını ve kullanıcının henüz abone olmamasını sağlar. Bundan sonra, sözleşmenin durum değişkenlerinde uygun değerleri ayarlar.

Son olarak, zamanlayıcı sözleşmesini çağırıyoruz:

```text
scheduler.scheduleCall(address(this), 0, 50000, 100, subscriptionPeriod, abi.encodeWithSignature("pay(address)", msg.sender));
```

Bu satırı biraz açalım:

- `adres(bu)` aranacak akıllı sözleşmenin adresidir, bu durumda zamanlama sözleşmesini çağıran akıllı sözleşmeyi çağırıyoruz
- 'subscriptionPeriod', bundan sonra bu çağrıyı denemesi ve yürütmesi gereken blok sayısıdır (ancak daha fazla olabilir!)
- `abi.encodeWithSignature("pay(address)"` akıllı sözleşme içinde çağrılacak fonksiyondur (bunu daha sonra tanımlayacağız).
- "msg.sender", bu işleve iletilen değerdir.

"Zamanlayıcı" sözleşmesine geçirilen argümanların geri kalanı hakkında daha fazla bilgi için "Scheduler.sol" dosyasını oluşturduğumuz yere gidin.

"Unsubscribe" işlevi, "periodSubscribed" durum değişkenini 0'a geri döndürür.

Şimdi zamanlayıcının çağırdığı 'ödeme' fonksiyonunu oluşturalım:

```text
contract Subscription {
  ...

  function pay(address _subscriber) public {
    require(msg.sender == address(this), "No Permission");
    require(periodSubscribed[_subscriber] > 0);

    // If the subscriber does not have enough
    if (balanceOf[_subscriber] < subscriptionPrice) {
      periodSubscribed[_subscriber] = 0;
      return;
    }

    periodSubscribed[_subscriber] += 1;
    balanceOf[_subscriber] -= subscriptionPrice;
    subTokensOf[_subscriber] += periodSubscribed[_subscriber];
    owner.transfer(subscriptionPrice);

    scheduler.scheduleCall(address(this), 0, 50000, 100, subscriptionPeriod, abi.encodeWithSignature("pay(address)", _subscriber));
  }
}
```

Burada abonenin yeniden abone olmak ve gerektiğinde çeşitli durum değişkenlerini güncellemek için yeterli kaynağa sahip olmasını sağlarız ve aboneye arka arkaya abone oldukları dönem sayısı kadar Abonelik Simgesi veririz.

İşlevin ilk satırına dikkat edin:

```text
require(msg.sender == address(this), "No Permission");
```

Bu, yalnızca sözleşmenin kendisinin bu işlevi çağırabileceğini söylüyor. "Zamanlayıcı" sözleşmesini kullanarak bir çağrı planladığımızda, aslında işlevi çağıran zamanlayıcı değil, işlevin kendisidir. Zamanlayıcı, aramayı daha sonra gönderiyor.

Son olarak bir 'addFunds' ve 'withdrawFunds' işlevi ekleyelim, böylece kullanıcı abonelikler için daha fazla fon ekleyebilir ve sözleşmeye gönderdikleri kullanılmayan fonları çekebilir..

```text
contract Subscription {
  ...

  function addFunds() public payable {
    balaneOf[msg.sender] += msg.value;
  }

  function wthdrawFunds() public {
    require(balanceOf[msg.sender] > 0, "No funds to withdraw");
    msg.sender.transfer(balanceOf[msg.sender]);
  }
}
```

İşte bu kadar! Artık otomatik aboneliklerle tamamen işleyen bir akıllı sözleşmemiz var!

## Bina

Akıllı sözleşmeyi oluşturmak için projenin kök dizininde aşağıdakileri çalıştırın:

```text
yarn build
```

## Dağıtım

Akıllı sözleşmeyi dağıtmak için [buradaki](https://wiki.acala.network/build/development-guide/smart-contracts/get-started-evm/deploy-contracts) yönergeleri izleyin.
