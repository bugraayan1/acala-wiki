# Karura Hesabı

Bu belge Acala, Karura, Polkadot ve Kusama hesap adreslerinin temellerini kapsar.

## Adres Biçimi

Acala ve Karura, Substrat tabanlı zincir adres biçimi SS58'i kullanır. Daha fazlasını [buradan](https://wiki.polkadot.network/docs/en/learn-accounts) okuyun.

* Acala adresleri her zaman 2 ile başlar.
* Karura adresleri l, r, p, q, o gibi küçük bir harfle başlayabilir...
* Polkadot adresleri her zaman 1 ile başlar.
* Kusama adresleri her zaman C, D, F, G, H, J gibi büyük harfle başlar...
* Genel Substrat adresleri 5 ile başlar.

## Varoluşsal Mevduat

Karura, toz hesaplarının şişmesini önlemek için bir [_existential mevduat_ \(ED\)](https://wiki.polkadot.network/docs/learn-accounts#existential-deposit-and-reaping) kullanır. Bir hesap ED'nin altına düşerse, kıt zincir üstü depolama kaynaklarını korumak için bu hesabın durumu blok zincirinden kaldırılacaktır. Bu hesaptaki bakiye kaldırılarak Hazine'ye bağışlanacak. Hesaba erişiminiz devam eder, ancak artık zincirleme durumu yoktur.

**Transferler:** A hesabından B hesabına bir miktar transfer ettiğinizde

* Transferden sonra A hesabının bakiyesi ED'nin altındaysa, kaldırılacaktır. Bu yüzden, A hesabını canlı tutmak için yeterli bakiye bıraktığınızdan emin olun.
* B hesabının bakiyesi yoksa ve transfer tutarı ED'nin altındaysa, durumu zincirden kaldırılacağı için B hesabı hiç tutar almıyormuş gibi olur. Bu nedenle, yeni bir hesabı canlı tutmak için yeterli miktarda gönderdiğinizden emin olun.

**Takas**: A jetonunu B jetonuyla değiştirdiğinizde, A jetonu bakiyesi ED gereksiniminin altına düşerse, işlem başarısız olabilir. Bu işlemi kolaylaştırmak ve ED'yi sizin için kontrol etmek için herkes acala.js SDK kullanarak bir ön uç oluşturabilir, ancak bunun her zaman farkında olacaksınız.

**Ödülleri talep edin**: LP jetonlarını veya diğer ödülleri talep ederken, talepten sonra bakiye ED gereksiniminin altındaysa, bakiye silinebilir.

ED, desteklenen tüm jeton hesapları ve her jeton hesabı türü için geçerlidir; KSM hesabının kendi ED gereksinimi vardır. Belirli bir jetonun bakiyesini değiştiren herhangi bir işlem, ör. takas, o zaman ED gereksiniminin farkında olacaksınız. Karura'da şu anda mevcut olan jetonlar için ED gereksinimlerinin listesi:

* KAR ED: 0.1 KAR
* kUSD ED: 0,01 kUSD
* KSM ED: 0.0001 KSM
* LKSM ED: 0.0001 LKSM

\([Kaynak kodu](https://meet.google.com/pye-erkv-duy)\)

## Hesap Oluşturma

Ağ yayınlanmadan önce ve ilk başlatma döneminde, Acala ve Karura hesabı oluşturmak için önerilen tek yöntem aşağıdadır:

* Polkadot{.js} Tarayıcı Eklentisi

## Polkadot{.js} Tarayıcı Eklentisi

### Tarayıcı Eklentisini Yükleyin

Tarayıcı eklentisi hem [Google Chrome](https://chrome.google.com/webstore/detail/polkadot%7Bjs%7D-extension/mopnmbcafieddcagagdcbnhejhlodfdd?hl=tr) \(ve Brave\ gibi Chromium tabanlı tarayıcılar) için kullanılabilir. ve [FireFox](https://addons.mozilla.org/en-US/firefox/addon/polkadot-js-extension). Eklentileri [buradan](https://polkadot.js.org/extension/) indirin.

![](../../../.gitbook/assets/screen-shot-2021-05-14-at-4.49.27-pm.png)

### Hesap oluştur

Tarayıcınızın üst çubuğundaki logoya tıklayarak Polkadot{.js} tarayıcı uzantısını açın. Aşağıdakinden farklı olmayan bir tarayıcı açılır penceresi göreceksiniz

![](../../../.gitbook/assets/screen-shot-2021-05-14-at-4.52.43-pm.png)

Büyük artı düğmesini tıklayın veya sağ üstteki küçük artı simgesinden "Yeni hesap oluştur"u seçin. Polkadot{.js} eklentisi daha sonra sizin için yeni bir tohum oluşturmak için sistem rastgeleliğini kullanacak ve bunu on iki kelime şeklinde size gösterecektir.

![](../../../.gitbook/assets/screen-shot-2021-05-14-at-4.53.46-pm.png)

Bu kelimeleri [burada açıklandığı gibi](https://wiki.polkadot.network/docs/en/learn-account-generation#storing-your-key-safely) yedeklemelisiniz. Tohumu güvenli, gizli ve güvenli bir yerde saklamak zorunludur. Herhangi bir nedenle Polkadot{.js} üzerinden hesabınıza erişemezseniz, "Hesap ekle" menüsünden "Önceden var olan tohumdan hesabı içe aktar"ı seçerek tohumunuzu yeniden girebilirsiniz.

### Adı Hesap ve Şifre

Hesap adı isteğe bağlıdır ve yalnızca sizin kullanımınız içindir. Şifre, bu hesabın bilgilerini şifrelemek için kullanılacaktır. Hesabı herhangi bir giden işlem için kullanırken veya bir mesajı kriptografik olarak imzalamak için kullanırken tekrar girmeniz gerekecektir.

Bu parolanın tohum ifadenizi KORUMADIĞINI unutmayın. Birisi anımsatıcı tohumunuzdaki on iki kelimeyi biliyorsa, şifreyi bilmese bile hesabınız üzerinde kontrol sahibi olmaya devam eder.

![](../../../.gitbook/assets/screen-shot-2021-05-14-at-4.54.44-pm.png)

### Acala Mainnet Adresini Ayarla

Şimdi adreslerin Acala mainnet adresleri olarak görüntülenmesini sağlayacağız.

Eklenti penceresinin sağ üst köşesindeki "Seçenekler"e tıklayın ve "Görüntülenen adres formatı" altında "Acala"yı seçin.

**Adresinizin biçimi yalnızca görseldir** - adresinizin bu temsilini elde etmek için kullanılan veriler aynıdır, dolayısıyla **aynı adresi birden çok yerde kullanabilirsiniz

uç zincirler**.

Hesabın simgesine tıklayarak adresinizi kopyalayabilirsiniz.

![](../../../.gitbook/assets/screen-shot-2021-05-14-at-4.58.59-pm.png)

### Karura Ana Ağı için Adres Ayarla

Eklenti penceresinin sağ üst köşesindeki "Seçenekler"e tıklayın ve "Görüntülenen adres formatı" altında "Karura"yı seçin.

**Adresinizin biçimi yalnızca görseldir** - adresinizin bu temsilini elde etmek için kullanılan veriler aynıdır, dolayısıyla **aynı adresi birden fazla zincirde kullanabilirsiniz**.

Hesabın simgesine tıklayarak adresinizi kopyalayabilirsiniz.

![](../../../.gitbook/assets/screen-shot-2021-06-08-at-2.27.20-pm.png)

### Polkadot Ana Ağı için Adres Ayarla

Eklenti penceresinin sağ üst köşesindeki "Seçenekler"e tıklayın ve "Görüntülenen adres formatı" altında "Polkadot"u seçin.

**Adresinizin biçimi yalnızca görseldir** - adresinizin bu temsilini elde etmek için kullanılan veriler aynıdır, dolayısıyla **aynı adresi birden fazla zincirde kullanabilirsiniz**.

Hesabın simgesine tıklayarak adresinizi kopyalayabilirsiniz.

![](../../../.gitbook/assets/screen-shot-2021-05-16-at-9.45.59-am.png)

### Kusama Mainnet Adresini Ayarla

Eklenti penceresinin üst kısmındaki "Seçenekler"e tıklayın ve "Görüntülenen adres biçimi" altında "Kusama"yı seçin.

**Adresinizin biçimi yalnızca görseldir** - adresinizin bu temsilini elde etmek için kullanılan veriler aynıdır, dolayısıyla **aynı adresi birden fazla zincirde kullanabilirsiniz**.

Hesabın simgesine tıklayarak adresinizi kopyalayabilirsiniz.

![](../../../.gitbook/assets/screen-shot-2021-05-16-at-9.46.09-am.png)

### Farklı zincir biçimleri için Adresi Dönüştür

Adresinizi farklı zincir biçimleri arasında dönüştürmek için [Alt Tarama Adresi Dönüştürme aracını](https://polkadot.subscan.io/tools/ss58_transform) kullanabilirsiniz.

Sol taraftaki giriş kutusuna herhangi bir adresi girin, ardından **`Dönüştür`** düğmesine tıklayın, sağ tarafta tüm zincirler için adres formatlarını görebilirsiniz.

## **Pulkawallet**

### **Polkawallet Uygulamasını Yükleyin**

Polkawallet uygulamasını [resmi web sitesi](https://polkawallet.io/) üzerinden indirin. Uygulama, iOS cihazlar için Apple App Store, Android cihazlar için Google Play ve Android APK olarak kullanılabilir.

### Hesap oluştur

1. "Hesap Oluştur" düğmesine tıklayın.

![](https://lh5.googleusercontent.com/VaB4EcpFPO9Qmvl2K_MVKk8rVevhEzDsD45WZzkWKe3B6DXyoSU8-IenMk3slTe4uGLVl4IzAEmOz-A0SyJ508VUy5DsD45WZzkWKe3slTe4uGLVl4IzAEmOz-A0SyJ508VUy5Ry7SyJ508VUy49U7SyJ508VUy49U7SyJ508VUy49U7SyJ508VUy49U7B)

2. Anımsatıcı ifadenizi güvenli bir yere kaydetmenin önemini açıklayan yeni bir ekran açılacaktır. "İleri" düğmesini tıklayın.

![](https://lh6.googleusercontent.com/509_xAUccOu0djt4YJZsvrLW4H_fdBxmOmMMwpRrseGSt9xcyZdx4Tgge7ZofXk6um7rSR6LcPL7c23rJHF2ZHv7Flql2SvrLW4H_fdBxmOmMMwpRrseGSt9xcyZdx4Tgge7ZofXk6um7rSR6LcPL7c23rJHF2ZHv7Flql2SvPinRpLql2Sb)

‌3. Anımsatıcı ifadeniz görünecektir. Anımsatıcıyı bir kağıda yazın ve güvenli bir yerde saklayın. "İleri" düğmesine tıklayın.

![](https://lh5.googleusercontent.com/XD1NG32OkmzZYToN8Fb-noLzUJmacWIACYhi-gSyV3-s58n4Ovu6sS0qQMRe1NkMMyLA4LBz_wEHRnEDwVnQgEaXQwCrgvArr8)

4. Sözcükleri doğru sırada girerek anımsatıcınızı onaylayın. Tamamlandığında "İleri" düğmesine tıklayın.

![](https://lh4.googleusercontent.com/ROVs8A4woJy9RYKmsGd6Jm1W8GMzG_cpB6ba3XLViS18GMTmRK0giSV7qkDh2XZrKxxLv4LFLEFuiRT6Lw3wri8yu6cT9tBMxyw5v)

### **Hesap Adı ve Şifre**

Hesabınıza bir ad verin ve güçlü bir parola oluşturun \(en az 6 karakter\). Tamamlandığında "İleri" düğmesine tıklayın.

![](https://lh4.googleusercontent.com/PWXIJxAuCBlb-QGBrpce0gvFgG_C_jWUL125eOU_ke_thRY4WDhUq1AvDa6bAWWy_sD5BXp40gM5zzJRdkDGF5XrtLEuLD5Twdj02sGFD5Twdj2r)

Cüzdanınız şimdi kuruldu! Ekran varsayılan olarak Polkadot ağına dönecektir. Hesap adının altındaki gri metne bakarak hangi ağa bağlı olduğunuzu belirleyebilirsiniz. Bu ekran görüntüsünde "Polkadot" yazıyor.

![](https://lh5.googleusercontent.com/xlFLRGhSFMpRc1QeJrObC8vazj7YCLIe2AvW-euSwN4bvjlZWhTbcyBxF4SPTXQGuOCJtdxMW_1IMNyoL88RzC51RGN7CkLep_k58TbcyBxF4SPTXQGuOCJtdxMW_1IMNyoL88RzC51RGN7CkLep_kOXT0)

### Polkadot Mainnet Adresini Ayarla

1. Sağ üst köşedeki menü düğmesine tıklayın.

 ![](https://i.imgur.com/JwPrsVe.jpg%20=250x)

2. Açılan menüde Polkadot logosunu seçin, ardından ana ekranda görünen adrese basın.

 ![](https://i.imgur.com/YGx8nne.jpg%20=250x)

### Kusama Mainnet Adresini Ayarla

1. Sağ üst köşedeki menü düğmesine tıklayın.
2. Açılan menüde Kusama logosunu seçin, ardından ana ekranda görünen adrese basın.

### Acala Mainnet Adresini Ayarla \(Çok Yakında\)

### Karura Mainnet Adresini Ayarla \(Çok Yakında\)

 



###
