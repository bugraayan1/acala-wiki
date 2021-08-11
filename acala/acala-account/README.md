# Acala Hesabı

Bu belge Acala, Karura, Polkadot ve Kusama hesap adreslerinin temellerini kapsar.

## Adres Formatı

Acala ve Karura, Substrat tabanlı zincir adres biçimi SS58'i kullanır. Daha fazlasını [buradan](https://wiki.polkadot.network/docs/en/learn-accounts) öğrenebilirsiniz.

* Acala adresleri her zaman 2 ile başlar.
* Karura adresleri l, r, p, q, o gibi küçük bir harfle başlayabilir...
* Polkadot adresleri her zaman 1 ile başlar.
* Kusama adresleri her zaman C, D, F, G, H, J gibi büyük harfle başlar...
* Jenerik Substrat adresleri 5 ile başlar.

## Hesap Oluşturma 

Ağın aktif olmadan önceki ve ilk başlatma dönemlerinde, Acala ve Karura hesabı oluşturmak için önerilen tek yöntem aşağıdadır:

* Polkadot{.js} Tarayıcı Eklentisi

## Polkadot{.js} Tarayıcı Eklentisi

### Eklentinin Kurulumu

Tarayıcı eklentisinin kurulumu [Google Chrome](https://chrome.google.com/webstore/detail/polkadot%7Bjs%7D-extension/mopnmbcafieddcagagdcbnhejhlodfdd?hl=en) \(Brave gibi Chromium tabanlı tarayıcılar\) ve [FireFox](https://addons.mozilla.org/en-US/firefox/addon/polkadot-js-extension) için sorunsuz olarak gerçekleşmektedir. Eklentiye [buradan](https://polkadot.js.org/extension/) ulaşabilirsiniz.

![](../../.gitbook/assets/screen-shot-2021-05-14-at-4.49.27-pm.png)

### Hesap Oluşturma

Tarayıcınızın üst çubuğundaki logoya tıklayarak Polkadot{.js} tarayıcı uzantısını açın. Aşağıdakinden farklı olmayan bir açılır pencere göreceksiniz.

![](../../.gitbook/assets/screen-shot-2021-05-14-at-4.52.43-pm.png)

Büyük artı düğmesini tıklayın veya sağ üstteki küçük artı simgesinden "Yeni hesap oluştur"u seçin. Polkadot{.js} eklentisi daha sonra sizin için yeni bir tohum cümlesi oluşturmak için sistem rastgeleliğini kullanacak ve bunu on iki kelime şeklinde size gösterecektir.

![](../../.gitbook/assets/screen-shot-2021-05-14-at-4.53.46-pm.png)

Bu kelimeleri [burada açıklandığı şekilde](https://wiki.polkadot.network/docs/en/learn-account-generation#storing-your-key-safely) muhafaza etmelisiniz. Tohum cümlenizi güvenli, gizli ve güvenli bir yerde saklamak zorunludur. Herhangi bir nedenle Polkadot{.js} üzerinden hesabınıza erişemezseniz, "Hesap ekle" menüsünden "Önceden var olan tohum cumlesinden hesabı içe aktar"ı seçerek tohum cumlenizi yeniden girebilirsiniz.

### İsim Hesap & Şifre

Hesap adı isteğe bağlıdır ve yalnızca sizin kullanımınız içindir. Şifre, bu hesabın bilgilerini şifrelemek için kullanılacaktır. Hesabı herhangi bir giden işlem için kullanırken veya bir mesajı kriptografik olarak imzalamak için kullanırken tekrar girmeniz gerekecektir.

Bu parolanın tohum ifadenizi KORUMADIĞINI unutmayın. Birisi anımsatıcı tohumunuzdaki on iki kelimeyi biliyorsa, şifreyi bilmese bile hesabınız üzerinde kontrol sahibi olmaya devam eder.

![](../../.gitbook/assets/screen-shot-2021-05-14-at-4.54.44-pm.png)

### Acala Mainnet Adresini Ayarlama

Şimdi adreslerin Acala mainnet adresleri olarak görüntülenmesini sağlayacağız.

Eklenti penceresinin sağ üst köşesindeki "Seçenekler"e tıklayın ve "Görüntülenen adres formatı" altında "Acala"yı seçin.

**Adresinizin formatı sadece görseldir** - adresinizin bu temsilini elde etmek için kullanılan veriler aynıdır, dolayısıyla **aynı adresi birden fazla zincirde kullanabilirsiniz**. 

Hesabın simgesine tıklayarak adresinizi kopyalayabilirsiniz.

![](../../.gitbook/assets/screen-shot-2021-05-14-at-4.58.59-pm.png)

### Karura Mainnet için Adres Ayarlama

Eklenti penceresinin sağ üst köşesindeki "Seçenekler"e tıklayın ve "Görüntülenen adres formatı" altında "Karura"yı seçin.

**Adresinizin biçimi yalnızca görseldir** - adresinizin bu temsilini elde etmek için kullanılan veriler aynıdır, dolayısıyla **aynı adresi birden fazla zincirde kullanabilirsiniz**.

Hesabın simgesine tıklayarak adresinizi kopyalayabilirsiniz.

![](../../.gitbook/assets/screen-shot-2021-06-08-at-2.27.20-pm.png)

### Polkadot Mainnet Adresini Ayarlama

Eklenti penceresinin sağ üst köşesindeki "Seçenekler"e tıklayın ve "Görüntülenen adres formatı" altında "Polkadot"u seçin.

**Adresinizin biçimi yalnızca görseldir** - adresinizin bu temsilini elde etmek için kullanılan veriler aynıdır, dolayısıyla **aynı adresi birden fazla zincirde kullanabilirsiniz**.

Hesabın simgesine tıklayarak adresinizi kopyalayabilirsiniz.

![](../../.gitbook/assets/screen-shot-2021-05-16-at-9.45.59-am.png)

### Kusama Mainnet Adresini Ayarlama

Eklenti penceresinin üst kısmındaki "Seçenekler"e tıklayın ve "Görüntülenen adres biçimi" altında "Kusama"yı seçin.

**Adresinizin biçimi yalnızca görseldir** - adresinizin bu temsilini elde etmek için kullanılan veriler aynıdır, dolayısıyla **aynı adresi birden fazla zincirde kullanabilirsiniz**. 

Hesabın simgesine tıklayarak adresinizi kopyalayabilirsiniz.

![](../../.gitbook/assets/screen-shot-2021-05-16-at-9.46.09-am.png)

### Farklı zincir biçimleri için Adresi Dönüştürme

Subscan Adres dönüştürme aracına [buradan](https://polkadot.subscan.io/tools/ss58_transform) ulaşabilirsiniz, adresinizi farklı blokzincir formatlarına dönüştürebilirsiniz.

Sol taraftaki giriş kutusuna herhangi bir adresi girin, ardından **`Transform`** düğmesine tıklayın, sağ tarafta tüm zincirler için adres formatlarını görebilirsiniz..

## **Polkawallet**

### **Polkawallet Uygulamasını Yükleme**

Polkawallet uygulamasını [resmi sitesinden](https://polkawallet.io/) indirin. Uygulama, iOS cihazlar için Apple App Store, Android cihazlar için Google Play ve Android APK olarak kullanılabilir.

### Hesap Oluşturma

1. "Hesap Oluştur" butonuna tıklayın.

![](https://lh5.googleusercontent.com/VaB4EcpFPO9Qmvl2K_MVKk8rVevhEzDsD45WZzkWKe3B6DXyoSU8-IenMk3slTe4uGLVl4IzAEmOz-A0SyJ508VUy49UfiGpsBT5R7q2QRmeybP1cE-2fU52iOdoudgcdmsLv_Kl)

2. Tohum cümleniz olan anımsatıcı ifadenizi güvenli bir yere kaydetmenin önemini açıklayan yeni bir ekran açılacaktır. "İleri" düğmesini tıklayın.

![](https://lh6.googleusercontent.com/509_xAUccOu0djt4YJZsvrLW4H_fdBxmOmMMwpRrseGSt9xcyZdx4Tgge7ZofXk6um7rSR6LcPL7c23rJHF2ZHv7FlLl2SbYciqd3-ck_v_hlco0RRP7oPpin90nv2YETvvN_cEb)

‌3. Anımsatıcı ifadeniz görünecektir. Anımsatıcıyı bir kağıda yazın ve güvenli bir yerde saklayın. "İleri" düğmesine tıklayın.

![](https://lh5.googleusercontent.com/XD1NG32OkmzZYToN8Fb-noLzUJmacWIACYhi-gSyV3-s58n4Ovu6sS0qQMRe1NkMMyLA4LBz_wEHRnEDwVnQgEaXQwCrgvUr0fNvA8SDilS7mrrnP--9bx3-SnHaioy_prFD4KoE)

4. Kelimeleri doğru sırayla girerek anımsatıcınızı onaylayın. Tamamlandığında "İleri" düğmesine tıklayın.

![](https://lh4.googleusercontent.com/ROVs8A4woJy9RYKmsGd6Jm1W8GMzG_cpB6ba3XLViS18GMTmRK0giSV7qkDh2XZrKxxLv4LFLEFuiRT6Lw3wri8yu6cT9tBMyw00vMhxq5Vmwb2qBOUg9-Eey7RHMbh4araqvk7P)

### **İsim Hesabı ve Şifresi**

Hesabınıza bir ad verin ve güçlü bir parola oluşturun \(en az 6 karakter\). Tamamlandığında "İleri" düğmesine tıklayın.

![](https://lh4.googleusercontent.com/PWXIJxAuCBlb-QGBrpce0gvFgG_C_jWUL125eOU_ke_thRY4WDhUq1AvDa6bAWHWy_sD5BXp40gM5zzJRdkDGF5XrtLEuLD5TwJ1sV8FDdjr1QRjDm9I-hzfXGsqBLsq0QVFgb02)

Cüzdanınız şimdi kuruldu! Ekran varsayılan olarak Polkadot ağına dönecektir. Hesap adının altındaki gri metne bakarak hangi ağa bağlı olduğunuzu belirleyebilirsiniz. Bu ekran görüntüsünde "Polkadot" yazıyor.

![](https://lh5.googleusercontent.com/xlFLRGhSFMpRc1QeJrObC8vazj7YCLIe2AvW-euSwN4bvjlZWhTbcyBxF4SPTXQGuOCJtdxMW_1IMNyoL88RzC51RGN7CkLepjjOXTnJkEkp0ZSRzS58F7rAVMamcuXJ_01S6AhE)

### Polkadot Mainnet için Adres Ayarlama

1. Sağ üst köşedeki menü düğmesine tıklayın.

 ![](https://i.imgur.com/JwPrsVe.jpg%20=250x)

2. Açılan menüde Polkadot logosunu seçin, ardından ana ekranda görünen adrese basın.

 ![](https://i.imgur.com/YGx8nne.jpg%20=250x)

### Set Address for Kusama Mainnet

1. Sağ üst köşedeki menü düğmesine tıklayın.
2. Açılan menüde Kusama logosunu seçin, ardından ana ekranda görünen adrese basın.

### Acala Mainnet Adresini Ayarla \(Çok Yakında\)

### Karura Mainnet Adresini Ayarla \(Çok Yakında\)

 



###  

