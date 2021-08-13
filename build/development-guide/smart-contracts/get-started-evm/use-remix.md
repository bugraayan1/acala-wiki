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

Not: Bu, Open Zeppelin ERC-20 şablonuna dayalı basit bir ERC-20 sözleşmesidir. İnşaatta, BAT sembolüyle BasicToken'ı oluşturur ve toplam ilk arzı basar.

Editör görünümü aşağıdadır.

Remix, tüm Open Zeppelin bağımlılıklarını içerecek ve sözleşmeyi derleyecektir.

Ardından kenar çubuğundan "Solidity derleyici"yi seçin ve "Compile BasicToken.sol" düğmesine basın.

Remix, tüm Open Zeppelin bağımlılıklarını indirir ve sözleşmeyi derler.

## **3. ABI Dosyasını Alın**

'Dosya gezginleri'ne geri dönün, 'eserler' bölümünde 'BasicToken.json' dosyasını bulun. İçeriği kopyalayıp yapıştırın ve yerel olarak kaydedin, bu daha sonra Acala EVM'ye dağıtılacak ABI dosyasıdır.

![](https://i.imgur.com/qzonFHr.png)

