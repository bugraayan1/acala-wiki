# Genel Bakış

Karura, aşamalı olarak merkezileşmemesine ve nihayetinde çoğunluk ağ paydaşları tarafından komuta edilmesine izin verecek çeşitli yönetişim mekanizmalarını kullanmak için aşamalı bir yaklaşım benimsiyor. Karura'nın yönetişim çerçevesi, ağı yönetmek için bir Referandum odası, bir Genel Konsey ve bir Teknik Komite kullanan Polkadot teknolojisine dayanmaktadır.

Ancak Karura, Finans Konseyi ve Likit Stake Konseyi dahil olmak üzere ağın özel yönlerini yöneten alt konseylere sahiptir.

Karura Lansman Aşamaları ve aşamalı ademi merkeziyet yol haritası hakkında daha fazla bilgi edinin [buradan](https://www.notion.so/acala/dcabf9ba7c6246c69b913d5972503227?v=4121894373fd43d98ffcac260803928d).

## referandum

Referandum, basit, kapsayıcı, hisse bazlı bir oylama planıdır. Referandum, halk teklifi veya meclis teklifi ile başlatılabilir. Bununla ilişkili 8 günlük bir yürürlüğe girme gecikmesi var. Acil durum teklifleri \(ör. acil ağ sorunlarını düzeltin\), daha kısa bir yürürlüğe girme süresine sahip olmak için "hızlı izlenebilir".

Karura, Polkadot'un Tallying, Voluntary Locking, Adaptive Quorum Biasing dahil olmak üzere oylama mekanizmalarıyla deneyler yapıyor. Daha fazlasını [buradan](https://wiki.polkadot.network/docs/learn-governance/#refrenda) okuyun.

## Konseyler

### Genel Konsey

Karura, başlangıçta, çalışma zamanı yükseltmeleri, ağ sorunlarının çözülmesi ve iyileştirmeler gibi ağla ilgili kararları zincir üzerinde şeffaf hale getirilen Acala Vakfı tarafından atanan bir Genel Konsey ile birlikte bir Referandum odası tarafından yönetilecek. Bu arada, herhangi bir KAR sahibi ağda, protokollerde herhangi bir değişiklik önerebilir ve Karura Hazinesi, Referandum odası aracılığıyla toplu olarak lehte veya aleyhte oylanacaktır. Daha sonra Genel Konsey, kötü niyetli, güvenlik riski oluşturan veya Karura ağının çıkarına olmayan teklifleri durdurmak için veto haklarıyla gözetim sağlar.

Ağ yeterince önyüklendiğinde, istikrara kavuştuğunda ve güvenlik önlemleri alındığında, yönetimi meclis üyelerinin adaylığının açık olduğu ve meclis üyelerinin halk oylamasıyla seçildiği Seçilmiş Konsey aşamasına taşımak için bir Referandum başlatılacaktır.

### Mali Konsey

Stabilcoin parametreleri, DeX parametreleri, Liquid Stake ücretleri ve protokol görevlerinin güncellemelerini denetleme.

* Genel Konsey tarafından 2/3 onay oranı ile seçilir.

### Likit Staking Konseyi

Liquid Staking parametrelerinin güncellemelerini denetleme, ör. doğrulayıcı seçimi

* LKSM sahipleri tarafından seçildi.

### Oracle Kolektifi

Oracle operatörlerinin seçilmesi. [Oracle Ağ Geçidi](../../../learn/basics/oracle/) üyeliği, esasen yalnızca yetkili güvenilir operatörlerin fiyat beslemeleri sağlayabildiği bir Yetki Kanıtı modeli olan Genel Konsey'den onay gerektirir. ağ içine. Bu model, Oracle problemindeki çağdaş Ar-Ge ile gelişecektir.

* Genel Konsey tarafından 2/3 onay oranı ile seçilir.

## Teknik Komite

Ağın çalışması için kritik olan acil durum tekliflerini hızlandırmak, bir yasayı geciktirmek ve tartışmasız tehlikeli teklifleri iptal etmek.

* Genel Konsey tarafından 2/3 onay oranı ile seçilir.

## Acil Durum Eylemleri

* Zamanlanmış bir görevi 12 saate hızlandırın+
  * Gerekli: 1/3+ Teknik Komite mutabakatı
* Zamanlanmış bir görevi <12 saate hızlı takip edin
  * Gerekli: 2/3+ Teknik Komite mutabakatı
* Zamanlanmış bir görevi 48 saate kadar geciktirme
  * Gerekli: 1/3 Teknik Komite mutabakatı
* Zamanlanmış bir görevi iptal et
  * Gerektirir: programdan Origin VEYA
  * 3/4+ Genel Konsey mutabakatı
