Solidity sözleşmelerini geliştirmek ve derlemek için kullanabileceğiniz birden fazla araç var, burada iki tanesini seçenek olarak sunacağız.

* Çevrimiçi web uygulaması Remix
* Solidity geliştirme ve test çerçevesi Waffle

### Waffle Yorumunu Kullanarak Solidity Sözleşmesini Derleyin

**Not:** Akıllı sözleşmeyi Remix ile derlediyseniz bu bölümü atlayabilirsiniz.

Bu kılavuz, [Waffle](https://github.com/EthWorks/Waffle) kullanarak Solidity tabanlı bir akıllı sözleşmeyi Acala'ya dağıtma sürecini anlatmaktadır. Waffle, Ethereum için en yaygın kullanılan akıllı sözleşme geliştirme çerçevelerinden biridir.

### **1. Ön Koşulları Kontrol Edin**

Öncelikle Node.js \(bu örnekte v15.x kullanıyoruz\) ve npm paket yöneticisini kurmamız gerekiyor. Kurulum için işletim sisteminizin resmi belgelerindeki kılavuzları takip edin: [NodeJS'yi kurun](https://nodejs.org/en/download/package-manager/)

Her paketin sürümünü sorgulayarak her şeyin doğru şekilde kurulduğunu doğrulayabiliriz:

```text
node -v
```

```text
npm -v
```

Yarn paketi yöneticisini kurun:

```text
npm install --global yarn
```

Doğru kurulup kurulmadığını kontrol edin:

```text
yarn -v
```

### **2. Örneklerimizle Waffle Kullanımı**

[AcalaNetwork/evm-examples](https://github.com/AcalaNetwork/evm-examples) deposunda gerekli tüm bağımlılıkları toplayarak bunu kolaylaştırdık.

Depoyu klonlayın ve bağımlılıkları yükleyin.

```text
git clone https://github.com/AcalaNetwork/evm-examples
cd evm-examples/erc20

yarn install 
```

### **3. Waffle'ı Sıfırdan Kullanma (isteğe bağlı)**


Alternatif olarak, her kitaplığı aşağıdaki gibi ayrı ayrı kurabilirsiniz:

`smart-contract-waffle` proje klasörü oluşturun

```text
mkdir smart-contract-waffle
cd smart-contract-waffle
```

Paket yöneticisini başlatın

```text
yarn init -y
```

Bağımlılıkları yükleyin

```text
yarn add --dev @openzeppelin/contracts@3.3.0 ethereum-waffle@3.2.1
```

Not: Değişiklikleri bozmamak için tam sürümlerle bağımlılıkları yüklemeniz önerilir.

Ardından bir waffle ayarları dosyası oluşturun.

```text
touch waffle.json
```

Aşağıdakini `waffle.json` dosyasına yapıştırın.

```text
 {
    "compilerType": "solcjs",
    "compilerVersion": "0.6.2",
    "sourceDirectory": "./contracts",
    "outputDirectory": "./build"
  }
```

This sets up the solidity compiler with version `0.6.2`, compiles contracts from the `./contracts` folder, and saves the bytecode output and ABI files to `./build` folder.


Now create the `./contracts` folder, and add the `BasicToken.sol` contract.

```text

mkdir contracts
touch contracts/BasicToken.sol
```

Paste the following content into the `BasicToken.sol` file and save.

```text
pragma solidity ^0.6.0;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";

// Example class - a mock class using delivering from ERC20
contract BasicToken is ERC20 {
    constructor(uint256 initialBalance) public ERC20("Basic", "BSC") {
        _mint(msg.sender, initialBalance);
    }
}

```

### **4. Compile the Smart Contract**
Now compile the contract into ABI and bytecode. Run the following in the terminal

```text
yarn waffle
```

### **5. Get the ABI file**

Waffle will then generate the output file `./build/BasicToken.json` into the `./build` folder. 

Note: this file should be the same as the one created with Remix.

Waffle also provides a full suite of testing utilities, check out their documentation and code samples [here](https://github.com/EthWorks/Waffle).

