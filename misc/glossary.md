# Sözlük

{% ipucu stili="bilgi" %}
\[TODO\] Acala ağ mekanizması ile ilgili kelime dağarcığı eklemeniz gerekiyor.
{% uç ipucu %}

### Acala

Stablecoin ve Staking Likidite için Merkezi Olmayan Finansal Ağ, Polkadot ağına bir parachain olarak bağlanacak.

### ACA

Acala ağ belirteçlerinin kısaltması.

### Onay

Polkadot geçerlilik sisteminde, bir _attestation_, doğrulayıcıların yayınladığı ve bir parachain aday bloğunun geçerli veya geçersiz olduğunu düşündüklerini söyleyen bir mesaj türüdür.

### Yetki

Otorite, fikir birliği mekanizmalarına katılabilen bir blok zincirindeki rol için genel bir terimdir. GRANDPA'da yetkililer, nihai olduğunu düşündükleri zincirlere oy veriyor. BABE'de yetkililer blok üreticisidir. Yetki kümeleri, Polkadot'un NPoS algoritması gibi mekanizmalar olarak seçilebilir.

### Baby

\_B\_lind \_A\_ssignment of \_B\_lock \_E\_xtension Polkadot'un blok üretim mekanizmasıdır.

### Engellemek

Birlikte blok zincirinin bir durum geçişini gösteren işlemler gibi bir veri koleksiyonu.

### Blok gezgini

Kullanıcının bir blok zincirindeki farklı blokları keşfetmesini sağlayan bir uygulama.

### BLS

Boneh-Lynn-Shacham \(BLS\) imzaları yavaş imzalamaya, çok yavaş doğrulamaya sahiptir, yavaş ve çok daha az güvenli eşleştirme dostu eğriler gerektirir ve tehlikeli dövülebilirliğe eğilimlidir. Yine de BLS, bilinen diğer imza şemalarının çok ötesinde çeşitli imza toplama seçenekleri dizisine izin verir ve bu da BLS'yi konsensüs algoritmalarında oylama ve eşik imzaları için tercih edilen bir şema haline getirir.

### Yapıştırma

Belirteçlerin başka bir fayda karşılığında "dondurulabileceği" bir süreç. Örneğin, staking, ağın güvenliğini sağlama karşılığında ödüller aldığınız bir bağlanma şeklidir. Parachain yuvası karşılığında jetonları da bağlayabilirsiniz.

### Köprü

Polkadot Röle Zinciri ile bir harici zincir arasında, Röle Zincirine dış zincirin bir parachain \(yani, Polkadot Host'un parachain gereksinimlerini karşıladığı\) gibi görünecek şekilde aracı görevi gören bir parachain. Köprüler, Polkadot ile doğal olarak uyumlu olmayan Ethereum ve Bitcoin gibi diğer blok zincirleri arasında etkileşime izin verir.

### Bizans Hata Toleransı

Bizans hatalarına toleranslı bir sistemin özelliği; yani, yalnızca bireysel alt sistemlerin başarısız olabileceği bir sistem değil, aynı zamanda belirli bir alt sistemin başarısız olup olmadığı da net olmayabilir. Yani sistemdeki farklı gözlemciler sistemin başarısız olup olmadığı konusunda anlaşamayabilirler. Bizans hata toleransının sağlanması, herhangi bir dağıtılmış sistem geliştirmenin önemli bir parçasıdır.

### Derleyici

Parachain işlemlerini toplayarak ve doğrulayıcılar için durum geçiş kanıtları üreterek bir parachain'i koruyan bir düğüm.

### Uzlaşma

Bir grup varlığın belirli bir veri değeri üzerinde anlaşmaya varma süreci \(bir blok zincirindeki blokların sıralanması ve oluşturulması gibi). Konsensüs belirlemek için kullanılan çeşitli algoritmalar vardır. Polkadot tarafından kullanılan konsensüs algoritması GRANDPA'dır.

### Uygulamalar

Belirli bir sistem veya sistem kümesi üzerinde çalıştırılmak yerine dağıtılmış bir ağın parçası olarak çalışan, merkezi olmayan bir uygulama için genel bir terim.

### NOKTALAR

Polkadot için yerel jeton. DOT'lar üç amaca hizmet eder: ağ yönetişimi \(ağ yükseltmeleri ve diğer istisnai olaylar için oy kullanmalarına izin verme\), genel operasyon \(iyi oyuncuları ödüllendirme ve kötü oyuncuları cezalandırma\) ve bağlama \(DOT'ları "dondurarak" yeni parachainler ekleme. Röle Zincirine\) bağlıdırlar.

### Görev kadrosu

Belirli bir doğrulayıcının yapması gereken işi belirten bir arama tablosu \(yani, belirli bir paracahain'in geçerliliğini doğrulamak\). Görev listesi, doğrulayıcı kümesini parachain başına farklı alt kümelere rutin olarak karıştırır.

### Çağ

Bir dönem, BABE protokolünde daha küçük zaman dilimlerine bölünmüş bir zaman süresidir. Her slot, bir blok önerme hakkına sahip en az bir slot liderine sahiptir. Kusama'da, bir [oturum](https://wiki.polkadot.network/docs/en/glossary#session) ile aynı süredir.

### Çağ

Doğrulayıcının belirlediği \(ve her doğrulayıcının etkin aday kümesinin\) yeniden hesaplandığı ve ödüllerin ödendiği \(tam\) oturum sayısı.

### Eşanlamlılık

Ağa çelişkili bilgiler sağlama. BABE eş anlamlısı, aynı yuvada birden fazla blok oluşturmayı gerektirir. GRANDPA eş anlamlısı, birden çok çakışan zincirin imzalanmasından oluşur.

### Dışsal

Dış dünyadan gelen durum değişiklikleri, yani bunlar sistemin parçası değildir. Dışsal öğeler iki biçimde olabilir: "[kalıtsal](https://wiki.polkadot.network/docs/en/glossary#inherent)" ve "[işlemler](https://wiki.polkadot.network/docs/en/ sözlük#işlem)".

### Kesinlik

Geri alınamayan bir bloğun özelliği. Genellikle, oluşturulan bloklar gelecekte bir noktaya kadar nihai değildir - "olasılıksal kesinlik" durumunda belki de asla. Polkadot Röle Zinciri u
