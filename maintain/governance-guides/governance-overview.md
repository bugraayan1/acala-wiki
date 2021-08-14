---
tanım: gelişme yönü.
---

# Yönetişime Genel Bakış

* [Governance](https://wiki.acala.network/maintain/governance-guides/governance-overview#governance)
  * [Acala Governance Odaları](https://wiki.acala.network/maintain/governance-guides/governance-overview#chambers-of-acala-governance)
  * [Aşamalı Yerel Yönetim](https://wiki.acala.network/maintain/governance-guides/governance-overview#progressive-decentralization)
    * [Aşama I: Konsey Yönetimi](https://wiki.acala.network/maintain/governance-guides/governance-overview#phase-i-council-governance)
      * [Uygulama](https://wiki.acala.network/maintain/governance-guides/governance-overview#implementation)
        * [Mandala TC3](https://wiki.acala.network/maintain/governance-guides/governance-overview#mandala-tc3)
    * [Aşama II: Seçilmiş Konsey + Referandum Yönetişimi](https://wiki.acala.network/maintain/governance-guides/governance-overview#phase-ii-elected-council-referendum-governance)
  * [Yetki Alanları](https://wiki.acala.network/maintain/governance-guides/governance-overview#jurisdictions)
    * [Honzon Konseyi Yargı Yetkileri](https://wiki.acala.network/maintain/governance-guides/governance-overview#honzon-council-jurisdictions)
    * [Homa Konseyi Yargı Yetkileri](https://wiki.acala.network/maintain/governance-guides/governance-overview#homa-council-jurisdictions)
    * [Genel Konsey Yargı Yetkisi](https://wiki.acala.network/maintain/governance-guides/governance-overview#general-council-jurisdiction)
  * [Tartışma ve Geliştirme Altında](https://wiki.acala.network/maintain/governance-guides/governance-overview#under-discussion-and-development)

## Yönetim

Acala, aşamalı olarak merkezden uzaklaştırılmasına ve nihayetinde çoğunluk ağ paydaşları tarafından komuta edilmesine izin verecek çeşitli yönetişim mekanizmalarını kullanmak için aşamalı bir yaklaşım benimsiyor.

Teknik ve yönetişim mekanizması tasarımı için Polkadot'tan çok ilham alıyoruz ve onu Acala Ağı'na en iyi şekilde hizmet edecek şekilde uyarlıyoruz.

### Acala Yönetim Odaları

Genel Konsey ve ACA Referandumu, Acala Ağı'nı yöneten kapsayıcı odalardır. Genel Konsey, ağın özelliklerini yönetmek için bu uzman konseyleri atar: Honzon \(Financial\) Konseyi, Homa \(Stake Likidite\) Konseyi ve Teknik Konsey. L-DOT Referandum odası, Homa Konseyi ile birlikte stake likidite protokolü ile ilgili işleri yönetecek.

### Aşamalı Yerel Yönetim

#### Aşama I: Konsey Yönetimi

Acala Ağı'nı geliştirmenin en erken aşaması, normal bir başlangıçtan pek de farklı olmayan bir şekilde Acala Vakfı tarafından yönetiliyor: harika bir ekip, yalın geliştirme, sıkı uygulama ve hızlı öğrenme. **Ademi merkeziyetçilik bahanesi olmamalıdır**

Bu aşamada, Acala Vakfı'nın ağa ilişkin kararları, atanan Genel Konsey oylamasıyla zincir üzerinde şeffaf hale getirilir. Diğer tüm konseyler Genel Konsey tarafından atanır.

**Teklifler ve Önergeler**

* **Gönderme**: Bu aşamada sadece meclis üyeleri öneri sunabilir ve bir sonraki aşamada halka açık olacaktır.
* **Oylama**: bir teklif ve gerekli onaylardan oluşan hareketler yoluyla sürekli \(belirlenmiş bir süre yok\) şeklindedir.
* **Yürütme**: Bir hareket onaylanırsa, [Open Web3 Stack](https://github.com/open-web3-stack/open-runtime) tarafından mümkün kılınan aşağıdaki stratejilerden biri kullanılarak yürütülebilir -modül-kütüphane):
  * hemen: süper çoğunluk gereklidir.
  * gecikmeli bir zamanda: uzman konseyleri, tartışmasız tehlikeli veya kötü niyetli bir hareketi uygulanmadan önce iptal edebilir. Basit çoğunluk gereklidir.
  * kademeli olarak: sayısal değer değiştirme hareketleri örn. istikrarı artırma ücreti, zaman içinde kademeli olarak uygulanabilir, bozulmayı azaltır. Basit çoğunluk aranmaktadır.
* **Süreler**: Bu aşamada tüm hareket süreleri 7 gün olarak ayarlanmıştır.

**Genel Konsey**

* **İstenilen üye**: Genel Kurul'un bu aşamada 5'i olup, bir sonraki aşamada artırılacaktır.
* **Oylama**: Bir sonraki hemen uygulanamayan önergeye konseyin basit çoğunluğu karar verebilir, aksi takdirde süper çoğunluk gerekir.
* **Seçim**: Acala Vakfı tarafından atanır.
* **Teklifler/Öneriler**: Yalnızca Genel Konsey üyeleri kök çağrı teklifi sunabilir, ör. çalışma zamanı yükseltmesi. Tartışmasız tehlikeli hareketleri oybirliğiyle iptal edebilir.

**Honzon Konseyi**

* **İstenilen üyelik**: Honzon Konseyi'nin bu aşamada 5'i olup, bir sonraki aşamada artırılacaktır.
* **Oylama**: Bir sonraki önergeye konseyin salt çoğunluğu karar verebilir.
* **Seçim**: Genel Konsey tarafından basit çoğunlukla seçilir.
* **Teklifler/Talepler**: üyeler Honzon ile ilgili parametre değişikliği tekliflerini sunabilir. Tüm hareketler, Genel Konseyin veya Teknik Konseyin tartışmasız bir şekilde tehlikeli hareketler yapabileceği gecikmeli bir zamanda yürütülür.

**Homa Konseyi**

* **İstenilen üyelik**: Homa Konseyi'nin bu aşamada 3'ü vardır ve bir sonraki aşamada artırılacaktır.

faz.
* **Oylama**: Bir sonraki önergeye konseyin salt çoğunluğu karar verebilir.
* **Seçim**: Genel Konsey tarafından basit çoğunlukla seçilir.
* **Teklifler/Öneriler**: üyeler Homa ile ilgili parametre değişikliği tekliflerini sunabilir. Tüm hareketler, Genel Konseyin veya Teknik Konseyin tartışmasız bir şekilde tehlikeli olabileceği gecikmeli bir zamanda yürütülür.

**L-DOT Odası**

* **Teklifler/Talepler**: L-DOT sahipleri, istedikleri doğrulayıcıları seçmek için her belirli dönemde oy kullanabilirler, ör. her dönem.
* **Program**: L-DOT sahipleri, Phragmen seçimlerine benzer bir plana dayalı olarak 16 aday için oy kullanabilir \[https://wiki.polkadot.network/docs/en/learn-phragmen\].

**Teknik Konsey**

* **İstenen üyelik**: Teknik Konseyin bu aşamada 3'ü olup, bir sonraki aşamada artırılacaktır.
* **Seçim**: Genel Konsey tarafından basit çoğunlukla seçilir.
* **Teklifler/Öneriler**: Tartışmaya açık olmayan tehlikeli önergeleri oybirliğiyle iptal edebilir.

#### **Uygulama**

#### **Mandala TC3**

Dört konsey odası uygulandı: Genel Konsey, Honzon Konseyi, Homa Konseyi, Teknik Konsey. Şu anda yalnızca işlevsellik testi amacıyla "sudo" ile birlikte çalışırlar. 'Gerçek' yönetim, gerçek hisse ile kanarya ağımız **Karura**'da yürürlüğe girecek.

**Konsey Odaları**

![Dapp](../../.gitbook/assets/gov_council.png)

**Konsey Önergeleri**

![Dapp](../../.gitbook/assets/gov_motion.png)

Yönetim tekliflerini belgelemek, görüş ve tartışmaları toplamak, oylama sonucunu ve yürütme durumunu yayınlamak vb. için iyi uygulamaları ve araçları yakından izliyoruz. Örnek olarak, [Polkassembly](https://kusama.polkassembly.io/) iyi bir yer gibi görünüyor Acala yönetişimi için benzer bir yaklaşımı entegre etmeyi veya kullanmayı düşünebiliriz.

#### Aşama II: Seçilmiş Konsey + Referandum Yönetimi

Çok yakında...

### yetki alanları

#### Honzon Konseyi Yargı Yetkileri

**Kredi ile ilgili parametreler**

| parametre | Tip | Açıklama | Örnek |
| :--- | :--- | :--- | :--- |
| Stabilite Ücreti | Puan | Belirli bir teminat için istikrar ücreti \(küresel istikrar ücretine ek olarak\) | BTC: 0,00001 |
| Tasfiye Oranı | Oran | Belirli teminatlar için tasfiye oranı | BTC: %150 |
| TasfiyePenaltı | Puan | Belirli teminatlar için tasfiye cezası oranı | BTC: %13 |
| Gerekli TeminatOranı | Oran | belirli bir teminat için USD kredisi açmak için gerekli teminat oranı | BTC: %180 |
| MaksimumToplamDebitDeğeri | Bakiye | Belirli bir teminat için USD cinsinden borç tavanı | BTC: 100.000.000 |
| GlobalStabilite Ücreti | Puan | Tüm teminat türleri için temel istikrar ücreti | 0.000005 |

**Tasfiye ve CDP Hazinesi ile ilgili parametreler**

| parametre | Tip | Açıklama | Örnek |
| :--- | :--- | :--- | :--- |
| ArtıTamponBoyutu | Bakiye | Fazla açık artırma tamponu. Artı &gt; fazla arabellek + sabit boyut | 1.000.000 USD |
| ArtıMüzayedeSabitBoyut | Bakiye | USD cinsinden fazla açık artırma boyutu | 10000 dolar |
| InitialAmountPerDebitAuction | Bakiye | Bir borç müzayedesinde ilk ACA müzayede tutarı | 80000 ACA |
| BorçAuctionFixedSize | Bakiye | USD cinsinden borç açık artırma boyutu | 10.000 ABD Doları |
| TeminatAuctionMaximumSize | Bakiye | Maksimum teminat açık artırma boyutu | BTC: 0.1 |

#### Homa Konseyi Yargı Yetkileri

* ya Homa hazinesi ya da doğrulayıcı tahvil yoluyla tahsisat kesintisi tazminatı
* oybirliğiyle rıza ile kara liste doğrulayıcıları
* doğrulayıcı seçim kriterlerini tanımlayın

#### Genel Konsey Yargı Yetkisi

Daha az sıklıkla değiştirilen parametreler ve diğer değişiklik türleri, şimdilik Genel Konsey tarafından yönetilen çalışma zamanı yükseltmesi aracılığıyla yürütülür.

**Acala DeX parametreleri**

| parametre | Tip | Açıklama | Örnek |
| :--- | :--- | :--- | :--- |
| GetExchangeÜcreti | Puan | Döviz ücreti oranı | 5‰ |
| GetBaseCurrencyId | Para Birimi Kimliği | Ticaret çiftleri için temel para birimi | birUSD |

**Global Stabilcoin Parametreleri**

| parametre | tip | açıklama | örnek |
| :--- | :--- | :--- | :--- |
| TeminatPara BirimiKimlikleri | Vec | Teminat varlık türleri | \[BTC, NOKTA\] |
| VarsayılanLiquidationRatio | Oran | Belirli bir teminat için herhangi bir tasfiye oranı belirlenmemişse varsayılan tasfiye oranı | %150 |
| VarsayılanDebitExchangeRate | Döviz Kuru | Tüm teminatlar için borç ve aUSD'nin başlangıç ​​değişim oranı | 10:1 |
| VarsayılanLiquidationPenaltı | Oran | Belirli bir teminat için herhangi bir tasfiye oranı belirlenmemişse varsayılan tasfiye oranı | %15 |
| MinimumDebitDeğeri | Bakiye | Tozdan kaçınmak için CDP'nin minimum borç değeri \(USD cinsinden\) | 1 |

**Tasfiye ve CDP hazine parametreleri**

| parametre | Tip | Açıklama | Örnek |
| :--- | :--- | :--- | :--- |
| MaxSlippageSwapWithDEX | Oran | Tasfiye sırasında, DeX üzerindeki bir teminatın likidasyonu bu değerin altında bir kaymaya neden olursa, sistem tasfiyeyi müzayede yerine DeX üzerinde gerçekleştirecektir | %5 |

**Açık artırma parametreleri**

| parametre | Tip | Açıklama | Örnek |
| :--- | :--- | :--- | :--- |
| MinimumArtışBoyutu | Puan | Asgari fiyat artışı | %5 |
| AuctionTimeToClose | BlokNumarası | Her yeni tekliften sonra açık artırma zamanı | 500 |
| Açık ArtırmaDurationSoftCap | BlokNumarası | Toplam müzayede süresi bu değeri aştığında, sistem fiyat artışını iki katına çıkaracak ve müzayedeyi hızlandırmak için müzayede süresini yarıya indirecektir | 5000 |
| GetAmountAyarlaması | Puan | Borç müzayedesinde başarılı bir bit yoksa ACA miktarını ayarlayın | %10 |

**Homa stake likidite parametreleri**

| parametre | Tip | Açıklama | Örnek |
| :--- | :--- | :--- | :--- |
| MaxBondRatio | Oran | Maksimum miktar stake edilebilir / toplam miktar yatırılabilir. Kalan tutar, bahse konu olmayan varlıkların sınırlandırılmasını hızlandırmak için kullanılır | %90 |
| MinBondOranı | Oran | Stake oranı bu oranın üzerinde tutulacaktır | %80 |
| MaxClaimÜcreti | Puan | Ani veya hızlandırılmış sınırlamasız dönem için alınan maksimum yüzde, L-DOT cinsinden alınan ücretler | %5 |
| TalepÜcretiDönüşOranı | Oran | Yakılacak ücretlerin yüzdesi, kalan Homa hazinesine gidiyor | %80 |
| ÖdülÜcret Oranı | Oran | Ücretin küçük bir kısmı, slash tazminatı, geliştirme vb. için Homa hazinesi tarafından yönetilecek olan stake ödülünden alınır. | %1 |
| VarsayılanDöviz Oranı | Döviz Kuru | Başlangıç ​​L-DOT için DOT döviz kuru | 10:1 |

**Doğrulayıcı seçim parametreleri**: Not: Şu anda röle zinciri köprüsü mevcut olana kadar bazı kodlarla alay edilir

| parametre | Tip | Açıklama | Örnek |
| :--- | :--- | :--- | :--- |
| MinBondEşik | Bakiye | Tozdan kaçınmak için doğrulayıcıyı seçmek için minimum L-DOT bağlı | 1 LDOT |
| Yapıştırma Süresi | Bakiye | L-DOT'u çözme süresi | 7 Çağ |
| MaxUnlockingChunks | kullanmak | Bir işaretleme zamanında maksimum bağlanma çözme olayı sayısı | 7 |
| Aday Sayısı | kullanmak | Aday gösterilebilecek doğrulayıcı sayısı | 7 |

### Tartışma ve Geliştirme Altında

* Yönetişimin bir sonraki aşaması, ayrıntıları tasarlanmakta olan seçilmiş konseyleri ve referandum odalarını harekete geçirecek. İlerledikçe hazine hakkında daha fazla ayrıntı açıklanacak.
* Acala, ağın refahını yöneten birden fazla hazineye ve fona sahip olacak.
  * ACA Hazinesi, Genesis ACA'yı elinde tutar, ağ gelir ve giderlerini yönetir
  * her protokolün gelir ve giderler için kendi hazinesi olacaktır.
  * Devlet Varlık Fonu, yatırım stratejilerine göre hazine ve alım rezervlerinden sağlanan fazlalığı elinde tutacaktır.
* Yönetim üzerinde etkisi olacak Homa likidite staking protokolünün ayrıntıları ortaya çıkıyor.

