---
Açıklama: Alt modülü kullanarak çalışma zamanı seviyesinde ACALA ile inşa edilir.
---

# Ekosistem modüllerini dağıtma

Aşağıda, alt modül kullanarak çalışma zamanı seviyesinde Acala ile inşa etmek için kaba bir kılavuzdur:

1. Proje ekibi bir alt modül repo'yu kurdu
2. Proje ekibi yerel olarak oluşturur ve test eder
3. Proje ekibi inceleme için repo gönderir
4. ACALA alt modülün içine çeker, TestNet'te çalışma zamanı yükseltmesi ile dağıtıyor
5. Güvenlik Denetimi
6. Yönetişim

** 1. Proje Yapısı ** Kendi reponunuzda bir alt modül oluşturacaksınız, hazır olduğunda, Acala'nın reposuna çekebiliriz. Bu, kod tabanınızın ve lisansınızın bağımsızlığına izin verir.

```text
// on Acala side, folder structure as follows
- Acala repo
  - ecosystem-modules
    - your-sub-module
```

[Örnek alt modül] (https://github.com/acalanetwork/ecosystem-template/tree/f42c127bf10239821E1E7A56565CDA4D64CD8D66). Kuruluşunuzda alt modül olarak kullanılacak bir repo oluşturacaksınız.

Alt modülünüz, Acala Repo uyarınca [Ekosistem-Modüller] (https://github.com/acalanetwork/acala/tree/master/ecosystem-modules) içine çekilecektir.

** 2. Yerel test ** çatal [ACALA Repo] (https://github.com/acalanetwork/acala), alt modülünüzü çekin ve yerel olarak test edin.

** 3. Yorum için kodu gönderin ** ACALA, mimari ve teknik rehberlik de dahil olmak üzere geliştirmeniz sırasında, mevcut kütüphaneleri ve standartları paylaşmanın yanı sıra teknik destek sağlayacaktır.

Geliştirmeyi tamamladıktan sonra, lütfen repo'nuzu gönderin ve teknisyen ekibimizin repo'ya çekmeden önce incelemelerine yardımcı olur ve geri bildirimde bulunacaktır.

** 4. TestNet Dağıtımı ** [ACALA Mandala Test Network] (https://wiki.acala.network/learn/get-starTed#Mandala-test-Network), yeni zincir mantıklarını ve işlevlerini doğrulamak için canlı bir değerli test. Modülünüz incelemeyi geçtikten sonra, Çalışma Zamanı Yükseltmesi ile Mandala'da konuşlandırılabilir.

** 5. AUDIT ** MODULE Seviyesi Entegrasyonu Acala Ağına Zincir Mantığını Değiştirirken, Proje Ekibi En Yüksek Esneklik ve Özelleştirme Düzeyi Sağlarken, Kodun güvenli ve amaç için uygun olmasını sağlamak için ACALA'da sorumluluk getirir ve istenmeyen genel zincir operasyonunun sonuçları. Bu nedenle, Acala'ya eklenen modüllerde güvenlik denetimi yapacağız ve bu olduğumda iletişim halinde olacağız.

** 6. Yönetişim ** Karura Kanarya Ağı'na (Kusama \) ve Mainnet \ (Polkadot'a bağlanma \) dağıtılması, ilgili yönetim tarafından belirlenir.
