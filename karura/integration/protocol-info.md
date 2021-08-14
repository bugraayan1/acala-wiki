# Protokol Bilgisi

## Jetonlar

* **Jeton ondalık sayıları:**
  * Karura \(KAR\): 12
  * LKSM: 12
  * Karura Doları \(kUSD\): 12
* **Temel birim:** "Tahta"
* **Bakiye türü:**
* **KAR'ın Toplam Sabit Arzı:** 100.000.000

## Hesap

### Adres Biçimi

Karura, [SS58 \(Substrate\) adres biçimini](https://github.com/paritytech/substrate/wiki/External-Address-Format-%28SS58%29) kullanır. İlgili SS58 önekleri şunlardır:

* **Acala**: 10 \([ss58 kayıt ayrıntıları](https://github.com/paritytech/substrate/blob/df4a58833a650cf37fc97764bf6c9314435e3cb2/ss58-registry.json#L103-L111)\)
* **Karura**: 8 \([ss58 kayıt ayrıntıları](https://github.com/paritytech/substrate/blob/df4a58833a650cf37fc97764bf6c9314435e3cb2/ss58-registry.json#L85-L92)\)
* **Mandala**: 42

### Varoluşsal Mevduat

Karura, toz hesaplarının şişmesini önlemek için bir _varoluşsal birikim_ \(ED\) kullanır. Bir hesap ED'nin altına düşerse, bu hesaptan kaldırılır ve Hazine'ye bağışlanır.

Yerel belirteç KAR'nin ED'si çalışma zamanında yapılandırılır. Yerel olmayan tokenler \(KSM, kUSD, BTC vb\) SDK aracılığıyla sorgulanabilir. ED miktarı artırılamaz, yalnızca azaltılabilir, bu nedenle genellikle daha yüksek bir sayı ile başlar.

"pallet_balances" ve "orml_tokens" içindeki "transfer" ve "deposit", alıcı hesabının ED'sini kontrol edecektir. ED gereksinimlerini karşılamadığı için bir işlem başarısız olabilir, tipik bir kullanıcı, simge A bakiyesinin artık ED gereksinimlerini karşılamadığı durumda, simge B için simge A'yı değiştirir. Bir ön uç DApp, bu tür olaylar için kontroller yapacak ve kullanıcıyı uyaracaktır.

ED hakkında daha fazla bilgiyi [buradan](https://github.com/AcalaNetwork/Acala/wiki/A.-Existential-Deposit) okuyun.

## İşlem ücretleri

Karura, gazın aksine ağırlığa dayalı ücretler kullanır, tahmin edilebilir ve sevkiyat öncesi ücretlendirilir. Daha fazla bilgi için [işlem ücreti](https://wiki.acala.network/karura/transaction-fees) sayfasına bakın.

## Türler

Buddle [buraya](https://unpkg.com/browse/@acala-network/type-definitions@0.7.4-19/json/typesBundle.json) yazın.

## JS SDK'sı

Acala.js: [https://github.com/AcalaNetwork/acala.js](https://github.com/AcalaNetwork/acala.js)

Belgeler: [https://github.com/AcalaNetwork/acala.js/wiki](https://github.com/AcalaNetwork/acala.js/wiki)

Lütfen ayrıca [polkadot.js belgelerine](https://polkadot.js.org/docs/api/) bakın.
