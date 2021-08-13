# EVM Çalışma Ortamı

Acala EVM'nin çeşitli fonksiyonlarını test etmek için bir web uygulaması - **Acala EVM Çalışma Ortamı** oluşturduk. Bu, "canvas-ui" paritesinden bir çatallanmadır.

Ortamı çalıştırmak için [https://evm.acala.network/](https://evm.acala.network/) adresini kullanabilirsiniz.

Oyun Alanı varsayılan olarak Acala test ağına bağlıdır. Ayrıca yerel bir düğüme de bağlanabilir. Playground'u daha önce kullandıysanız, bağlantı bilgileri önbelleğe alınabilir.

### Düğüm Bağlantısının Kurulumu

Oyun Alanının sol alt köşesindeki bağlantı sekmesine tıklayın.

![](https://i.imgur.com/9qnD9Gq.png)

Bağlanmak istediğiniz düğümü seçmek için `Bağlanılacak düğüm` açılır menüsüne tıklayın

- Yerel Acala düğümünüze bağlanmak için 'Yerel Düğüm'ü seçin.
- Dağıtılan Acala test ağına bağlanmak için `Acala`yı seçin.
- Özel bir Websocket URL'si girmek için "Özel uç noktayı kullan"ı tıklayın

![](https://i.imgur.com/eHAdxLb.png)

### Bind EVM address

Akıllı sözleşmeleri kullanmak için bir EVM adresinizin olması gerekir. Varsayılan olarak, adresi kullanıcının hesabına eklemeyiz ve kullanıcıların adresi talep etmesi gerekir. Bir EVM hesabı talep etmek bir işlemdir ve bunun için ödeme yapmak için jetonlarınızın olması gerekir.

Acala düğümünüzü çalıştırıyorsanız ve standart Geliştirme hesapları (Alice, Bob) kullanıyorsanız, yeterli paranız vardır. Acala test ağı tarafından kullanılmasına rağmen, bir "faucet" kullanarak para kazanmanız gerekir.
Sol üst köşedeki "EVM Hesabını Kur" seçeneğine tıklayarak EVM hesap ayarlarına gidin.
![](https://i.imgur.com/F6UTXtm.png)
Ardından, "Adım 1"de bir alt tabaka hesabı seçin. Yerel düğümü kullanmıyorsanız, seçilen hesabın altında bir "Faucet" düğmesi göreceksiniz.
Test jetonlarını almak için tıklayın.
Ve son olarak, oluşturulan EVM'yi cari hesaba eklemek için alttaki "Bağla" düğmesine tıklayın. Polkadot.js uzantınızdan işlemi onaylayın.
Bir onay almalısınız.

### Bakiye Kontrolü

Alice'in DOT bakiyesini kontrol edelim. Sol kenar çubuğunda 'Yürüt'ü tıklayın.

Yerel belirteç sözleşmelerinin bir listesi görünecektir; DOT, aUSD, ACA, renBTC, vb. Bu yerel jetonlar \(renBTC gibi zincirler arası varlıklar dahil\), aksi takdirde bir EVM'de mevcut olmayacak olan önceden derlenmiş sözleşmeler olarak sunulur. Tedarikleri, hesaplardaki bakiyeler ve işlevlerin tümü EVM'de mevcuttur.

'DOT'u seçin ve altındaki 'Yürüt'e basın.
![](https://i.imgur.com/gGqwRZM.png)

'Hesaptan Çağrı'dan Alice'i seçin.

'Gönderilecek Mesaj'dan 'balanceOf'u seçin.

Alice'in hesabının altındaki "EVM Adresi"ne dikkat edin, kopyalayıp "sahip: adres" bağımsız değişken alanına yapıştırın.

Yürütmek için "Ara" düğmesini tıklayın.

![](https://i.imgur.com/8XQSarA.png)

En alttaki "Arama sonuçları", Alice'in DOT hesap bakiyesini göstermelidir.

![](https://i.imgur.com/2TNjbUM.png)
