# Acala Hesabı

### Acala Hesabı

Acala, Substrat tabanlı bir blok zinciridir ve Substrat tabanlı hesapları kullanır. Kullanıcılar bir hesap aka kullanabilir. birden çok Substrat tabanlı zincirde bir özel-genel anahtar çifti. Esasen bir özel-genel anahtar çifti \(bir hesap\) için farklı blok zincirleri için farklı bir adres gösterimi vardır.

* Genel Substrat adresleri 5 ile başlar. Polkadot{js} uzantısındaki adresler
* Adres gösteriminizi farklı blok zincirinde kontrol edebilirsiniz [buradan](https://acala-testnet.subscan.io/tools/ss58_transform)

Substrat tabanlı zincirlerde kullanılan adres formatı SS58'dir. SS58, bazı küçük değişikliklerle Bitcoin'den Base-58-check'in bir modifikasyonudur. Substrat adres formatı hakkında daha fazla bilgi edinin [buradan](https://wiki.polkadot.network/docs/en/learn-accounts).

Kılavuzu [buradaki](https://wiki.acala.network/learn/get-started#create-a-polkadot-account) veya [buradaki](https://wiki.polkadot.network/docs/en/) izleyin Öğren-hesap-oluşturma) bir Substrate hesabı oluşturmak için.

### EVM Hesabı

Ethereum, Substrate'dan farklı bir adres formatına sahiptir. EVM'de dağıtılan akıllı sözleşme DApp'lerini kullanırken, kullanıcıların normalde işlem yapmak için bir Ethereum adresi kullanmaları gerekir. Acala EVM'de, kullanıcıların Substrate hesaplarını bir kez bir EVM adresi ile bağlamalarını, ardından Substrate hesabını kullanarak Acala'da herhangi bir işlem imzalamalarını sağlayan Tek Hesap özelliğimiz bulunmaktadır.

Daha fazlasını [buradan](https://wiki.acala.network/learn/basics/acala-evm/acala-evm-composable-defi-stack/single-account) okuyun.
