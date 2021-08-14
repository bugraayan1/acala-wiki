# Tasfiye ve Acil Kapatma

## Tasfiye

Bir kredinin teminat oranı tasfiye oranının altındaysa, o zaman tasfiye edilecektir, yani kredinin teminatları, ödenmemiş borçları geri ödemek için bir ABD Doları'na satılacaktır. Teminatlar, miktara bağlı olarak, kabul edilebilir fiyat ve kayma ile otomatik olarak DeX'te satılacak ve geri kalanı teminat açık artırmasına konulacak.

## Kredi Sahibi Olarak

Krediniz risk altındaysa - yani teminat oranı gerekli tasfiye oranına yakındır, ör. cari teminat oranı %150, tasfiye oranı %135 iken, %10'luk bir aşağı yönlü fiyat hareketi tasfiyeyi tetikleyecektir. Bu nedenle, bir kredi sahibi olarak, krediniz tasfiye tehlikesi altındaysa, **krediyi ayakta tutmak için daha fazla teminat ekleyin** veya **geri ödeme borçları \(` Geri ödeme` düğmesi\) tasfiyeyi önlemek için teminat oranını** artırmak için.

**Riskli Pozisyon**

* **KIRMIZI**: Yüksek riskli pozisyon, mevcut teminat oranı likidasyon oranına \(Mandala Testnet'te: %10 içinde\) çok yakın.
* **SARI**: Orta riskli pozisyon, mevcut teminat oranı likidasyon oranına \(Mandala Testnet'te: %20'si dahilinde\) nispeten yakındır.
* **YEŞİL**: Güvenli pozisyon, mevcut teminat oranı likidasyon oranının \(Mandala Testnet'te: %20'nin üzerinde\) oldukça üzerinde.

Bir pozisyonu riske atmak için, daha fazla teminat eklemek için 'Para Yatırma' düğmesini veya bir USD borcunu geri ödemek için 'Geri Ödeme' düğmesini tıklayın.

**Yüksek Riskli Pozisyon**

![riskli](https://github.com/AcalaNetwork/Acala/wiki/image/liquidate-risky.png)

**Orta Riskli Pozisyon**

![](../../../.gitbook/assets/image%20%282%29.png)

## Tasfiye İhalelerine Katılın

Acala, kredi pozisyonlarını otomatik olarak değerlendirmek ve kredileri tasfiye etmek için [Off-Chain Worker](https://www.substrate.io/kb/learn-substrate/off-chain-workers) kullanır. Az teminatlı tasfiyelerde otomatik olarak DeX'te tasfiye edilecektir. Geri kalanlar teminat açık artırmalarında açık artırmaya çıkarılacak ve kullanıcılar teminatların ihalesine katılabilecek. Süreçle ilgili daha fazla ayrıntı [buradan](https://github.com/AcalaNetwork/Acala/wiki#25-automatic-liquidations-of-risky-cdps). Açık artırma türleri hakkında daha fazla bilgiyi [buradan](https://wiki.acala.network/learn/basics/auctions) okuyun

### DApp'te - Darbe

Nabız Uygulamasında \(bağlantı yakında...\) oturum açın, "Tasfiye" sekmesine gidin - "Teminat Açık Artırma" bölümüne gidin ve katılabileceğiniz açık artırmaları görebilirsiniz.

![açık artırma](https://github.com/AcalaNetwork/Acala/wiki/image/liquidate-auction.png)

### Olayları İzleme

Bunlar ilgili tasfiye ile ilgili olaylardır

* [**`LiquidateUnsafeCDP` olayı**](https://acala-testnet.subscan.io/event?module=cdpengine&event=liquidateunsafecdp).
* [**`NewCollateralAuction` event**](https://acala-testnet.subscan.io/event?module=auctionmanager&event=newcollateralauction)

Bu sistem borç ve artı açık artırmalarına da katılabilirsiniz. \([https://github.com/AcalaNetwork/Acala/wiki/6.-Auctions](https://github.com/AcalaNetwork/Acala/wiki/6.-Auctions)\).

* [**`NewDebitAuction` etkinliği**](https://acala-testnet.subscan.io/event?module=auctionmanager&event=newdebitauction)
* [**`NewSurplusAuction` etkinliği**](https://acala-testnet.subscan.io/event?module=auctionmanager&event=newsurplusauction)

### Guardian - Yapılandırılabilir İzleme ve Bot Çerçevesi

Guardian çerçevesini kullanarak açık artırmayı izleyin ve açık artırmaya katılın, örneklere bakın [buradan](https://github.com/open-web3-stack/guardian/tree/master/packages/example-guardian).

#### **Örnek: Tek Tıkla Teminat Açık Artırma Botunu Başlat**

1. **Heroku'yu başlatmak için 'Heroku'da Dağıt' düğmesini tıklayın**
2. **Yapılandırmayı doldurun**

![heroku](https://github.com/AcalaNetwork/Acala/wiki/image/liquidate-guardian2.png)

![heroku](https://github.com/AcalaNetwork/Acala/wiki/image/liquidate-guardian1.png)

* **Teklif Sahibi Adresi**: botun hesabı, bir USD veya diğer gerekli alım satım varlıklarına sahip olduğundan emin olun
* **SURI**: bu türetilmiş yol veya anımsatıcı olabilir
* **Marj**:
* **Uç Nokta**: En son WS uç noktası [burada](https://github.com/AcalaNetwork/Acala/wiki/1.-Get-Started#mandala-test-network)

#### **Örnek: Otomatik yeniden büyük harf kullanımı için CDP Guardian Bot**

CDP Guardian Bot, kredi pozisyonunuzu izleyecek ve teminat oranı belirli bir eşiğin altına düşerse kredilerinizi ayakta tutmak için otomatik olarak daha fazla teminat yatıracaktır. Daha fazlası [burada](https://github.com/open-web3-stack/guardian/tree/master/packages/example-guardian#cdp-guardian-bot).

1. **Teklifini izleyin 💰**

![heroku](https://github.com/AcalaNetwork/Acala/wiki/image/liquidate-guiardian3.png)

### Ryabina'dan Acala Bot

Ryabina, Acala kullanıcılarının finansal durumlarını - kredi pozisyonlarını, tasfiye olaylarını, bakiye değişikliklerini, likidite provizyonunu ve getirilerini izlemeleri için bir Telegram 🤖️ oluşturdu. [Buradan](https://t.me/Acala_Ryabina_bot) katılın.

Mini kılavuzu [buradan](https://medium.com/@ryabina/mini-guide-for-acala-network-telegram-bot-by-ryabina-92990e01120) okuyun.

![ryabina](https://github.com/AcalaNetwork/Acala/wiki/image/liquidate-ryabina1.png)

**USD Kredileri için Uyarılar Ekleyin**

![ryabina2](https://github.com/AcalaNetwork/Acala/wiki/image/liquidate-ryabina2.png)

**Tasfiye Açık Artırmaları için Uyarılar Ekleyin**

![ryabina3](https://github.com/AcalaNetwork/Acala/wiki/image/liquidate-ryabina3.png)

## Acil Kapatma

Acil kapatma, Acala'nın stabilcoin sistemini ciddi güvenlik tehditlerine karşı korumak için son çaredir. Kapatma, Acala yönetimi aracılığıyla tetiklenir. Varlıkların hedef fiyatlarını uygulayacak ve USD ve kredi sahiplerinin hak ettikleri varlıkların değerini almalarını sağlayacaktır.

Sistem, tek teminat veya küresel bir kapatma için kısmi kapatma kredileri verebilir. Bundan sonra küresel Acil Durum Kapatma prosedürünü detaylandıracağız. Küresel bir Acil Durum Kapatma tetiklendiğinde, aşağıdakiler gerçekleşir:

1. **Kapanma tetiklendi**: kullanıcıların kredi pozisyonlarını güncellemelerine izin verilmez, sistem her varlık için bir hedef fiyatı kilitler, ancak kullanıcılar herhangi bir ücretsiz teminatı, yani henüz USD ödünç almak için kullanılmamış teminatları çekmekte özgürdür.
2. **Kredi işleme**: sistem tüm açık artırmayı durduracak/temizleyecek, ödenmemiş kredileri ve borçları işleme koyacaktır, bu biraz zaman alabilir, ancak nihayetinde USD sahiplerinin geri alması için bir teminat varlıkları sepeti mevcut olacaktır.
3. **Borçları geri alın**: \#2 adımı tamamlandıktan sonra, sistem sıfır fazla ve sıfır borç başlangıç ​​durumuna dönecektir, kullanıcılar aUSD'lerini yakabilir ve teminat varlıklarının eşdeğer değerini geri alabilir \(bu bir karışım olabilir renBTC, DOT vb\). İade edilen teminatların karışımı, müsaitlik durumuna göre sistem tarafından belirlenecektir.

### Küresel Acil Durum Kapatma Kılavuzu

**Adım 1** Kapatma başlar... Kullanıcılar ücretsiz teminatlarını, yani USD kredileri için kullanılmayan/kilitli olmayan teminatları çekebilirler. Diğer kredi güncelleme işlemleri bundan sonra yasaktır.

![adım1](https://github.com/AcalaNetwork/Acala/wiki/image/shutdown-1.jpg)

**Adım 2** Tasfiye... Sistem tüm açık artırmaları, kredileri ve borçları temizleyecektir.

![adım2](https://github.com/AcalaNetwork/Acala/wiki/image/shutdown-2.jpg)

**Adım 3** USD teminatlarını geri alın... 2. Adım tamamlandıktan sonra, USD sahipleri ve kredi sahipleri teminat varlıklarını geri almak için USD yakabilir.

![adım3](https://github.com/AcalaNetwork/Acala/wiki/image/shutdown-3.jpg)
