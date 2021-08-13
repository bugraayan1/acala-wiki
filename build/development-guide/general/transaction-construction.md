---
description: >-
  This page will discuss the transaction format in Acala and how to create,
  sign, and broadcast transactions.
---

# Transaction Yapısı

Bu sayfada Polkadot'taki işlem formatı ve işlemlerin nasıl oluşturulacağı, imzalanacağı ve yayınlanacağı açıklanacaktır. Bu kılavuzdaki diğer sayfalar gibi, bu sayfada da mevcut araçlardan bazıları gösterilmektedir. **Entegrasyon yaparken her zaman her aracın belgelerine bakın.**

### Transaction Formatı

Polkadot, tüm işlemlerde ortak olan bazı temel işlem bilgilerine sahiptir.

* Adres: Gönderen hesabın SS58 kodlu adresi.
* Blok Hash: Kontrol noktası bloğunun hash'i.
* Blok Numarası: Kontrol noktası bloğunun numarası.
* Genesis Hash: Zincirin genesis hash'i.
* Meta veriler: Gönderildiğinde çalışma zamanı için SCALE kodlu meta veriler.
* Nonce: Bu işlem için nonce.\*
* Özel Sürüm: Çalışma zamanı için geçerli özel sürüm.
* İşlem Sürümü: İşlem biçimi için geçerli sürüm.
* İpucu: İsteğe bağlı, işlem önceliğini artırmak için ipucu.
* Dönem Dönemi: İsteğe bağlı, bir işlemin geçerli olduğu kontrol noktasından sonraki blok sayısı. Sıfır ise, işlem ölümsüzdür.

\*Sistem modülünden sorgulanan nonce, bekleyen işlemleri hesaba katmaz. Aynı anda birden fazla geçerli işlem göndermek istiyorsanız nonce'yi manuel olarak izlemeli ve artırmalısınız.

Her işlemin eklenecek kendi \(veya no\) parametreleri olacaktır. Örneğin, Bakiye paletindeki 'transferKeepAlive' işlevi,:

* `dest`: Destination address
* `#[compact] value`: Number of tokens \(compact encoding\)

Gerekli tüm bilgilere sahip olduğunuzda, yapmanız gerekenler:

1. İmzasız bir işlem oluşturun.
2. Bir imzalama yükü oluşturun.
3. Yükü imzalayın.
4. İmzalı yükü bir işleme seri hale getirin.
5. Serileştirilmiş işlemi gönderin.

Parity, bu adımları gerçekleştirmenize yardımcı olacak aşağıdaki araçları sağlar.

### Acala JS

\[TODO\]

### Tx Wrapper

İmza işlemleri için CLI'yi kullanmak istemiyorsanız, Parity, işlemleri çevrimdışı oluşturmak ve imzalamak için [TxWrapper](https://github.com/paritytech/txwrapper) adlı bir SDK sağlar. Kılavuz için [örneklere](https://github.com/paritytech/txwrapper/tree/master/examples) bakın.

**Özel anahtarı içe aktarın**

```text
import { importPrivateKey } from '@substrate/txwrapper';

const keypair = importPrivateKey(“pulp gaze fuel ... mercy inherit equal”);
```

**Bir ortak anahtardan bir adres türetme**

```text
import { deriveAddress } from '@substrate/txwrapper';

// Public key, can be either hex string, or Uint8Array
const publicKey = “0x2ca17d26ca376087dc30ed52deb74bf0f64aca96fe78b05ec3e720a72adb1235”;
const address = deriveAddress(publicKey);
```

**Çevrimdışı bir işlem oluşturun**

```text
import { methods } from "@substrate/txwrapper";

const unsigned = methods.balances.transferKeepAlive(
  {
    dest: "15vrtLsCQFG3qRYUcaEeeEih4JwepocNJHkpsrqojqnZPc2y",
    value: 500000000000,
  },
  {
    address: "121X5bEgTZcGQx5NZjwuTjqqKoiG8B2wEAvrUFjuw24ZGZf2",
    blockHash: "0x1fc7493f3c1e9ac758a183839906475f8363aafb1b1d3e910fe16fab4ae1b582",
    blockNumber: 4302222,
    genesisHash: "0xe3777fa922cafbff200cadeaea1a76bd7898ad5b89f7848999058b50e715f636",
    metadataRpc, // must import from client RPC call state_getMetadata
    nonce: 2,
    specVersion: 1019,
    tip: 0,
    eraPeriod: 64, // number of blocks from checkpoint that transaction is valid
    transactionVersion: 1,
  },
  {
    metadataRpc,
    registry, // Type registry
  }
);
```

**Bir imzalama yükü oluşturun**

```text
import { methods, createSigningPayload } from '@substrate/txwrapper';

// See "Construct a transaction offline" for "{...}"
const unsigned = methods.balances.transferKeepAlive({...}, {...}, {...});
const signingPayload = createSigningPayload(unsigned, { registry });
```

**İmzalı bir işlemi seri hale getirin**

```text
import { createSignedTx } from "@substrate/txwrapper";

// Example code, replace `signWithAlice` with actual remote signer.
// An example is given here:
// https://github.com/paritytech/txwrapper/blob/630c38d/examples/index.ts#L50-L68
const signature = await signWithAlice(signingPayload);
const signedTx = createSignedTx(unsigned, signature, { metadataRpc, registry });
```

**Yük türlerinin kodunu çözün**

Göndermeden önce içeriklerini doğrulamak için yüklerin kodunu çözmek isteyebilirsiniz.

```text
import { decode } from "@substrate/txwrapper";

// Decode an unsigned tx
const txInfo = decode(unsigned, { metadataRpc, registry });

// Decode a signing payload
const txInfo = decode(signingPayload, { metadataRpc, registry });

// Decode a signed tx
const txInfo = decode(signedTx, { metadataRpc, registry });
```

**Bir işlemin karmasını kontrol edin**

```text
import { getTxHash } from ‘@substrate/txwrapper’;
const txHash = getTxHash(signedTx);
```
### İmzalı Bir Yük Gönderme

İmzalı bir yükü göndermenin birkaç yolu vardır:

1. İmzalayan CLI \(`yarn çalıştırma: imzalayan gönder --tx <signed-transaction> --ws <endpoint>`\)
2. [Substrate API Sidecar](https://wiki.polkadot.network/docs/en/build-node-interaction#substrate-api-sidecar)
3. "author_submitExtrinsic" veya "author_submitAndWatchExtrinsic" ile [RPC](https://wiki.polkadot.network/docs/en/build-node-interaction#polkadot-rpc) bir işlem olarak bildirilir ve onaylanır ve zincire dahil edilir.

### Notlar

Örneklerde kullanılacak bazı adresler. [Alt anahtar belgeleri](https://substrate.dev/docs/en/knowledgebase/integrate/subkey) konusuna bakın.

```text
$ subkey --network polkadot generate
Secret phrase `pulp gaze fuel ... mercy inherit equal` is account:
  Secret seed:      0x57450b3e09ba4598 ... ... ... ... ... ... ... .. 219756eeba80bb16
  Public key (hex): 0x2ca17d26ca376087dc30ed52deb74bf0f64aca96fe78b05ec3e720a72adb1235
  Account ID:       0x2ca17d26ca376087dc30ed52deb74bf0f64aca96fe78b05ec3e720a72adb1235
  SS58 Address:     121X5bEgTZcGQx5NZjwuTjqqKoiG8B2wEAvrUFjuw24ZGZf2

$ subkey --network polkadot generate
Secret phrase `exercise auction soft ... obey control easily` is account:
  Secret seed:      0x5f4bbb9fbb69261a ... ... ... ... ... ... ... .. 4691ed7d1130fbbd
  Public key (hex): 0xda04de6cd781c98acf0693dfb97c11011938ad22fcc476ed0089ac5aec3fe243
  Account ID:       0xda04de6cd781c98acf0693dfb97c11011938ad22fcc476ed0089ac5aec3fe243
  SS58 Address:     15vrtLsCQFG3qRYUcaEeeEih4JwepocNJHkpsrqojqnZPc2y
```

