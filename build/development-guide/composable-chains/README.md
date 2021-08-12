# Birleştirilebilir Zincirler

Şu anda, zincirler arası mesaj geçişi ve parachainler yalnızca Polkadot'un test ağında [Rokoko](https://wiki.polkadot.network/docs/en/build-parachains-rococo) mevcuttur. Acala'nın test ağı \(Mandala\) şimdilik Rococo'da başlatıldı ve zincirler arası takas edilebilir token transferlerini ve diğer işlevleri test ediyor.

Acala ile \#Composable olmak için lütfen [Discord teknik sohbetimizde](https://discord.gg/Xb3CxcjCVc) bizimle lütfen iletişime geçin!

## Acala ile Birleştirilebilir

* Acala Mandala PC2, Rokoko'da yayındadır, [buradan ulaşabilirsiniz.](https://polkadot.js.org/apps/?rpc=wss://rococo-rpc.polkadot.io#/parachains).
* Xtokens belgelerine [buradan] bakabilirsiniz.(https://github.com/open-web3-stack/open-runtime-module-library/wiki/xtokens)

### Altyapı

[Polkadot Cross-Consensus Message Format \(XCM\)](https://github.com/paritytech/xcm-format) değiştirilebilir jetonlar gibi kullanım senaryolarını belirtmeyen genel bir mesaj formatıdır. Bu nedenle, gerekli kullanım örneğinin bir uygulamasını sağlamamız gerekiyor; bu zincirler arası transfer, parazincirlerin aynı bağlamla birlikte çalışabilir olması, yani parazincirler arasında ve aktarma zinciri ile parazincirler arasında değiştirilebilir varlıkları gönderme/alma gibi düşünülebilir.Röle Zinciri varlıkları \(DOT veya KSM\ gibi) ve yerel parachain varlıkları \(Acala için ACA\ gibi) için aynı arayüzü ve entegrasyonu kolaylaştıran uygulama ayrıntılarından soyutlamayı istiyoruz.

[XCM Fungible Asset Uygulama Kılavuzu](https://github.com/open-web3-stack/open-runtime-module-library/discussions/385), zincirler arası değiştirilebilir varlık tasarımı hususlarını ve tartışmalarını da ortaya koymuştur, bununla birlikte Acala ve diğerlerinin şu anda benimsediği ve test ettiği bir referans uygulama orml-xtokens olarak düşünülebilir.

`orml-xtokens`, değiştirilebilir belirteçler için XCM'nin bir referans uygulamasıdır. xtokens için kaynak kodu [burada](https://github.com/open-web3-stack/open-runtime-module-library/tree/master/xtokens) ve xcm-support [burada](https:/ /github.com/open-web3-stack/open-runtime-module-library/tree/master/xcm-support).

Şu anda, "xtokens" kod tabanı Acala tarafından geliştirilmektedir, desteğe ihtiyacınız olursa lütfen [Discord teknik sohbetinde](https://discord.gg/Xb3CxcjCVc) bize ulaşın.


## Entegrasyon Kılavuzu

Yerel bir parachain test ağı ortamı kurmak için @bertstachios'un [bu kılavuzu](https://hackmd.io/dhmCATb_QqygCPxkxaDcmA) izleyin.

### Adım 0 Yerel Parachain Testnet

Yerel bir parachain test ağı ortamı oluşturmak için @bertstachios'un [bu kılavuzunu](https://hackmd.io/dhmCATb_QqygCPxkxaDcmA) izleyin.

### Adım 1 Acala Jetonlarını Destekleyin

Acala'nın zincirinde verilen USD, ACA, renBTC, LDOT vb. jetonları almak için ve ayrıca, para birimi kimliği dönüşümünü uygulamak için para birimi türünüze dahil etmeniz gerekir;

Acala'da para birimi kimliği dönüşümü için örnek bir uygulamaya [buradan](https://github.com/AcalaNetwork/Acala/blob/master/runtime/acala/src/lib.rs#L1307) bakabilirsiniz.

### 2. Adım Simgenizi Acala'da kullanılabilir hale getirin

Spam belirteçlerinden kaçınmak için Acala'da yeni belirteçleri tanıtmak için bir onboarding prosedürü vardır. Test amaçlıysa, bu adımı her zaman atlayabilirsiniz ve 'orml-unkown-tokens' alınan tüm yabancı belirteçleri işleyecektir.

### 3. Adım "xtokens" modülünü entegre edin

"xtokens" modülü, XCM mesajlarını kullanarak zincirler arası varlık aktarımı için bir arayüz sağlar.

[Token transferleri için XCM](https://github.com/open-web3-stack/open-runtime-module-library/tree/master/xtokens) ve [XCM-support](https) uygulamasına göz atın ://github.com/open-web3-stack/open-runtime-module-library/tree/master/xcm-support).

Daha fazla ayrıntı için [`xtokens` modül entegrasyonu örneğini](https://github.com/AcalaNetwork/Acala/blob/3c5da19e6031df91184106057fdcf73ba8784a29/runtime/mandala/src/lib.rs#L1517-L1658) inceleyebilirsiniz.

> Not: referans uygulaması hiçbir şekilde kesin değildir, bunun yerine parachain topluluğunun denemesi ve yinelemesi için başlangıç noktasıdır. Lütfen [`xtokens`](https://github.com/open-web3-stack/open-runtime-module-library/tree/master/xtokens) veya [uygulama kılavuzuna](https://github.com/com/open-web3-stack/open-runtime-module-library/discussions/385) geri bildirim sağlayın.
### 4. Adım HRMP Kanalını Açın

Zinciriniz zaten bir parachain olarak Rokoko'ya bağlı olacaktır. XCMP \(Cross-chain Message Passing\) hala uygulanıyorken - bu, Röle zincirinden geçmeden zincirler arası mesajları doğrudan birbirine göndermektir, bir stop-gap protokolü HRMP \(Horizontal Relay-routed Message Passing\) yerindedir.

> HRMP, XCMP ile aynı arayüze ve işlevselliğe sahiptir, ancak tüm mesajları Relay Chain depolamasında depoladığı için kaynaklar üzerinde çok daha talepkardır. XCMP uygulandığında, HRMP'nin kullanımdan kaldırılması ve onun lehine aşamalı olarak kaldırılması planlanmaktadır.

Çapraz zincir mesajları göndermek ve almak için iki para zincirinin her iki tarafta da HRMP kanalını açması gerekecektir. [HRMP Kanalını açmak için buradaki talimatları](open-hrmp-channel.md) uygulayabilirsiniz.

## \#Birleştirilebilir

Polkadot/Kusama'daki tüm zincirler, değer alışverişinden durum değiştirmeye kadar birbirleriyle _**birleştirilebilir**_ olacaktır. Örneğin, zincirler sadece değerleri güvenle aktaramazlar, birbirlerinin palet/akıllı sözleşme fonksiyonlarını da çağırabilirler örn. PolkaBTC'yi Interlay zincirinde basmak, PolkaBTC'yi Acala'ya aktarmak ve hepsini tek bir işlemde USD karşılığında teminat altına almak.

Acala aşağıdaki \(potansiyel\) parachains ile birleştirilebilir olacaktır. 'xtokens' varsa veya uyguluyorsanız, lütfen kendinizi eklemek için bu Repo'ya PR yapın:

* Plasm
* Interlay
* Phala
* Laminar
* Moonbeam
* Centrifuge
* HydraDX
* Darwinia
* Kilt
* Crust
* Snowfork
* Bit.Country
* ...

Denemek, desteğe ihtiyaç duymak ve/veya bizimle birlikte zincirler arası testler yapmak istiyorsanız bizimle iletişime geçmekten çekinmeyin!
