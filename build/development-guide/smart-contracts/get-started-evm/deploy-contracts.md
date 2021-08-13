# Kontratları Çalıştırma

Acala EVM Playground, Acala EVM'nin çeşitli fonksiyonlarını test etmek için kullanışlıdır. Bu, "canvas-ui" paritesinden bir çatallanmadır.

### **1. Kurulum**

Akıllı sözleşmenizi dağıtmak için test ağımızı kullanabilir veya yerel geliştirme düğümünüzü çalıştırabilirsiniz.

#### Kendi geliştirme düğümünüzü çalıştırın**

Geliştirme düğümünüzü çalıştırmak için şunları yapabilirsiniz:
1. Acala projesini yerel olarak oluşturun.
    Nasıl yapılacağına ilişkin kılavuzu buradan takip edebilirsiniz:
    [https://github.com/AcalaNetwork/Acala#3-building](https://github.com/AcalaNetwork/Acala#3-building). Acala'yı kurduktan sonra, aşağıdaki komutu çalıştırarak bir EVM hazır yerel geliştirme düğümü başlatabilirsiniz:

```bash=
make run-eth;
```
2. Önceden oluşturulmuş Acala Docker görüntüsünü kullanın.
    Makinenizde Docker'ın kurulu olması gerekir. Kurulum talimatlarını buradan takip edebilirsiniz: [Docker'ı Kur](https://docs.docker.com/get-docker/). Docker çalıştığında, son acala görüntüsünü çekmeniz ve çalıştırmanız gerekir:
    
```shell=
docker pull acala/acala-node:latest
docker run -p 9944:9944 acala/acala-node:latest --name "calling_home_from_a_docker_container" --rpc-external --ws-external --rpc-cors=all --dev
```

Düğümünüz çalıştığında, terminal pencerenizde buna benzer bir şey görmelisiniz:

![](https://i.imgur.com/MQEURQr.png)

Geliştirme düğümünüz çalışmaya başladıktan sonra, sol alt köşedeki açılır menüyü tıklayıp 'Yerel Düğüm'ü seçerek Acala EVM çalışma alanını düğümünüzü gösterecek şekilde ayarlayabilirsiniz.

![](https://i.imgur.com/pOfQb8z.png)

Yerel geliştirme düğümünü çalıştırınca, önceden finanse edilen geliştirici hesaplarıyla "Hesaplar" açılır listelerini önceden dolduracaktır.

**Test ağımızı çalıştırma**

Test ağımıza çalıştırmak için tarayıcınızda [polkadot{.js}](https://polkadot.js.org/extension/) cüzdan uzantısının yüklü olması gerekir.

Uzantıyı kurduktan sonra, Acala EVM çalışma alanında bulunan 'EVM Hesabı Kur' sayfasından hesaplarınızı bir EVM adresi ile bağlayabilir ve test ağı fonları alabilirsiniz. Daha ayrıntılı talimatlar için [buradaki](https://wiki.acala.network/build/development-guide/smart-contracts/get-started-evm/evm-account) belgeleri okuyun.

**Not:** Bu sayfanın geri kalanında yerel bir geliştirme düğümü kullandığınızı varsayacağız. Test ağına 'polkadot{.js}' uzantısını kullanarak dağıtım yapıyorsanız, 'Alice' ve 'Bob' hesaplarını uzantınızda oluşturduğunuz hesaplarla değiştirmeniz yeterlidir.

### **2. Sözleşme ABI ve bayt kodunu yükleyin**

[https://evm.acala.network/](https://evm.acala.network/) adresine giderek "BasicToken" ABI ve bayt kodu dosyasını yükleyin.

"Yükle" sekmesine gidin.

![](https://i.imgur.com/Ge3IwiM.png)


Sözleşme adını girin, ardından `BasicToken.json` sözleşme dosyasını yükleyin.

![](https://i.imgur.com/kRM8Mfb.png)

Daha sonra sözleşmede mevcut yöntemlerin bir listesini görüntülenecektir. Ardından 'Yükle'yi tıklayın.

### **3. Kontratı Çalıştırma**

ABI ve bayt kodu dosyasını yükledikten sonra, Oyun Alanı otomatik olarak "Dağıt" adımına gidecektir. Değilse, sol kenar çubuğundan "Dağıt"ı seçin. "BasicToken", "ABI paketlerinde" görünecektir.

'Dağıt' düğmesini tıklayın ve 'dağıtım hesabı' olarak 'Alice'i (veya tarayıcı uzantısını kullanıyorsanız hesabınızı) seçin.

![](https://i.imgur.com/FfoYEFU.png)

İlk kaynağı \(ör. "1000"\) ayarlayın ve "Dağıt"a basın.

![](https://i.imgur.com/wY0YG54.png)

İşlemi onayladıktan sonra otomatik olarak 'Yürüt' bölümüne gitmelisiniz. Veya sol kenar çubuğundaki "Yürüt" düğmesini tıklayarak oraya manuel olarak gidebilirsiniz.

![](https://i.imgur.com/wyrpMIv.png)


### **4. Sözleşmeyle Etkileşime Geçin**

"Yürüt" sekmesine gidin. Dağıtılan "BasicToken" sözleşmesini bulun ve "BasicToken" kutusunun altındaki "Execute" düğmesini tıklayın.


### **5. Bakiyeleri Sorgula**

Bir hesabın bakiyesini sorgulamak için aşağıdaki adımları uygulayın:

1. 'Hesaptan Ara' açılır menüsünden 'Alice'i seçin. Bu, işlemi göndermek için kullanılan hesaptır.

2. 'Gönderilecek Mesaj' açılır menüsünden 'balanceOf'u seçin.

3. 'Hesaptan Ara' altında Alice'in EVM Adresini bulun, kopyalayıp 'hesap: adres' girişine yapıştırın.
![](https://i.imgur.com/xH1j0ph.png)

**Note:** Solidity kontratları iki tip metoda sahiptir: `views` ve `executable` metodları.

- "Views", blok zincirine veri yazmadan bilgi sorgulamak için kullanılır. 'Views' işlemleri ücretsizdir. Çalışma Alanı bunu belirtmek için "Ara" düğmesini kullanır.
- 'Executable' yöntemler blok zincirine veri yazabilir ve bu işlemler ücretsiz değildir. Yürütmek için 'Executable' düğmesini tıklayın.

Son olarak, alttaki 'Ara'yı tıklayın ve 'Çağrı sonuçları' Alice'in (1000) BasicToken bakiyesini göstermelidir.

![](https://i.imgur.com/GS7Znys.png)

### **6. Transfer Yapma**

Şimdi BasicTokens'i Bob'un Hesabına aktarmayı deneyelim.

1. Hesap açılır menüsünden 'Alice'i seçin.

2. 'Gönderilecek Mesaj' açılır menüsünden 'aktarım'ı seçin.

3. 'Hesaptan Ara' açılır menüsünden Bob'un hesabını seçin (Alice için yaptığımız gibi BOB'nin hesabına EVM adresini bağlamayı unutmayın), ardından 'EVM adresini' kopyalayın ve 'alıcı adresi' giriş kutusuna yapıştırın . ("Hesaptan Ara"yı tekrar "Alice" olarak değiştirmeyi unutmayın)

4. "amount: unit256" bağımsız değişken kutusuna transfer tutarını girin, belirtecin standart 18 ondalık basamağa sahip olduğunu unutmayın.

5. 'Yürüt'e tıklayın.

![](https://i.imgur.com/l2utsuN.png)

İşlemin başarılı olduğunu onaylamak için bir bildirim açılır.

Şimdi Alice ve Bob'un bakiyelerini kontrol edin ve değiştiklerini onaylayın.
Alice'in hesabı:

![](https://i.imgur.com/SCLwxRk.png)

Bob'un hesabı:

![](https://i.imgur.com/pi3AKiN.png)
