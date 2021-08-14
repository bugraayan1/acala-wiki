# Jeton Transferi

Karura, Kusama'dan farklı jeton türlerini destekler ve jetonları aktarmanın çeşitli yollarına izin verir. Bu kılavuz, Karura'da bulunan tokenler, transferler için kullanılabilecek araçlar, transfer işlemlerinin nasıl gönderileceği, bu işlemlerin nasıl izleneceği ve izleneceği hakkında bilgi verecektir.

## Simge Türleri

* **Yerel Ağ Simgesi**
  * KAR
* **Yerel Protokol Simgeleri**
  * LKSM: Liquid Staking protokolünden tokenize edilmiş stake edilmiş KSM
  * kUSD: çoklu teminatlı stabilcoin
* **Yabancı Jetonlar**
  * KSM: Kusama Relay Chain'den Karura'ya geçti
  * Jetonlar diğer parachainlerden alınmıştır
  * ETH, renBTC veya Compound CASH gibi diğer blok zincirlerinden çapraz tokenler
* **ERC20 Jetonları**
  * Karura EVM'de dağıtılan ERC20 sözleşmeleri tarafından verilen jeton

## Araçlar

* JS/TS SDK: [https://github.com/AcalaNetwork/acala.js](https://github.com/AcalaNetwork/acala.js)
* Blockchain gezgini: [http://karura.subscan.io](http://karura.subscan.io)
* api-sidecar: [https://github.com/paritytech/substrate-api-sidecar](https://github.com/paritytech/substrate-api-sidecar)
* txwrapper: [https://github.com/AcalaNetwork/txwrapper](https://github.com/AcalaNetwork/txwrapper)
* Alt Sorgu: [https://github.com/AcalaNetwork/acala-subql](https://github.com/AcalaNetwork/acala-subql)

## Jeton Gönder

### İşlemler

#### para birimleri.transferi

* [https://karura.subscan.io/extrinsic?module=Currencies&call=transfer](https://karura.subscan.io/extrinsic?module=Currencies&call=transfer)
* Bu, ağda desteklenen herhangi bir belirteç göndermek için kullanılabilir

#### para birimleri.transferNativeCurrency

* [https://karura.subscan.io/extrinsic?module=Currencies&call=transfer\_native\_currency](https://karura.subscan.io/extrinsic?module=Currencies&call=transfer_native_currency)
* Bu, yerel belirteç \(KAR\) göndermek için kullanılabilir. Para birimlerine kıyasla biraz daha ucuz işlem ücretlerine sahiptir.transfer

#### bakiyeler.aktarım

* [https://karura.subscan.io/extrinsic?module=Balances&call=transfer](https://karura.subscan.io/extrinsic?module=Balances&call=transfer)
* 'currencies.transferNativeCurrency' ile aynı
* Polkadot / Kusama ve diğer çoğu Substrat tabanlı zincirlerle uyumludur.

## Jeton Al

Gelen bakiye transferlerini tespit etmenin birden fazla yolu vardır:

* Olayları izleyin
* Depolama değişikliklerine abone olun
* İşlemleri izleyin

### Olayları İzleme

Olayları izlemek, gelen bakiye transferlerini izlemenin önerilen bir yoludur. Doğrudan bir işlem tarafından başlatılmamış olanlar da dahil olmak üzere **TÜM** türdeki transfer işlemlerini gerçekleştirebilir \(ör. gecikmeli proxy\).

#### bakiyeler.aktarım

* [https://karura.subscan.io/event?module=Balances&event=Transfer](https://karura.subscan.io/event?module=Balances&event=Transfer)
* Yerel bir belirteç aktarımı gerçekleştiğinde yayılır.

#### para birimleri.transferi

* [https://karura.subscan.io/event?module=Currencies&event=Transfered](https://karura.subscan.io/event?module=Currencies&event=Transfered)
* Bir jeton transferi gerçekleştiğinde ortaya çıkar.
* NOT: Transfer yapmak için Balances.transfer kullanıldığında bu yayılmaz.

#### para birimleri.depozito

* [https://karura.subscan.io/event?module=Currencies&event=Yatırılan](https://karura.subscan.io/event?module=Currencies&event=Yatırılan)
* Bir hesaba bir jeton basıldığında ortaya çıkar. Bu, zincirler arası bir transfer olduğunda veya sabit para basan bir işlem olduğunda olabilir.

### Depolama, RPC'yi değiştirir

* [state\_subscribeStorage](https://polkadot.js.org/docs/substrate/rpc#subscribestoragekeys-vecstoragekey-storagechangeset)
  * Hesap bakiyeleri listesine abone olun. Ancak, bağlantı hataları veya blok zincirinin yeniden düzenlenmesi nedeniyle abonelik teslimini garanti etmez.

### İşlemleri İzleme

Her blokta işlemleri getirmek, transfer işlemlerini kontrol etmek ve transfer işleminin başarılı olup olmadığını kontrol etmek mümkündür. Bununla birlikte, bu muhtemelen yanlış negatif sonuçlar verebilir, yani depozito alındı, ancak transfer için çeşitli yollar nedeniyle tanınmadı.

Doğrudan transfer işlemleri için Token Gönder bölümüne bakın. Ek olarak, transfer işlemlerini tek tek göndermeye ek olarak, toplu gönderme transfer işlemleri için yaygın yardımcı yöntemler vardır:

#### yardımcı program.batch

* [https://karura.subscan.io/extrinsic?module=Utility&call=batch](https://karura.subscan.io/extrinsic?module=Utility&call=batch)
* Bu toplu işlem göndermek için kullanılabilir
* NOT: toplu işlemler her zaman başarı olaylarını yayacaktır.
  * `utility.BatchCompleted` olayı tüm işlemlerin başarılı olduğunu gösterir
  * `utility.BatchInterrupted` olayı hangi işlemin başarısız olduğunu gösterir. Başarısız olan işlemden önceki işlemler başarıyla yürütülür ve geri alınmayacaktır.

#### yardımcı program.batchTümü

* [https://karura.subscan.io/extrinsic?module=Utility&call=batch\_all](https://karura.subscan.io/extrinsic?module=Utility&call=batch_all)
* Bu, yardımcı program.batch'e benzer, ancak başarısız işlemde tüm işlemleri geri alır.
