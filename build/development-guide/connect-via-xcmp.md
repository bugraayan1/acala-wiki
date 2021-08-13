# Polkadot/Kusama ile bağlanın

Şu anda, zincirler arası mesaj geçişi ve parachainler yalnızca Polkadot'un test ağında [Rokoko](https://wiki.polkadot.network/docs/en/build-parachains-rococo) mevcuttur. Acala'nın test ağı Mandala şimdi Rococo'da piyasaya sürüldü ve zincirler arası token transferlerini ve diğer işlevleri test ediyor.

### Jeton Transferi

Belirteç transferleri için [Polkadot Cross-Consensus Message Format \(XCM\)](https://github.com/paritytech/xcm-format) uygulamak için "orml-xtokens" oluşturduk.

* xtoken için kaynak kodu [burada](https://github.com/open-web3-stack/open-runtime-module-library/tree/sw/rococo-v1/xtokens).
* Bunun Acala'nın Mandala testnet entegrasyonu [burada](https://github.com/AcalaNetwork/Acala/blob/sw/rococo-v1/runtime/mandala/src/lib.rs)
* Acala Mandala PC2, Rococ'ta [burada](https://polkadot.js.org/apps/?rpc=wss://rococo-rpc.polkadot.io#/parachains) yayındadır.

Denemek ve bizimle birlikte zincirler arası testler yapmak isterseniz lütfen bizimle iletişime geçin!
