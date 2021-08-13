# EVM Hesabı Kur

## **Tek Cüzdan, Tek Hesap Deneyimi**

Kullanıcılar, Substrate çalışma zamanı, EVM'deki sözleşmeler ve wasm sözleşmeleri veya bunların bir karışımı ile etkileşim kurmak için **tek bir uzantı/cüzdan** ve **tek bir Substrat hesabı** kullanabilir. Bir kullanıcı belirli bir Ethereum adresini kullanmak isterse, bunu Substrate adresiyle \(temelde kullanıcının her iki adresin de sahibi olduğunu kanıtlayarak\) bağlamanız yeterlidir, bundan sonra kullanıcı Substrate hesabını [Polkadot{js} uzantılı] kullanabilir (https://wiki.polkadot.network/docs/en/learn-account-generation) veya benzeri herhangi bir Ethereum işlemini sorunsuz bir şekilde imzalamak için.

Bu, kullanıcıların birden fazla hesabı veya cüzdanı yönetmeden Acala ve çapraz zincir yetenekleri içindeki tüm işlevleri kullanmalarına olanak tanır.

## EVM Hesabının Kurulumu

Acala'daki bir kullanıcının her zaman, kullanıcıların birden fazla blok zincirinde kolayca gezinmesini ve herhangi bir \(EVM ve Susbtrate\) işlemini tek bir hesapla imzalamasını sağlayan Substrate tabanlı bir hesabı olacaktır. Acala Substrate Hesabı hakkında daha fazla bilgiye [buradan] (https://wiki.acala.network/learn/basics/acala-account) ulaşabilirsiniz. Bir Substrate hesabı oluşturmak için [buradaki](https://wiki.acala.network/learn/get-started#create-a-polkadot-account) kılavuzu veya [buradaki](https://wiki.polkadot.network/docs/en/) dokümanlara göz atabilirsiniz.  

Tek Hesabı ve Acala EVM'yi kullanmak için

1. Otomatik olarak bir Ethereum adresi VEYA
2. Mevcut bir Ethereum için Substrate eski statüsündedir.

### **1. Otomatik oluşturulan bir EVM Hesabını**

Bir kullanıcı, onun Substrate hesabı için bir EVM adresi süsleme. Kullanıcı daha sonra EVM adresi Alt tabakayı bağlayabilir, yöresel belirteçlerin bakiyeleri ör. Substrat hesabındaki DOT, renBTC, aUSD vb. EVM'de kullanım hazır hale gelir.

Acala, EVM adresiyle ilişkili bir EVM adresi'nde bir EVM adresi olmayana, otomatik olarak bir EVM adresiul ve Substrate oluşturVM ile bağlanacaktır.

Bakiyeler, Substrate hesabı ve ilişkili EVM adresi arasında otomatik olarak senkronize edilir. Örneğin bir kullanıcı 10 renBTC'nin ışınımları Acala'ya ışıklar, bakiyesi hesabında gösterilir, bakiyesi de EVM üzerinden gösterilebilir ve aktarılabilir.

#### EVM Adres oluşturma

EVM Adresi, "evvm" öneki ve giriş olarak ilişkili alt hesaplayla "blade ödemeden2_256" karma ödemeden. Kaynak koduna [buradan] bakabilirsiniz. (https://github.com/AcalaNetwork/Acala/blob/master/modules/evm-accounts/src/lib.rs#L185-L186).

```text
blake2_256(“evm:” ++ account_id)[0..20]
```

#### EVM Playground aracılığıyla bir EVM Adresi Oluşturun

[EVM Playground](https://evm.acala.network/#/evmAccount) \(çeşitli Acala EVM işlevlerini test etmek için bir web uygulaması\) öğesine gidin.

Henüz üzerinde değilseniz, `Setup EVM Account` sekmesine gidin.

![](../../../../.gitbook/assets/screen-shot-2021-02-03-at-10.52.25-am.png)

**Adım 1: Bir Substrat Hesabı Seçin**

Polkadot{js} uzantısını henüz yüklediyseniz ve bir hesap oluşturduysanız, lütfen [buradaki](https://wiki.polkadot.network/docs/en/learn-account-generation#polkadotjs-browser) adımları uygulayarak bunu yapın. -Eklenti).

Hesap oluşturulduysa ve uzantı doğru şekilde yüklendiyse, hesap açılır menüde mevcut olmalıdır.

Hesapları bağlamak için daha sonra Acala blok zincirine bir işlem göndermesi gerekeceğinden, hesaba para yatırmak için `Musluk` Düğmesine tıklayın.

![](../../../../.gitbook/assets/screen-shot-2021-02-03-at-10.53.47-am.png)

**Adım 2: Otomatik olarak oluşturulmuş bir EVM adresini Bağlamak için Seçenek 1'i seçin**

**Adım 3: Bağlayın**

Oluşturulan EVM adresini 3. Adımda görebilir ve `Bağla` butonuna tıklayabilirsiniz.

Polkadot{js} uzantısı sizden bir şifre girmenizi veya kayıtlı şifreyi kullanmanızı isteyecek ve `İşlemi imzala` Düğmesine tıklayın.

![](../../../../.gitbook/assets/screen-shot-2021-02-03-at-10.54.49-am.png)

`Bind` işlemi başarılı olduysa, `Bu hesabı bağlamak için bir evm hesabı zaten var` mesajını alırsınız, temelde bağlama zincir üzerinde kaydedilmiştir ve herhangi bir EVM işlemi için Polkadot uzantısını kullanabilirsiniz.

![](../../../../.gitbook/assets/screen-shot-2021-02-03-at-5.01.33-pm.png)

### **2. Mevcut Bir Ethereum Hesabını Bağlayın**

Her durumda, kullanıcılar Acala EVM'de mevcut bir Ethereum hesabını kullanmak isterse, bu adresin talep edilmesi ve Subatrate hesabına bağlanması gerekecektir.

_**Bir Substrate hesabı yalnızca bir Ethereum adresiyle ilişkilendirilebilir.**_ Önceden oluşturulmuş bir EVM adresine bağlı bir Substrate adresi artık mevcut bir Ethereum adresine bağlanamaz ve bunun tersi de geçerlidir.

Mevcut bir Ethereum hesabını bağlamak, kullanıcıların bir mesajı imzalayarak Ethereum hesabı özel anahtarına sahip olduklarını kanıtlamalarını, bunu bir "talep" işlemine dahil etmelerini ve Acala ağına göndermelerini gerektirir.

Bu özellik, bir sonraki sürümde yakında geliyor.

#### Kullanım Örnekleri

Aşağıda, mevcut bir Ethereum adresini bağlamanın iki olası kullanım durumu bulunmaktadır.

** Durum 1'i kullanın**

Örneğin, Ethereum üzerindeki bir DeFi protokolü, sözleşmelerini Acala ağına dağıtarak operasyonunu Polkadot'a genişletiyor. Acala'daki protokolleri de kullanıyorlarsa, bu yeni şubeyi mevcut kullanıcılarına jetonlar bırakarak yapacaklar.

En kolay yol, jetonları Acala'daki mevcut Ethereum adreslerine hava yoluyla bırakmaktır. Bu nedenle kullanıcılar, mevcut Ethereum adreslerini bir Substrate adresine bağlayacak, herhangi bir EVM işlemi için kullanacak ve airdrop alacaklardır.

** Durum 2'yi kullanın**

[Linkdrop](https://linkdrop.io/) gibi DApp'ler için, kullanıcıların Ethereum özel anahtarını kullanarak mesajları imzalamaları gerekir. Acala'da Linkdrop kullanmak, kullanıcıların mevcut Ethereum adreslerini talep etmelerini ve bunu Substrate hesaplarına bağlamalarını gerektirir. Daha sonra Ethereum hesabı adına işlem gönderebilirler.
