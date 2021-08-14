# Harmanlayıcı

## Genel Bakış

Düzenleyiciler, kullanıcılardan parachain işlemlerini toplayarak ve Relay Chain doğrulayıcıları için durum geçiş kanıtları üreterek parachainleri korur. Başka bir deyişle, derleyiciler, parachain işlemlerini parachain blok adaylarında toplayarak ve bu bloklara dayalı olarak doğrulayıcılar için durum geçiş kanıtları üreterek parachainleri korurlar.

Karura'nın ağ güvenliği ve fikir birliği \(nPoS\) Kusama Relay zincirinin Doğrulayıcı seti tarafından sağlanırken, Karura'nın Harmanlayıcı seti, doğrulayıcıların doğrulaması için parachain işlemlerini toplayarak ağı canlı tutacaktır. Doğrulayıcılardan farklı olarak, harmanlayıcılar ağı güvence altına almaz, bir parachain sansüre dayanıklı olması için yalnızca bir dürüst harmanlayıcıya ihtiyaç duyar.

Karura'nın Harmanlayıcı düğümü, Kusama Realy Zinciri için tam düğüm hizmeti ve Karura ağı için tam düğüm hizmeti sağlar. Her hizmetin kendi http/ws RPC uç noktaları, P2P bağlantı noktaları vb. vardır. Kusama tam düğüm hizmetinin temel yolu, Karura tam düğüm hizmetinin temel yolunun içinde bulunur.

## Derleyici Kullanım Planı

Karura, Harmanlayıcı operasyonunu başlatmak için aşamalı bir yaklaşım benimsiyor. Harmanlayıcılar güvenlik açısından kritik olmayan işlemler olduğundan, bir parachain sansüre dayanıklı olması için yalnızca bir dürüst Harmanlayıcıya ihtiyaç duyar ve daha fazla harmanlayıcı mutlaka iyi değildir; ağı yavaşlatacağından, Harmanlayıcı kullanıma sunma planı her şeyden önce ağ kararlılığını ve çalışmasını sağlamak için tasarlanmıştır.

**Geçerli Aşama: Özel Harmanlayıcı Seti**

**Aşama 0: Özel Harmanlayıcı Seti**
Karura ağının Genesis'i 23 Haziran 2021'de başlatıldı. Oluşum üzerine, Karura'nın ağ güvenliği ve fikir birliği, Kusama Relay Chain'in aday gösterilen Proof-of-Stake \(nPoS\) doğrulayıcıları tarafından sağlanır. Statemine \(Kusama'daki ortak yarar para zinciri\) gibi, Karura'nın Harmanlayıcıları, Harmanlayıcı yazılımı kararlı hale gelene ve daha geniş topluluğa yayınlanabilene kadar başlangıçta Acala Vakfı tarafından yürütülecek.

**Aşama 1: Yetkili Harmanlayıcı Seti**
Yönetim onayı aracılığıyla Karura, daha sonra Harmanlayıcı setini yetkili bir toplayıcı grubuna açar. Bu yetkili derleyiciler için blok ödülü veya ek teşvik bulunmamakla birlikte, Acala Vakfı tarafından düğüm hizmeti sağlamaları için makul bir ücret ödenir.

Bu derleyiciler, kanıtlanmış hizmet seviyeleri geçmişine sahip ve ağa derin bir bağlılık gösteren, bilinen saygın düğüm hizmeti sağlayıcılarıdır. Bu aşamada hala çok fazla kaos ve yazılım güncellemesi olması bekleniyor ve bu ortakların ağ istikrarını sağlamak için çekirdek geliştirme ekibiyle yakın bir şekilde çalışması gerekiyor.

Karura ağının, ağ tamamen stabilize olana, harmanlayıcı stake etme modülü ve ödül planı tamamen uygulanıp denetlenene kadar böyle bir yetkilendirilmiş Harmanlayıcı Setini sürdürmesi beklenmektedir.

**Aşama 2: Genel Harmanlayıcı Seti**
Yönetim onayı sayesinde Karura, daha sonra Harmanlayıcıların izinsiz seçilmesine ve ortak ödüllerinin verilmesine olanak sağlayacak. Harmanlayıcıların güvenlik açısından kritik olmaması nedeniyle, bir parachain canlılığı ve sansür direncini sağlamak için yalnızca küçük bir Harmanlayıcı grubuna ihtiyaç duyar, ödül planı buna göre bunu yansıtacaktır.

[Bu formu doldurarak](https://forms.gle/WQesfKVZmJeXov1e9) Karura Ağı \(ve daha sonra Acala Ağı\) için bir derleyici/canlılık sağlayıcısı olmakla ilgilendiğinizi belirtebilirsiniz.

Güncellemeler ve son dakika değişiklikleri için Discord'umuzdaki [`Düğüm Operatörü - Duyuru`](https://discord.gg/uWSZWsUcEn) kanalına abone olabilirsiniz.

## Harmanlayıcı Düğümü

### Özel Gereksinim

[Kusama doğrulayıcı düğüm gereksinimi](https://guide.kusama.network/docs/mirror-maintain-guides-how-to-validate-kusama/#requirements) ile aynı.

### Düğümü Çalıştır

[Tam Düğüm Kılavuzuna](ful-node.md) bakın.

### Harmanlayıcı Yapılandırması

#### **Anahtar yönetimi**

Karura Harmanlayıcının Aura oturum anahtarına ihtiyacı var. Oturum anahtarını güncellemek için RPC "author_rotateKeys" veya "author_insertKey" kullanılabilir.

#### **Kayıt**

* Karura, harmanlayıcı kaydını işlemek için şu anda Statemint'in 'collectorSelection' paletini kullanıyor. Yetkilendirilmiş Harmanlayıcı seti aşamasında, gerekli adaylık bonosu, halka açık kaydı önlemek için ulaşılamayacak kadar yüksek bir değer olacaktır.
* Yetkili sağlayıcıların, harmanlayıcı için Aura oturum anahtarının genel anahtarını göndermesi gerekecektir.

#### CLI

* Parachain kısmı için `--collator`
### **Örnek CLI**

```text
--base-path=/acala/data
--chain=karura
--name=collator-1
--collator
--execution=wasm
--
--chain=kusama
```

