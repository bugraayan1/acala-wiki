# Birleştirilebilir Zincirler

Şu anda, zincirler arası mesaj geçişi ve parachainler yalnızca Polkadot'un test ağında [Rokoko](https://wiki.polkadot.network/docs/en/build-parachains-rococo) mevcuttur. Acala'nın test ağı Mandala henüz Rococo'da piyasaya sürüldü ve zincirler arası token transferlerini ve diğer işlevleri test etmeye devam ediyor.

Acala ile \#Birleştirilebilir bir çalışma yapmak için lütfen bizimle iletişime geçin!

## Acala ile Birleştirilebilir Olma

* Acala Mandala PC2, Rococo [burada](https://polkadot.js.org/apps/?rpc=wss://rococo-rpc.polkadot.io#/parachains) yayındadır.

#### Adım 1 Acala Jetonlarını Destekleyin

Acala zincirinde verilen USD, ACA, renBTC, LDOT vb. tokenleri almak için Acala'yı yedek zincir olarak yapılandırmanız ve jeton sembolleri eklemeniz gerekir. Aşağıdaki adımları izleyin:

1. CurrencyId'e jeton ekleyin. USD ekleyen Laminar'ın [buradaki örneği](https://github.com/laminar-protocol/laminar-chain/blob/a07ea4aa75bce5d30a24ce2e7a506dda5e22013f/primitives/src/lib.rs#L83).
2. CurrenyId için metin sembolü ekleyin. [Buradaki örnek](https://github.com/laminar-protocol/laminar-chain/blob/a07ea4aa75bce5d30a24ce2e7a506dda5e22013f/primitives/src/lib.rs#L101) "AUSD" ekleyin.
3. "Tokens" modülünü çalışma zamanınıza entegre edin.

#### 2. Adım xToken'ı Kurun ve Rezerv Zincirini Yapılandırın

"Orml-xtokens", belirteç transferleri için [Polkadot Cross-Consensus Message Format \(XCM\)](https://github.com/paritytech/xcm-format) konseptinin bir uygulamasıdır. xtoken için kaynak koda [buradan](https://github.com/open-web3-stack/open-runtime-module-library/tree/sw/rococo-v1/xtokens) ve xcm-support'a [buradan] (https://github.com/open-web3-stack/open-runtime-module-library/blob/sw/rococo-v1/xtokens/src/lib.rs) ulaşabilirsiniz.

1. xToken'ı zincirinize kurun. xToken ekleyen Laminar'ın [buradaki örneğinden](https://github.com/laminar-protocol/laminar-chain/blob/a07ea4aa75bce5d30a24ce2e7a506dda5e22013f/runtime/dev/src/lib.rs#L861-L960) yardım alabilirsiniz.
2. Belirtilen jetonlar için Acala'yı Yedek Zincir olarak yapılandırın.
   1. Jeton ve yedek zincirini ekleyin. [Burada örnek](https://github.com/laminar-protocol/laminar-chain/blob/a07ea4aa75bce5d30a24ce2e7a506dda5e22013f/runtime/dev/src/lib.rs#L916) Acala'yı aUSD için yedek zincir olarak ekleme.
   2. Yedek varlıkları yapılandırın. [Buradaki örnek](https://github.com/laminar-protocol/laminar-chain/blob/a07ea4aa75bce5d30a24ce2e7a506dda5e22013f/runtime/dev/src/lib.rs#L916).

#### 3. Adım Jetonlarınızı Acala'da kullanılabilir hale getirin

Jeton sembollerinizi ekleyin ve Acala'ya bir PR yapın. [Örnek](https://github.com/AcalaNetwork/Acala/pull/730) Plasm'ın PLM eklemek için PR'ı.

#### 4. Adım HRMP Kanalını Açın

Zinciriniz zaten parachain olarak Rokoko'ya bağlı olacaktır. XCMP \(Cross-chain Message Passing\) sitll uygulanırken - bu, Röle zincirinden geçmeden çapraz zincir mesajları gönderirken, bir stop-gap protokolü HRMP \(Horizontal Relay-routed Message Passing\) yerindedir.

Çapraz zincir mesajları göndermek ve almak için iki para zincirinin her iki tarafta HRMP kanalını açması gerekecektir. [HRMP Kanalını açmak için buradaki talimatlar](open-hrmp-channel.md).

## \#Birleştirilebilir

Polkadot/Kusama'daki tüm zincirler, değer alışverişinden durum değiştirmeye kadar birbirleriyle _**birleştirilebilir**_ olacaktır. Örneğin, zincirler sadece güvenilir bir şekilde değerleri aktaramazlar, aynı zamanda palet/akıllı sözleşme fonksiyonlarını da çağırabilirler. 1 tıkla PolkaBTC'yi Interlay zincirinde basmak, PolkaBTC'yi Acala'ya aktarmak ve hepsini tek bir işlemde USD karşılığında teminatlandırmak mümkündür.

Acala şu anda aşağıdaki \(potansiyel\) parachainler ile birleştirilebilir, lütfen kendinizi eklemek için bu Repo'ya PR:

* Plasm
* Interlay
* Phala


Denemek ve bizimle birlikte zincirler arası testler yapmak isterseniz lütfen bizimle iletişime geçin!
