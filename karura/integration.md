# Entegrasyon

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

Kaura'nın ED değeri 0.1 KAR'dır.

## İşlem ücretleri

Karura, gazın aksine ağırlığa dayalı ücretler kullanır, tahmin edilebilir ve sevkiyat öncesi ücretlendirilir. Daha fazla bilgi için [işlem ücreti](https://wiki.acala.network/karura/transaction-fees) sayfasına bakın.

## Karura ÇHC Uç Noktaları

* `wss://karura.api.onfinality.io/public-ws`
* `wss://karura-rpc-0.aca-api.network`
* `wss://karura-rpc-1.aca-api.network`
* `wss://karura-rpc-2.aca-api.network/ws`
* `wss://karura-rpc-3.aca-api.network/ws`

## Türler

Buddle [buraya](https://unpkg.com/browse/@acala-network/type-definitions@0.7.4-19/json/typesBundle.json) yazın.
