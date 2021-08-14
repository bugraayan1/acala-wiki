---
tanım: Acala DeX Protokolü
---

# DeX

* [Genel Bakış](https://wiki.acala.network/learn/basics/dex#overview)
* [Kılavuz](https://wiki.acala.network/learn/basics/dex#guide)
  * [Acala Uygulaması Üzerinden](https://wiki.acala.network/learn/basics/dex#via-acala-app)
  * [Polkadot Kullanıcı Arayüzü Üzerinden](https://wiki.acala.network/learn/basics/dex#via-polkadot-ui)
    * [Değişimi Kontrol Et](https://wiki.acala.network/learn/basics/dex#check-exchange)
    * [Takas](https://wiki.acala.network/learn/basics/dex#swap)

## Genel Bakış

Acala DeX protokolü Uniswap'tan esinlenmiştir, ancak aUSD topluluğuna hizmet etmek için Acala Substrate zincirinin bir parçası olarak bir çalışma zamanı modülü olarak oluşturulmuştur. Her likidite havuzu, iki jeton bakiyesi içerir ve döviz kuru, basitçe, bir jetonun diğerini bölen miktarıdır. Kullanıcılar, bir sipariş defterine ihtiyaç duymadan anında token takasının keyfini çıkarırken, likidite sağlayıcısı, bir ücret kazanmak için bir havuzdaki iki tokenin likiditesini sağlayabilir.

Likidite sağlayıcı iadeleri için [Para Yatır ve Kazan](https://wiki.acala.network/learn/basics/deposit-and-earn) sayfasına bakın.

## Rehberlik etmek

1. Döviz Kurunu Kontrol Edin
2. Jetonları Değiştirin

### Acala Uygulaması ile

![Dapp](../../../.gitbook/assets/dex_app.png)

### Polkadot Kullanıcı Arayüzü Üzerinden

#### Değişimi Kontrol Edin

"Zincir durumu"nu kullanın -&gt; "dex" -&gt; `liquidityPool` havuzdaki USD miktarını ve seçilen jeton miktarını kontrol etmek için Onaltılık değeri sayıya dönüştürün.

![döviz kuru](../../../.gitbook/assets/dex_liquiditypool.png)

* DOT jetonlarının sayısı "0x00000000000000003d055121747a4273", "4397009815327097459" olarak
* aUSD jetonlarının sayısı `0x000000000000003babfb8f48dfeed58e`, `1100750556691660985742` olarak
* döviz kuru \(DOT to aUSD\) = USD token sayısı / DOT token sayısı = 250

#### Takas

"Dışsal Bilgiler" -&gt; "dex" -&gt; Jetonları takas etmek için "swapCurrency".

![takas](../../../.gitbook/assets/dex_swap.png)

* "Tedarik", ödediğiniz jetondur
* 'Hedef' satın almak istediğiniz jetondur, hedef fiyat kaymayı da kapsar
