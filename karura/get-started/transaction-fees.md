# İşlem ücretleri

**🔔 Karura, ücretlerin desteklenen herhangi bir simgede ödenmesine izin verir.** Ancak aktarım etkinleştirildikten sonra, yerel belirteç $KAR'da KSM/KAR, kUSD/'ye kadar işlem ücretlerinin ödenmesi gereken bir süre olacaktır. KAR ve diğer [Karura Swap](../defi-hub/swap/) havuzları önyüklenir, ardından işlem ücretlerini ödemek için KSM, kUSD ve diğer tokenler kullanılabilir.

İşlem ücretleri, kullanıcıların depolama ve hesaplama gücü gibi blok zincirinin çok fazla sınırlı kaynaklarını tüketmesini önlemek için kullanılır. Karura, gazın aksine ağırlığa dayalı ücretler kullanır, tahmin edilebilir ve sevkiyat öncesi ücretlendirilir.

### Ücret Tahminleri

Bunlar tipik ilgili işlemlerin kaba tahminleridir:

* **Kusama'dan Karura'ya transfer,** Zincirler arası transfer ücretlerinin iki bileşeni vardır:
  * Kusama tarafından belirlenen Kusama ücreti
  * Karura ücreti: 0.3 milliKSM~
* **Karura'dan Kusama'ya transfer,** Zincirler arası transfer ücretlerinin iki bileşeni vardır:
  * Karura ücreti: 4 milliKAR \(0,004 KAR\)~
  * Kusama tarafından belirlenen Kusama ücreti
* **Karura**
  * **Transfer:** 4 milliKAR \(0,004 KAR\)~
  * **DeX takası:** 12 milliKAR~
  * **Likidite ekleyin:** 18 milliKAR~
  * **KUSD kredisini ayarlayın:** 18 milliKAR~

Not: bunlar tahminlerdir ve gerçek işlem boyutuna, ağ koşullarına ve diğer faktörlere göre değişecektir.

Şimdilik, tüm işlem ücretleri Karura Hazinesine gidiyor - sürdürülebilir bir geleceğe küçük bir katkı. Daha fazlasını [buradan](treasury.md) okuyun.

### Ücret Ayarlaması <a id="ücret-adjustment"></a>

Karura'daki ücretler, işlem hacmine göre ayarlanır, ancak yine de tahmin edilebilir. Karura'nın bir blok doluluk hedefi vardır, hedefe göre mevcut bloğun doluluğuna bağlı olarak bir sonraki blok için ücretler artar veya azalır.

### Kendi Gazınızı Getirin

Kullanıcılar neden diğer belirteçleri aktarırken yerel belirteçte ücret ödemekle sınırlandırılıyor?! Karura'da buna gerek yok. Kullanıcılar, Karura ağında desteklenen herhangi bir belirteçte ücret ödeyebilir. KAR dışındaki jetonlarda ücretler ödenirken, ücretler hala KAR cinsinden tahmin edilir, zincir tarafından otomatik olarak gerçek zamanlı bir takas işlemi \(ödenen jeton ile KAR\ arasında) yürütülür. Bu işlem atomik ve kullanıcılar için şeffaftır.
