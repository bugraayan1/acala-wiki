# Oracle Gateway'i açın

## Genel Bakış

Güvenilir, doğru ve merkezi olmayan kahinler sağlama zorluğu, yalnızca Acala tarafından çözülemez. Acala'nın Polkadot, Kusama ve ötesinde daha fazla zincirler arası DeFi DApp'lerine güç sağlayan DeFi merkezi ve platformu olduğu göz önüne alındığında, sektördeki diğer önde gelen projelerle daha açık, kapsayıcı ve merkezi olmayan bir oracle altyapısı oluşturmak kritik hale geliyor. Open Oracle Gateway \(OOG\) bu vizyona doğru atılmış önemli bir adımdır.

Ağ Geçidi, Acala'nın DeFi optimize edilmiş oracle altyapısından yararlanarak ve Acala, Polkadot, Kusama ve ötesinde herhangi bir DApp'e hizmet vererek Acala ağında birden fazla oracle'ın kurulmasına izin verir. Ağ Geçidi özellikle şunları sunar:

1. **Çoklu Oracle Ağları**: Acala Oracle'a ek olarak birden fazla taraf kendi Oracle servislerini çalıştırabilir. Sağlayıcılar, düğüm operatörleriyle kendi oracle ağlarını kurabilir veya bir Oracle API ile entegre edebilir.
2. **Seçime Göre Fiyat Beslemeleri**: Dapps, tüm sağlayıcılardan veya tek bir sağlayıcıdan toplu bir özet akışı kullanmayı seçebilir veya bireysel düğüm operatörlerinden ham veriler alabilir ve bunları kendileri toplayabilir.
3. **Hizmet Kalitesi**: Ağ Geçidi üzerinden gönderilen tüm fiyat akışları Hizmet Kalitesi ile sağlanacaktır - bu işlemler, öncelik verilen ve bir bloğa dahil edilmeleri garanti edilen _operasyonel işlemler_ \(sistem açısından kritik işlemler\)dir.
4. **ÜCRETSİZ**: Tüm geçerli yayınlar, yapılan işlem ücretleri ile birlikte iade edilecektir, esasen Oracle yayınlarını sağlayıcılar için ÜCRETSİZ hale getirirken spam'i önler ve bütünlüğü sağlar.
5. **Aşamalı Yerelleşme**: Acala ağı aşamalı olarak merkezileşmeyecek, PoA \(atanmış Konsey yönetimi\) ile başlayacak, ardından seçilmiş Konsey yönetimine ve nihayetinde demokrasiye dönüşecektir. Ağ Geçidi daha sonra başlangıçta yeni oracle sağlayıcılarını ve onların düğüm operatörlerini kabul etmek için oturma Konseyi onayını gerektirecektir.

## Sağlayıcı Ayarlama

Bir Oracle Ağ Sağlayıcısı, kendi Oracle paletlerini uygulayabilir \([varsayılan Oracle paletine](https://github.com/open-web3-stack/open-runtime-module-library/tree/master/oracle)\ ) zincirler arası veri beslemelerinin doğrulanması gibi özel gereksinimlerini karşılamak için. Ayrıca, yalnızca bir Coinbase Sağlayıcı paleti ekleyerek [Coinbase fiyat oracle](https://blog.coinbase.com/introduction-the-coinbase-price-oracle-6d1ee22c7068) gibi mevcut imzalı Oracle API'leriyle kolayca entegre olabilir ve bunların doğruluğunu onaylayabiliriz. imza.

Ardından, Oracle sağlayıcısını yürürlüğe girecek olan çalışma zamanına \(bkz. [Acala Oracle](https://github.com/AcalaNetwork/Acala/blob/master/runtime/mandala/src/lib.rs#L447)\) ekleyin çalışma zamanı yükseltmesi aracılığıyla.

### Operatör Düğümlerini Ayarlama

Bir Sağlayıcı, Oracle ağına birden çok operatör düğümü ekleyebilir, örnek bir operatör düğümü [burada](https://github.com/laminar-protocol/oracle-server).

## Open Oracle Gateway'e Katılın

Oracle Gateway, Acala'nın Mandala Test Ağı üzerinde kurulu ve çalışıyor. Acala ekibi ve Laminar ekibinin yanı sıra Band Protokol ekibi de Gateway'in geliştirilmesine katkıda bulunmuştur. Ağ Geçidinin Acala, Polkadot, Kusama ve genel olarak zincirler arası DeFi ekosistemi için ortak bir iyi altyapı olmasını umuyoruz. Bu nedenle, Oracle servis sağlayıcılarını Gateway kaynak kodunu kontrol etmeye, entegrasyon hakkında bizimle konuşmaya, kod tabanına katkıda bulunmaya ve hizmetlerinizi sürekli büyüyen bir ekosisteme sunmaya davet ediyoruz.

**Acala öncesi/Karura oluşumu**

* lütfen doğrudan bizimle iletişime geçin \(acala dot network'ten merhaba\) veya ilginizi belirtmek için [Discord](https://discord.gg/vdbFVCH) üzerinden sorun.
* bir Çekme Talebi gönderin
* PR'yi inceleyip onaylayacağız
* daha sonra kodu birleştirin ve test ağına dağıtın

**Post Acala/Karura oluşumu**

* ilgiyi artırmak ve onay almak için lütfen Acala/Karura konseyi ile iletişime geçin.
* onaylandıktan sonra bir Çekme Talebi gönderin
* kod inceleme ve birleştirme
* çalışma zamanı yükseltmesi
