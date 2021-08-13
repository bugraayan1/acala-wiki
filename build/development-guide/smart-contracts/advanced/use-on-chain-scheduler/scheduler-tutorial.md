# Eğitim

Bu eğitimde, kullanıcıları abone oldukları süre boyunca ödüllendiren otomatik bir abonelik hizmeti oluşturmak için Acala'nın zincir üstü zamanlayıcısını kullanacağız. Bir kullanıcı bu hizmete abone olabilir ve belirli bir süre geçtiğinde, sözleşme onları bazı jetonlarla ödüllendirecektir.

## Bağımlılıkları Kur ve Yükle

Sıfırdan bir proje oluşturacağız, Waffle kullanarak inşa edeceğiz ve test edeceğiz. Akıllı sözleşmelerinizi Remix kullanarak oluşturmayı tercih ediyorsanız lütfen [bu](https://wiki.acala.network/build/development-guide/smart-contracts/get-started-evm/use-remix) sayfaya göz atın. .

Başlamak için, henüz yapmadıysanız, `nodejs` ve yarn'ı yükleyelim.:

```text
sudo apt install -y nodejs

npm install --global yarn
```

Ardından, projenizin yaşamasını istediğiniz klasörde aşağıdaki komutları çalıştırın:

```text
mkdir subscription-contract
cd subscription-contract

yarn init -y
yarn add --dev ethereum-waffle@3.2.1
```

Ve aşağıdaki betiği "package.json" dosyanıza ekleyin:

```text
"build": "waffle"
```

Bu, projemiz için bir klasör oluşturacak, yeni bir yarn projesi başlatacak ve bir geliştirme bağımlılığı olarak waffle ekleyecektir. Akıllı sözleşmelerimizi derlemek için waffle kullanacağız.

Proje klasörünüzde `waffle.json` adında bir dosya oluşturun ve aşağıdakini dosyanın içine yapıştırın:

```text
{
  "compilerType": "solcjs",
  "compilerVersion": "0.6.2",
  "sourceDirectory": "./contracts",
  "outputDirectory": "./build"
}
```

Bu dosya, akıllı sözleşmelerimizi oluştururken kullanılacak 'waffle' yapılandırmalarıdır.

Sözleşmeler klasörümüzü oluşturalım..

```text
mkdir contracts
```

## Use Scheduler.sol

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

Bu dosya, zamanlayıcı akıllı sözleşmesini ve bunu kullanmak için ona hangi argümanları sağlamanız gerektiğini açıklar. Ancak zamanlayıcı nasıl çalışır?

Acala EVM, Solidity, Substrate ve Web3 geliştiricilerine tek bir cüzdan ile eksiksiz bir full-stack \(Acala+EVM+Substrate+WASM\) deneyimi sağlar. Birçok Substrat ve WASM özelleştirmesi, zincir üstü zamanlayıcı, kendi gas'ınızı getirin, Hizmet Kalitesi oracle beslemeleri ve daha fazlası gibi önceden derlenmiş sözleşmeler aracılığıyla EVM içinde kullanıma sunulur. Ethereum'da imkansız olacak yeni özellikler eklememize izin verirken, geliştiricilerin bu özelliklerden yararlanan DApp'ler oluşturmak için mevcut kodu ve araçları kullanmasına izin verir. Bu önceden derlenmiş akıllı sözleşmeler, Acala EVM'de statik, bilinen adreslere sahiptir ve bu da kullanımı inanılmaz derecede kolaylaştırır.

## Abonelik Sözleşmesini Oluşturun

`Contracts` klasörü içerisinde bir `Subscription.sol` dosyası oluşturarak akıllı sözleşme dosyamızı oluşturalım. İçinde aşağıdaki kodu ekleyin:

```text
pragma solidity ^0.6.0;

import "./Scheduler.sol";

contract SubscriptionToken {
    Scheduler scheduler;
    constructor(address scheduler_address) public payable {
        scheduler = Scheduler(scheduler_address);
    }
}
```

Burada, 'Scheduler' akıllı sözleşmesini tanımlayan ve 'scheduler'ımızı yapıcıdaki adresine yönlendiren soyut sınıfı içe aktardığımızı görebilirsiniz. Yine, Zamanlayıcı, statik bir adrese sahip önceden derlenmiş bir akıllı sözleşmedir. Her zaman bu adreste zincirde yaşayacak, kendi sürümünüzü dağıtmanıza gerek yok. ![](https://i.imgur.com/8d8Mxly.png)

### Yapıcı

Ardından, bazı durum değişkenlerini ayarlayalım ve bir yapıcıyı değiştirelim. Sözleşmeye aşağıdakileri ekleyin:

```text
contract SubscriptionToken {
    uint period;
    address[] subscribers;
    mapping(address => uint) public balanceOf;
    Scheduler scheduler;

    constructor(uint _period, address scheduler_address) public payable {
        period = _period;
        scheduler = Scheduler(scheduler_address);
        scheduler.scheduleCall(address(this), 0, 50000, 100, period, abi.encodeWithSignature("paySubscribers()"));
    }
}
```

Burada 6 durum değişkeni ekledik. Bunları tek tek inceleyelim:

1. "balanceOf": bir kullanıcının bakiyesindeki yerel jeton sayısını tanımlar/gösterir.
2. "dönem": Zamanlayıcı'nın kaç blok olarak adlandırılması gerektiğini gösteren bir dönem

Yapıcı kendini açıklayıcıdır, tek yaptığı sözleşme için ilk durum değişkenlerini ayarlamaktır.

### Abone olma ve Aktarma işlevleri

Ardından 'abone ol' işlevini ekleyelim:

```text
contract SubscriptionToken {
  ...

  function subscribe() public {
        subscribers.push(msg.sender);
  }
  function transfer(address _to, uint amount) public {
        require(balanceOf[msg.sender] > amount -1, "Insuffcient funds");
        balanceOf[msg.sender] -= amount;
        balanceOf[_to] += amount;
  }

}
```

Burada 'abone ol' işlevi, bir kullanıcıyı belirteçlerin dağıtılacağı bir listeye ekler.

Son olarak, 'scheduleCall' argümanlarına bir göz atalım:

```text
scheduler.scheduleCall(address(this), 0, 50000, 100, period, abi.encodeWithSignature("paySubscribers()"));
```

Bu satırı parçalayalım:

* `adres(bu)` aranacak akıllı sözleşmenin adresidir, bu durumda, zamanlama sözleşmesini çağıran aynı akıllı sözleşmeyi çağırıyoruz.
* "değer" - Çağrıyla birlikte ne kadar yerel jeton gönderileceğidir.
* `gas_limit` - Çağrı için gaz limiti. İlgili ücret önceden rezerve edilecek ve aramadan sonra iade edilecektir.
* `storage_limit` - Arama için depolama limiti. İlgili ücret önceden rezerve edilecek ve aramadan sonra iade edilecektir.
* "min_delay", bundan sonra bu çağrıyı denemesi ve yürütmesi gereken blok sayısıdır \(daha fazla olabilir!\)
* `abi.encodeWithSignature("paySubscribers()")`, akıllı sözleşmede \(bunu daha sonra tanımlayacağız\) içinde çağrılacak işlevdir.

"Zamanlayıcı" sözleşmesine geçirilen argümanların geri kalanı hakkında daha fazla bilgi için "Scheduler.sol" dosyasını oluşturduğumuz yere gidin.

### Ücretli aboneler

Şimdi planlayıcının çağırdığı `paySubscribers` fonksiyonunu oluşturalım:

```text
contract SubscriptionToken {
  ...

  function paySubscribers() public {
        require(msg.sender == address(this));
        if (subscribers.length > 0) {
            for (uint256 i = 0; i < subscribers.length; i++) {
                address subscriber = subscribers[i];
                balanceOf[subscriber] += 1;
            }
        }

        scheduler.scheduleCall(address(this), 0, 50000, 100, period, abi.encodeWithSignature("paySubscribers()"));
    }
}
```

İşlevin ilk satırına dikkat edin:

```text
require(msg.sender == address(this), "No Permission");
```

Bu, yalnızca sözleşmenin kendisinin bu işlevi çağırabileceğini söylüyor. "Zamanlayıcı" sözleşmesini kullanarak bir çağrı planladığımızda, aslında işlevi çağıran zamanlayıcı değil, işlevin kendisidir. Zamanlayıcı, aramayı daha sonra gönderiyor.

Ve bu kadar! Artık otomatik aboneliklerle işleyen bir akıllı sözleşmemiz var!

## İnşaa Etme

Akıllı sözleşmeyi oluşturmak için projenin kök dizininde aşağıdakileri çalıştırın:
```text
yarn build
```

## Yerleştirme

Akıllı sözleşmeyi dağıtmak için [buradaki](https://wiki.acala.network/build/development-guide/smart-contracts/get-started-evm/deploy-contracts) yönergeleri izleyin.

1 \(≈6 saniyedir\) olarak bir "dönem" ayarlayabilir ve önceden konuşlandırılmış sözleşmeler listesinde planlayıcı adresini bulabilirsiniz.

![](https://i.imgur.com/NX3iQUW.png) Her şey bittiğinde konuşlandır'a basın.

## Sözleşmenin yürütülmesi

Bu yeni jetonu almanın tek yolu akıllı sözleşmeye abone olmaktır. 'Abone ol' işlevini yürütün ve abonenin \('balanceOf' işlevi\) için bakiyenin zaman içinde nasıl değiştiğini kontrol edin.
