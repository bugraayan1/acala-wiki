---
açıklama: Bu sayfa, düğümünüzle bazı temel etkileşimlerde size rehberlik edecektir.
---

# Düğüm Etkileşimi

Bu sayfa, düğümünüzle bazı temel etkileşimlerde size rehberlik edecektir. Her zaman kullandığınız alet için uygun belgelere bakın. Bu kılavuz, sizi uygun araçlara yönlendirmeli,_ kurallı referans olarak görülmemelidir.

* [Substrate RPC API](https://crates.parity.io/sc_rpc_api/index.html)
* [Polkadot JS RPC Belgeleri](https://polkadot.js.org/api/substrate/rpc.html)
* [Substrate API Sidecar](https://github.com/paritytech/substrate-api-sidecar)

### RPC

Substrate Chain istemcisi, RPC bağlantıları için HTTP ve WS uç noktalarını kullanıma sunar. Varsayılan bağlantı noktaları, HTTP için 9933 ve WS için 9944'tür.

Tüm RPC yöntemlerinin bir listesini almak için, düğümün "rpc_methods" adlı bir RPC bitiş noktası vardır.

Örneğin:

```text
$ curl -H "Content-Type: application/json" -d '{"id":1, "jsonrpc":"2.0", "method": "rpc_methods"}' http://localhost:9933/

{"jsonrpc":"2.0","result":{"methods":["account_nextIndex","author_hasKey","author_hasSessionKeys","author_insertKey","author_pendingExtrinsics","author_removeExtrinsic","author_rotateKeys","author_submitAndWatchExtrinsic","author_submitExtrinsic","author_unwatchExtrinsic","chain_getBlock","chain_getBlockHash","chain_getFinalisedHead","chain_getFinalizedHead","chain_getHead","chain_getHeader","chain_getRuntimeVersion","chain_subscribeAllHeads","chain_subscribeFinalisedHeads","chain_subscribeFinalizedHeads","chain_subscribeNewHead","chain_subscribeNewHeads","chain_subscribeRuntimeVersion","chain_unsubscribeAllHeads","chain_unsubscribeFinalisedHeads","chain_unsubscribeFinalizedHeads","chain_unsubscribeNewHead","chain_unsubscribeNewHeads","chain_unsubscribeRuntimeVersion","offchain_localStorageGet","offchain_localStorageSet","payment_queryInfo","state_call","state_callAt","state_getChildKeys","state_getChildStorage","state_getChildStorageHash","state_getChildStorageSize","state_getKeys","state_getKeysPaged","state_getKeysPagedAt","state_getMetadata","state_getPairs","state_getRuntimeVersion","state_getStorage","state_getStorageAt","state_getStorageHash","state_getStorageHashAt","state_getStorageSize","state_getStorageSizeAt","state_queryStorage","state_subscribeRuntimeVersion","state_subscribeStorage","state_unsubscribeRuntimeVersion","state_unsubscribeStorage","subscribe_newHead","system_accountNextIndex","system_addReservedPeer","system_chain","system_health","system_name","system_networkState","system_nodeRoles","system_peers","system_properties","system_removeReservedPeer","system_version","unsubscribe_newHead"],"version":1},"id":1}
```

Çağrıya parametreler ekleyin, örneğin hash değerine göre bir blok alın:

```text
$ curl -H "Content-Type: application/json" -d '{"id":1, "jsonrpc":"2.0", "method": "chain_getBlock", "params":["0x3fa6a530850324391fde50bdf0094bdc17ee17ec84aca389b4047ef54fea0037"]}' http://localhost:9933

{"jsonrpc":"2.0","result":{"block":{"extrinsics":["0x280402000b50055ee97001","0x1004140000"],"header":{"digest":{"logs":["0x06424142453402af000000937fbd0f00000000","0x054241424501011e38401b0aab22f4d72ebc95329c3798445786b92ca1ae69366aacb6e1584851f5fcdfcc0f518df121265c343059c62ab0a34e8e88fda8578810fbe508b6f583"]},"extrinsicsRoot":"0x0e354333c062892e774898e7ff5e23bf1cdd8314755fac15079e25c1a7765f06","number":"0x16c28c","parentHash":"0xe3bf2e8f0e901c292de24d07ebc412d67224ce52a3d1ffae76dc4bd78351e8ac","stateRoot":"0xd582f0dfeb6a7c73c47db735ae82d37fbeb5bada67ee8abcd43479df0f8fc8d8"}},"justification":null},"id":1}
```

Bazı dönüş değerleri ilk bakışta anlamlı görünmeyebilir. Substrat, kaynak kısıtlı yürütme ortamları için uygun bir biçim olarak [SCALE kodlamasını](https://substrate.dev/docs/en/knowledgebase/advanced/codec) kullanır. İnsanların okuyabileceği bilgileri elde etmek için bilgilerin kodunu çözmeniz ve [meta veri](https://substrate.dev/docs/en/knowledgebase/runtime/metadata) \(`state_getMetadata`\) zincirini kullanmanız gerekir.

#### Zincir Başını İzleme

Sonlandırılmış üstbilgilerin karmaları akışına abone olmak için RPC uç noktası "chain_subscribeFinalizedHeads"i veya kesinleştirilmiş üstbilginin en son karmasını almak için "chain_FinalizedHeads"i kullanın. Belirli bir karma ile ilişkili bloğu almak için 'chain_getBlock' kullanın. "chain_getBlock" yalnızca blok karmalarını kabul eder, bu nedenle ara blokları sorgulamanız gerekiyorsa, bir blok numarasından blok karmasını almak için "chain_getBlockHash" kullanın.

### Substrate API Sidecar

Parity, TypeScript'te yazılmış ve sınırlı sayıda uç nokta ortaya çıkaran bir RPC istemcisi tutar. Meta verileri ve kodek mantığını işler, böylece her zaman kodu çözülmüş bilgilerle uğraşırsınız. Ayrıca, bir altyapı işletmesinin muhasebe ve denetim için ihtiyaç duyabileceği bilgileri toplar, ör. işlem ücretleri.

Sepet blokları getirebilir, bir adresin bakiyesini atomik olarak \(yani, karşılık gelen bir blok numarasıyla\), zincirin meta verilerini alabilir, bir işlem ücreti tahmini alabilir ve işlemleri bir düğümün işlem kuyruğuna gönderebilir. Herhangi bir özellik/uç nokta isteğiniz varsa [repoda](https://github.com/paritytech/substrate-api-sidecar) bir sorun kaydedin.

İstemci bir HTTP ana bilgisayarında çalışır. Aşağıdaki örnekler python3'ü kullanır, ancak `http://HOST:PORT/` adresinden istediğiniz şekilde sorgulayabilirsiniz. Varsayılan "http://127.0.0.1:8080"dir.

#### Blok Alma

"block/number" uç noktasını kullanarak bir blok getirin. Zincir ucunu almak için blok numarasını atlayın.

```text
import requests
import json

url = 'http://127.0.0.1:8080/block/2077200'
response = requests.get(url)
if response.ok:
    block_info = json.loads(response.text)
    print(block_info)
```

Bu, tamamen kodu çözülmüş bir blok döndürür. "balances.transfer" dış kısmında, "partialFee" maddesi işlem ücretidir. Toplam ücretin bahşiş alanını içermesi nedeniyle "kısmi ücret" olarak adlandırılır. Bazı dışsal öğelerin imzası olmadığına dikkat edin. Bunlar doğasında var.

> İşlem ücretlerini takip ederken, 'extrinsics.paysFee' değeri dışsalın ücretli olup olmadığını belirlemek için yeterli değildir. Bu alan yalnızca işlem olarak gönderildiğinde ücret talep edeceği anlamına gelir. Bir ücret almak için bir işlemin de imzalanması gerekir. Dolayısıyla, aşağıdaki örnekte, 'timestamp.set' dışsal öğesi, blok yazarı tarafından bloğa yerleştirilen _içsel,_ olduğu için bir ücret ödemez.

```text
{'number': '2077200',
 'hash': '0x00e4e8bd8ec39e54aa26f01f5af7484d771f810fd7f1f4685a204dbc8fbfe80b',
 'parentHash': '0xf4065df1171047819592013770a98fff4b9058a96c4499676b72b1b93f5589e9',
 'stateRoot': '0xf1258925262058ef5d9eaaed49bd878e82584356f42aade40b68cdbd219be46c',
 'extrinsicsRoot': '0xbd4ea887b1a3cb3068db0524b938a0fb13093584b4e6664b3f121448a871cd3d',
 'logs': [{'type': 'PreRuntime',
   'index': '6',
   'value': ['BABE', '0x02b300000087b5c60f00000000']},
  {'type': 'Seal',
   'index': '5',
   'value': ['BABE',
    '0x689eddf91f1551f74de96ab0e2e52f41522bd82920cbe595148f873aa6d0541f48cfbb9b281181f2e52141b1c401dde7259634485fdab02cc7b63febe51ff78a']}],
 'onInitialize': {'events': []},
 'extrinsics': [{'method': 'timestamp.set',
   'signature': None,
   'nonce': '0',
   'args': ['1588085034000'],
   'tip': '0',
   'hash': '0x3cb46207ef8fadf3def3400ae2cb2a09b780431a6daf0b9bde15d91aeaf8faa3',
   'info': {},
   'events': [{'method': 'system.ExtrinsicSuccess',
     'data': [{'weight': '10000000', 'class': 'Mandatory', 'paysFee': True}]}],
   'success': True,
   'paysFee': True},
  {'method': 'finalityTracker.finalHint',
   'signature': None,
   'nonce': '0',
   'args': ['2077197'],
   'tip': '0',
   'hash': '0x2214831b2a13c75288d2267ebd089fffef82ba99d41f6c319ca06e24facc4d51',
   'info': {},
   'events': [{'method': 'system.ExtrinsicSuccess',
     'data': [{'weight': '10000000', 'class': 'Mandatory', 'paysFee': True}]}],
   'success': True,
   'paysFee': True},
  {'method': 'parachains.setHeads',
   'signature': None,
   'nonce': '0',
   'args': [[]],
   'tip': '0',
   'hash': '0xcf52705d1ade64fc0b05859ac28358c0770a217dd76b75e586ae848c56ae810d',
   'info': {},
   'events': [{'method': 'system.ExtrinsicSuccess',
     'data': [{'weight': '1000000000',
       'class': 'Mandatory',
       'paysFee': True}]}],
   'success': True,
   'paysFee': True},
  {'method': 'balances.transfer',
   'signature': {'signature': '0xf4cd36691d6ceb0a913e9d8409bde34e83761829f2fb25db15052de7ba9a6f7c4c54949f884d59005248c2c8b2951575ad0ae8f3c5d866e147a1771f47d91385',
    'signer': 'HUewJvzVuEeyaxH2vx9XiyAPKrpu1Zj5r5Pi9VrGiBVty7q'},
   'nonce': '155',
   'args': ['GoJ89MXptpNt1dH4NaZ73YtzknhrYeZcBJ33mifX5BMqoFz',
    '5000000000000'],
   'tip': '0',
   'hash': '0xc7b57537e2e63f866083ea22265cb65c846528d76378a3b3490eeada97f83d1d',
   'info': {'weight': '200000000', 'class': 'Normal', 'partialFee': '10000000000'},
   'events': [{'method': 'system.NewAccount',
     'data': ['GoJ89MXptpNt1dH4NaZ73YtzknhrYeZcBJ33mifX5BMqoFz']},
    {'method': 'balances.Endowed',
     'data': ['GoJ89MXptpNt1dH4NaZ73YtzknhrYeZcBJ33mifX5BMqoFz',
      '5000000000000']},
    {'method': 'balances.Transfer',
     'data': ['HUewJvzVuEeyaxH2vx9XiyAPKrpu1Zj5r5Pi9VrGiBVty7q',
      'GoJ89MXptpNt1dH4NaZ73YtzknhrYeZcBJ33mifX5BMqoFz',
      '5000000000000']},
    {'method': 'treasury.Deposit', 'data': ['8000000000']},
    {'method': 'balances.Deposit',
     'data': ['E58yuhUAwWzhn2V4thF3VciAJU75eePPipMhxWZe9JKVVfq',
      '2000000000']},
    {'method': 'system.ExtrinsicSuccess',
     'data': [{'weight': '200000000', 'class': 'Normal', 'paysFee': True}]}],
   'success': True,
   'paysFee': True}],
 'onFinalize': {'events': []}}
```

> JS sayı türü, 53 bitlik bir hassas kayan noktadır. Yanıttaki sayısal değerlerin sayısal bir türe sahip olacağının garantisi yoktur. "2**53-1"den büyük tüm sayıların bir dize türü olacaktır.

#### İşlem Gönderme

Bir HTTP POST isteğiyle "tx" uç noktasını kullanarak serileştirilmiş bir işlem gönderin.

```text
import requests
import json

url = 'http://127.0.0.1:8080/tx/'
tx_headers = {'Content-type' : 'application/json', 'Accept' : 'text/plain'}
response = requests.post(
    url,
    data='{"tx": "0xed0...000"}', # A serialized tx.
    headers=tx_headers
)
tx_response = json.loads(response.text)
```

Başarılı olursa, bu uç nokta, işlem karması ile bir JSON döndürür. Hata durumunda, bir hata raporu döndürür, örneğin:

```text
{
    "error": "Failed to parse a tx" | "Failed to submit a tx",
    "cause": "Upstream error description"
}
```

