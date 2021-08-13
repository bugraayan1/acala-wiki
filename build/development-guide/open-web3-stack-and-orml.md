# Open-Web3-Stack ve ORML

Open Web3 Stack, Substrate üzerinde uygulama geliştirmeyi hızlandırmak için yaygın olarak kullanılan bir kitaplık koleksiyonudur. Çoğu uzman zincir için ortak olan uygulama yapı taşları sağlamayı amaçlar.

Açık Web3 Yığını aşağıdaki depoları içerir

* **Açık Çalışma Zamanı Modül Kitaplığı \(ORML\)** yaygın olarak kullanılan tüm paletleri, modülleri uyguladığımız yer
* **Open-web3.js** - ORML'den genişletilmiş Substrate mantığını kullanmak için ön uç SDK'sı
* **Guardian** - belirli görevleri izlemek ve yürütmek için çalışan bir işçi
* **Rokoko topluluğu**: parachainleri ve zincirler arası iletişimi test etmek için barındırılan bir ortam

### ORML

Daha fazlasını [buradan](https://github.com/open-web3-stack/open-runtime-module-library) öğrenin.

* [orml-traits](https://github.com/open-web3-stack/open-runtime-module-library/blob/master/traits)
  * "Temel Para Birimi", "Çok Para Birimi", "Açık Artırma" ve daha fazlasını içeren paylaşılan özellikler.
* [orml-utilities](https://github.com/open-web3-stack/open-runtime-module-library/blob/master/utilities)
  * 'OrderSet' dahil olmak üzere çeşitli yardımcı programlar.
* [orml-belirteçleri](https://github.com/open-web3-stack/open-runtime-module-library/blob/master/tokens)
  * 'MultiCurrency' özelliğini uygulayan Fungible belirteçleri modülü.
* [orml-para birimleri](https://github.com/open-web3-stack/open-runtime-module-library/blob/master/currencies)
  * 'Palet-balances' ve 'orml-tokens' modülünü kullanarak 'MultiCurrency' uygulamasını sağlayın.
* [orml-nft](https://github.com/open-web3-stack/open-runtime-module-library/tree/master/nft)
  * Fungible olmayan token modülü, NFT\(nonfunble token\) oluşturmak ve yönetmek için temel işlevler sağlar
* [orml-oracle](https://github.com/open-web3-stack/open-runtime-module-library/blob/master/oracle)
  * Zincir dışı verileri zincir üzerinde kullanılabilir hale getiren Oracle modülü.
* [orml-açık artırma](https://github.com/open-web3-stack/open-runtime-module-library/blob/master/auction)
  * "Açık Artırma" özelliğini uygulayan Müzayede modülü.
* [orml-vesting](https://github.com/open-web3-stack/open-runtime-module-library/blob/master/vesting)
  * Kademelendirilmiş bir şekilde, planlı denge kilitleme mekanizması sağlar.
* [orml-kademeli olarak güncelleme](https://github.com/open-web3-stack/open-runtime-module-library/blob/master/gradually-update)
  * Belirli bir süre boyunca kademeli olarak sayısal parametreyi ayarlamanın yolunu sağlar.
* [orml-xtokens](https://github.com/open-web3-stack/open-runtime-module-library/blob/master/xtokens)
  * Zincirler arası varlık transferi yapmanın yolunu sağlar.
  * [Adım Adım kılavuz](https://github.com/open-web3-stack/open-runtime-module-library/wiki/xtokens) XCM çapraz zincir değiştirilebilir varlık transferini para zincirinizde kullanılabilir hale getirmek için
* [orml-xcm-support](https://github.com/open-web3-stack/open-runtime-module-library/blob/master/xcm-support)
  * XCM entegrasyonunu desteklemek için özellikler, türler ve uygulamalar sağlar.

### Muhafız

Guardian ile **sadece konfigürasyonla**, bir endişe zinciri için komutları izlemek ve yürütmek için bir dizi otomatik görev ayarlayabilirsiniz. Bir görev, koşullarla \(teminat oranı <%110 ise\) "marj pozisyonlarını izlemek" olabilir ve ardından eylemleri \(örneğin, veritabanı hizmetine uyarı mesajı göndermek veya pozisyon eklemek için bir komut dosyası yürütmek\) tetikleyebilir.

İşte [örnekler](https://github.com/open-web3-stack/guardian/tree/master/packages/example-guardian) ve ilgili [belgeler](https://github.com/open- web3 yığını/koruyucu/ağaç/ana/paketler/koruyucu/belgeler).

### Open-web3.js

Open-web3, orml, indeksleyici ve oracles ile etkileşime izin veren bir grup ön uç paketidir. Daha fazlasını [buradan](https://github.com/open-web3-stack/open-web3.js) öğrenin.

### Topluluk Rokoko Test Ağı

Ortak altyapı ile topluluk Rococo parachain test ağını başlattık. Herkesin zincirler arası jeton transferlerini, harmanlayıcıları, doğrulayıcıları vb. daha düşük ek yük ile test etmesine olanak tanır.

[Buradan](https://github.com/open-web3-stack/rococo-community) başlayın.
