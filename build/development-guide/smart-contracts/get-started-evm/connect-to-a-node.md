# Bir Düğüme Bağlan

Acala EVM'yi kullanmak için bir Acala Node'a bağlanmanız gerekir. sen de yapabilirsin

1. yerel bir Acala test düğümü çalıştırın
2. konuşlandırılmış bir test ağına bağlanın \(Acala tarafından sağlanır\)

### **1. Yerel bir Acala test düğümü çalıştırın Yorum**

Kendi düğümünüzü çalıştırmak için makinenize [Docker](https://www.docker.com/) yüklemiş olmanız gerekir. Yüklü değilse lütfen [buradaki](https://docs.docker.com/get-docker/) talimatları uygulayın.

Docker'ın başarıyla yüklenip yüklenmediğini kontrol etmek için aşağıdaki komutu çalıştırın:

```text
docker version
```

Versiyon numarasını alırsanız, aşağıdaki komutla yerel Acala düğümünüzü başlatabilirsiniz:

```text
docker pull acala/acala-node:latest
docker run -it -p 9944:9944 -p 9933:9933 acala/acala-node:latest --dev --ws-external --rpc-external --rpc-cors=all
```

Düğümünüzün çıktısı şöyle görünmelidir:

![](https://i.imgur.com/EyryyFs.png)

### **2. Dağıtılmış bir test ağına bağlanın**

Mevcut tüm test ağı düğümlerine [buradan](https://wiki.acala.network/learn/get-started/public-nodes#mandala-test-network-nodes) ulaşabilirsiniz.
