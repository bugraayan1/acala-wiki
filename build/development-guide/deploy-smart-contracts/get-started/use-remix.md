# Remix Kullanımı

Solidity sözleşmelerini geliştirmek ve derlemek için kullanabileceğiniz birden fazla araç var, burada iki tanesini seçenek olarak sunacağız.

* Çevrimiçi web uygulaması Remix
* Solidity geliştirme ve test uygulaması Waffle

### Remix kullanarak bir Solidity Sözleşmesi Derleyin

Bu kılavuz, [Remix](http://remix.ethereum.org/) kullanılarak Acala bağımsız düğümüne Solidity tabanlı bir akıllı sözleşme oluşturma ve dağıtma sürecini açıklar. Remix, Ethereum'daki akıllı sözleşmeler için yaygın olarak kullanılan geliştirme ortamlarından biridir.

### **1. Remix'i Başlat**

[https://remix.ethereum.org/](https://remix.ethereum.org/) adresine gidin. 'Ortamlar' altında, Solidity geliştirme için Remix'i yapılandırmak için 'Solidity'yi seçin, ardından 'Dosya Gezgini' görünümüne gidin.

İşte Remix kullanarak bir ERC20 sözleşmesi derlemek için bir örnek.
Remix'i açın ve 'Dosya' bölümünün altında 'Yeni Dosya'yı tıklayın.
![](https://i.imgur.com/J9jtCF4.png)

Dosya gezgininde sol pencerede dosya adını yazdığınız bir girdi görünecektir: `BasicToken.sol`.

### **2. Solidity kodunu derleyin**

Açılan editör sekmesine aşağıdaki kodu yapıştırın.

```text
pragma solidity ^0.7.0;

import 'https://github.com/OpenZeppelin/openzeppelin-contracts/blob/release-v3.2.0-solc-0.7/contracts/token/ERC20/ERC20.sol';

// This ERC-20 contract mints the specified amount of tokens to the contract creator.
contract BasicToken is ERC20 {
  constructor(uint256 initialSupply) ERC20("BASICT", "BAT") public {
    _mint(msg.sender, initialSupply);
  }
}

```

Not: Bu, Open Zeppelin ERC-20 şablonuna dayalı basit bir ERC-20 sözleşmesidir. İnşaatta, BAT sembolüyle BasicToken'ı oluşturur ve toplam ilk arzı sağlar.

Editör görünümü aşağıdadır.
![](https://i.imgur.com/le9ZroU.png)

Ardından sol kenar çubuğu kenar çubuğundaki 'Solidity derleyici'yi tıklayın, yukarıdaki ekran görüntüsünde gösterilenle tamamen aynı derleyici sürümünü kullandığınızdan emin olun; ve `Compile BasicToken.sol` butonuna tıklayın.

Remix, tüm Open Zeppelin bağımlılıklarını yapacak ve sözleşmeyi derleyecektir.

### **3. ABI ve Bayt kodu Dosyasını Gösterme**

Akıllı sözleşmeyi Acala EVM'ye yerleştirmek için ABI (Uygulama İkili Arayüzü) içeren bir dosyaya ihtiyacımız olacak - akıllı sözleşmenin meta verileri, onunla etkileşime izin verir; ve bayt kodu - yürütülecek derlenmiş kodu oluşturur. Acala EVM için bu iki veriyi tek dosyada bulundurmamız gerekiyor.

"Dosya Gezgini"ne (sol kenar çubuğundaki en üstteki simge) geri gidin, açılan gezginde "artifacts" klasörünü seçin ve "BasicToken.json" dosyasının içini bulun, üzerine tıklayın. Dosyanın içeriğini göreceksiniz, bu içeriği kopyalayın.
![](https://i.imgur.com/SHH7Mj3.png)

İçeriği kopyalayıp yapıştırın ve yerel olarak kaydedin, bu daha sonra Acala EVM'ye dağıtılacak olan ABI & bytecode dosyasıdır.


#### <a id="Compile-a-Solidity-Contract-using-Remix"></a>
