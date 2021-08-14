# Birleştirilebilir DeFi Yığını

### **EVM ve Runtime'da Tamamen Oluşturulabilir DeFi Temel Öğeleri**

Acala EVM'de dağıtılan Akıllı Sözleşme Dapp'leri, DOT, ACA, aUSD, renBTC vb. gibi yerel ve zincirler arası varlıkları doğrudan kullanabilir. EVM'de dağıtılan ERC-20 jetonları, DeX'te listelenmek üzere çalışma zamanı düzeyinde de kullanılabilir hale getirilebilir. veya \(yönetim onayı ile\) ücret belirteçleri olarak kullanılacak. Örneğin Ampleforth, yerel bir belirteç olarak sunulacak olan Acala EVM'de AMPL sözleşmelerini dağıtacak, böylece işlem ücretlerini ödemek için kullanılabilir ve doğrudan DeX'imizde listelenebilir.

Akıllı Sözleşme Dapp'leri, ödünç verme, özel amaçlı DeX, finansal gibi çeşitli ilginç DeFi uygulamalarını oluşturmak için Acala DeFi ilkellerini \(DeX, stablecoin kredisi ve sıvı staking\), köprüleri, oracle altyapısını, yerel ve zincirler arası likiditeyi doğrudan kullanabilir. esnetmeye dayalı ürünler ve daha fazlası.

Süreç, kullanıcılar ve geliştiriciler için sorunsuzdur, ancak sahne arkasında yerel belirteçler ve protokoller \(diğer adıyla çalışma zamanı modülleri\) önceden derlenmiş sözleşmeler biçiminde EVM'de sağlanır. EVM'de bir akıllı sözleşme tarafından başlatılan bir işlem, bir Substrat işlemine dönüştürülür ve polkadot.js kullanılarak herhangi bir Polkadot uzantısı tarafından imzalanır. Yanıt SDK \([bodhi.js](https://github.com/AcalaNetwork/bodhi.js)\) tarafından işlenecek ve Ethereum uyumlu bir biçime dönüştürülecektir.

### Kullanılabilir Birleştirilebilir Sözleşmeler

Bu önceden derlenmiş sözleşmeler artık Acala EVM'nin kullanımına sunulmuştur.

* **ERC20'de bulunan yerel ve zincirler arası tokenler**: DOT, ACA, aUSD, XBTC, LDOT, RENBTC. [Buradan](https://wiki.acala.network/build/development-guide/smart-contracts/advanced/use-native-tokens) deneyin.
* Fiyat beslemesi almak için Oracle sözleşmesi: Bu, garantili Hizmet Kalitesi gibi [Open Oracle Gateway](https://wiki.acala.network/learn/basics/oracle) işlevlerini ortaya çıkarır. [Buradan](https://wiki.acala.network/build/development-guide/smart-contracts/advanced/use-oracle-feeds) deneyin.
* Abonelikler ve yinelenen ödemeler gibi kullanım örneklerine olanak tanıyan zincir üstü otomatik zamanlayıcı. [Buradan](https://wiki.acala.network/build/development-guide/smart-contracts/advanced/use-on-) deneyin zincir zamanlayıcı).
* Dolandırıcılığı ve zincir üzerindeki kaynakların israfını önlemek için devlet kiralama gibi gelişmiş sözleşme dağıtım özellikleri.
* Daha fazlası: Acala EVM'ye kademeli olarak daha fazla yerel işlevsellik sunuyoruz, sıradaki DeFi ilkelleri \(DeX, stabilcoin kredisi ve sıvı staking\).

Bu sözleşmeler hakkında daha fazla bilgi edinin [buradan](https://github.com/AcalaNetwork/predeploy-contracts#predeployed-system-contract).
