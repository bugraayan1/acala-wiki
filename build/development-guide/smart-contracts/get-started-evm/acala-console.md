# Acala Konsolu

Acala Konsolu, blok zincirinin durumunu sorgulayabileceğiniz bir Acala Düğümü ile iletişim kurmak için kullanılır. Buradan hesap bakiyeleri, blok bilgileri vb. ve zincirin çeşitli çalışma zamanı modülleriyle ilgili bilgi alabilir ve etkileşim kurabilirsiniz. Örn. bir jeton aktarabilir veya DeX'te jeton takası yapabilirsiniz.
Acala Konsoluna buradan ulaşabilirsiniz: [https://console.acala.network/](https://console.acala.network/).

Konsol, Polkadot tarafından sağlanan ve çeşitli Substrate düğümlerine bağlanabilen oluşturulmuş bir ön uçtur. Konsolu kendi düğümünüze bağlamak için sol üst köşedeki açılır menüyü açın

![](https://i.imgur.com/8G8Rnbe.png)

'Geliştirme' bölümünü açın, yerel Acala düğümünüze bağlanmak için 'Yerel Düğüm'ü seçin.

![](https://i.imgur.com/TygeyXu.png)

Dağıtılan bir düğüme bağlanmak için "Özel"i seçin ve Websocket URL'sini "özel uç nokta" giriş kutusuna yapıştırın. Dağıtılmış düğümleri burada \[TODO\] bulabilirsiniz.

```text
wss://node-6757141250775003136.rz.onfinality.io/ws?apikey=086df60c-6a2d-414e-add2-cc0b74b6d00b
```

Ardından üst kısımdaki 'Anahtar'ı tıklayın ve sayfanın yenilenmesini ve ağa bağlanmasını bekleyin. Mevcut uç noktanız seçiminizle zaten eşleşiyorsa, 'Geçiş' düğmesi devre dışı bırakılır.

### Bakiye Kontrolü

Üst gezinme çubuğundaki "Geliştirici" sekmesine tıklayın ve açılır listeden "Zincir Durumu"nu seçin.

![](https://i.imgur.com/BvFEcsZ.png)

Ardından "seçili durum sorgusu"na tıklayın ve "belirteç"i seçin.

"Hesap Kimliği" açılır menüsünden "Alice"yi seçin.

'CurrencyId'den 'Token'ı ve 'Token: TokenSymbol' olarak 'DOT'u seçin

Çağrıyı başlatmak için `+` düğmesine basın.

![](https://i.imgur.com/5hdanQC.png)

Alice'in DOT bakiyesi aşağıda gösterilecektir.

![](https://i.imgur.com/nOB7L3k.png)
