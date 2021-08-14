# Tam Düğüm

## Özel Gereksinim

Kusama tam düğüm gereksinimleriyle aynı.

## Kaynak Kodundan Çalıştır

* Depoyu klonlayın: [https://github.com/AcalaNetwork/Acala](https://github.com/AcalaNetwork/Acala)
* Ödeme etiketi burada: [https://github.com/AcalaNetwork/Acala/tags](https://github.com/AcalaNetwork/Acala/tags)
* Bağımlılıkları yükleyin
* Karura'nın Derlenmesi: `cargo build --release --features with-karura-runtime`
* Çalıştırma `./target/release acala --chain=karura`

## Docker Yükleme

* Image: `acala/karura-node:latest` or `acala/karura-node:[version number]`
* `docker run acala/karura-node:latest --chain=karura`

## Ortak CLI

* CLI, çoğunlukla Polkadot ve Kusama gibi herhangi bir Substrat tabanlı zincirle aynıdır.
* Çalışan iki düğüm hizmeti olduğundan, CLI'yi bölmek için `--' kullanılır. "--"den önceki argümanlar parachain tam düğüm hizmetine iletilir ve "--"den sonraki argümanlar Relay Chain tam düğüm hizmetine iletilir.
  * Örneğin; `--chain=parachain.json --ws-port=9944 -- --chain=relaychain.json --ws-port=9945` anlamı
* Parachain hizmeti, zincir özelliği olarak 'parachian.json'u kullanıyor ve web soketi RPC bağlantı noktası 9944'tür
     * Relay Chain hizmeti, zincir özelliği ve web soketi olarak "relaychain.json"u kullanıyor

       RPC bağlantı noktası 9945
* Karışıklığı önlemek için her iki hizmet için de bağlantı noktalarını açıkça belirtmeniz önerilir.
  * Örneğin `--listen-addr=/ip4/0.0.0.0/tcp/30333 --listen-addr=/ip4/0.0.0.0/tcp/30334/ws -- --listen-addr=/ip4/0.0.0.0/tcp/30335 --listen-addr=/ip4/0.0.0.0/tcp/30336/ws`

## Örnek CLI

### Arşiv PRC Düğümü

```text
--base-path=/acala/data
--chain=karura
--name=rpc-1
--pruning=archive
--ws-external
--rpc-external
--rpc-cors=all
--ws-port=9944
--rpc-port=9933
--ws-max-connections=2000
--
--chain=kusama
```

