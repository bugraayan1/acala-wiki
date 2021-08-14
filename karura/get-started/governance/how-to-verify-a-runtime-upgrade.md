# Çalışma Zamanı Yükseltmesi Nasıl Doğrulanır

Bu kılavuz, örnek olarak çalışma zamanı yükseltme sürümü 1.1.3'ü kullanır.

Yükseltme önerildiğinde, [Polkadot App - Karura parachain - Democracy bölümünde](https://polkadot.js.org/apps/?rpc=wss%3A%2F%2Fkarura-rpc-2) göreceksiniz. aca-api.network%2Fws#/democracy).

![](../../../.gitbook/assets/screen-shot-2021-07-14-at-10.22.16-pm.png)

## Ön Görüntü Bilgisini Yükselt

Teklifi genişletin ve Ön Görüntü bilgilerini bulun.

* Ön görüntü: `parachainSystem.authorizeUpgrade(0xd9660e7d73163f7b2e1591c08c60e68f4b47cb85dcba54d55c53b9573876f55e)`
* Karma: `0x4f8bf2c02c5a1e8cdcf7a94dabf2805c563c46a87876c684c5d79ffb745db115'

## Kodla doğrulama

Teklifin tartışma gönderisinde, yayın etiketini, çalışma zamanı WASM dosyasını ve diğerlerinin bunu önerilen ön görüntüye göre doğrulaması için gerekli diğer bilgileri sağlayacaktır.

* Yayın sayfası: [https://github.com/AcalaNetwork/Acala/releases/tag/1.1.3](https://github.com/AcalaNetwork/Acala/releases/tag/1.1.3)
* Çalışma Zamanı Wasm: [https://gateway.pinata.cloud/ipfs/QmTrUJragkgGrp3eNyun7n7p5zT8MFLE3s87o3ZJSyj4wf](https://gateway.pinata.cloud/ipfs/QmTrUJragkgGrp3eNyun7n7p5sySwf)

### Doğrulamak için aşağıdaki adımı uygulayın

#### 1. Sürüm için kendi Wasm Runtime'ınızı oluşturun

* srtool wasm oluşturmak için kullanılır
  * srtool hakkında daha fazlası:
    * [https://www.chevdor.com/post/2019/12/06/srtool/](https://www.chevdor.com/post/2019/12/06/srtool/)
    * [https://github.com/paritytech/srtool](https://github.com/paritytech/srtool)
* inşa etmek için bu adımları izleyin
  * Docker'ı yükleyin
    * [https://docs.docker.com/get-docker/](https://docs.docker.com/get-docker/)
  * Klon Acala deposu
    * `git klonu https://github.com/AcalaNetwork/Acala.git`
  * Ödeme sürümü şubesi
    * `git checkout yayın-karura-1.1.3`
  * srtool ile oluşturun
    * `srtool-build-wasm-karur yap`
  * Derlemenin tamamlanmasını bekleyin ve wasm'iniz oluşturuldu

#### 2. Karma oluştur ve karşılaştır

'Geliştirici - Dışsal Bilgiler' sekmesinde, aşağıdakini kullanın ve çağrı karmasını oluşturmak için wasm'yi yükleyin. Bunu önerilen preimage hash ile karşılaştırın.

![](../../../.gitbook/assets/image%20%2826%29.png)
