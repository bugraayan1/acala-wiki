# HRMP Kanal Açma

HRMP kanallarını açma adımları: 1. Gönderici parachain, bir init açık kanal isteği gönderir. 2. Alıcı parachain isteği kabul eder.

Yukarıdaki adımlar, gönderenin veya alıcının kısmından `Xcm::Transact` aracılığıyla yapılır.

### init açık kanal isteği gönder

#### Kodlanmış işlem oluşturun

PolkadotJS uygulamasında canlı Rokoko ağına geçin. **Geliştirici -&gt; Javascript** bölümü.

Kodlama kodunu çalıştırın, demo alıcı kimliği '777'yi alıcınızla değiştirmeyi unutmayın:

```javascript
const tx = api.tx.hrmp.hrmpInitOpenChannel(777, 8, 1024);
console.log(tx.toHex())
```

Sonuç "0x3c041600090300000800000000040000" gibi olacaktır, baştaki onaltılı "3c04" kaldırılacak ve kodlanmış sonuç "0x1600090300000800000000040000" olacaktır.

#### İstek gönder

PolkadotJS uygulamasına gidin, gönderen parachain'e geçin. **Geliştirici -&gt; Sudo** bölümünü açın.

İşlemi göndermek için `xcmHandler -> sudoSendXcm` kullanın.

İsteğin gönderildiğini onaylamak için canlı Rokoko'ya geçin, **Geliştirici -&gt; Zincir Durumu**, **hrmp -&gt; hrmpOpenChannelRequests**.

### Kanal isteğini kabul etme

#### Kodlanmış işlem oluşturun

PolkadotJS uygulamasında canlı Rokoko ağına geçin. **Geliştirici -&gt; Javascript** bölümünü açın.

Kodlama kodunu çalıştırın, demo alıcı para kimliği "666"yı alıcınızla değiştirmeyi unutmayın:

```javascript
const tx = api.tx.hrmp.hrmpAcceptOpenChannel(666);
konsol.log(tx.toHex())
```

Sonuç "0x1c0416019a020000" gibi olacaktır, baştaki onaltılı "1c04" kaldırılır ve kodlanmış sonuç "0x16019a020000" olur.

#### İstek gönder

PolkadotJS uygulamasına gidin, gönderen parachain'e geçin. **Geliştirici -&gt; Sudo** bölümünü açın.

İşlemi göndermek için `xcmHandler -> sudoSendXcm` kullanın.

