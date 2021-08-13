# Zamanlayıcı Uygulaması

Bu eğitimde, kullanıcılara daha uzun süre abone olduklarında ödül veren otomatik bir abonelik hizmeti oluşturmak için Acala'nın zincirleme zamanlayıcısını kullanacağız.

## Kurulum

Eğitimde daha sonra testler oluşturmamıza izin vermek için Waffle kullanarak sıfırdan bir proje oluşturacağız. Akıllı sözleşmelerinizi Remix kullanarak oluşturmayı tercih ediyorsanız bu sayfaya göz atın [https://wiki.acala.network/build/development-guide/smart-contracts/get-started-evm/use-remix](https:/ /wiki.acala.network/build/development-guide/smart-contracts/get-started-evm/use-remix).

### 1. Bağımlılıkların Yüklenmesi

Başlamak için, henüz yapmadıysanız, düğümü ve yarn'ı yükleyelim:

```text
sudo apt install -y nodejs

npm install --global yarn
```

Ardından, projenizin yaşamasını istediğiniz klasörde aşağıdaki komutları çalıştırın:

```text
mkdir subscription-contract
cd subscription-contract

yarn init -y
yarn add --dev ethereum-waffle@3.2.1
```

Ve aşağıdaki betiği "package.json" dosyanıza ekleyin:
```text
"build": "waffle"
```

Bu, projemiz için bir klasör oluşturacak, yeni bir yarn projesi başlatacak ve bir geliştirme bağımlılığı olarak waffle ekleyecektir. Akıllı sözleşmelerimizi derlemek için waffle kullanacağız.

Proje klasörünüzde `waffle.json` adında bir dosya oluşturun ve aşağıdakini dosyanın içine yapıştırın:

```text
{
  "compilerType": "solcjs",
  "compilerVersion": "0.6.2",
  "sourceDirectory": "./contracts",
  "outputDirectory": "./build"
}
```
Bu dosya, akıllı sözleşmelerimizi oluştururken kullanılacak 'waffle' yapılandırmalarıdır.

Son olarak 'sözleşmeler' klasörümüzü oluşturalım.

```text
mkdir contracts
```
