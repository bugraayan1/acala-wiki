# Bir Havuzu Önyükleme

**\(**[**Kaynak**](https://github.com/AcalaNetwork/Acala/blob/master/modules/dex/src/lib.rs#L462)**\)**

## **Önyükleme Parametreleri ve İşlem**

Aşağıdaki parametrelerle bir likidite havuzu önyüklenebilir

* **Önceden Değil**: havuz belirli bir blok numarasından önce başlatılamaz
* **Token A için Hedef Karşılığı**: Token A için minimum likidite gereksinimi
* **Token B için Hedef Karşılığı**: Token B için minimum likidite gereksinimi
* **Token A için minimum katkı**: her katkı minimum miktarda Token A gerektirir
* **Token B için minimum katkı**: her katkı minimum miktarda Token B gerektirir

Bir likidite havuzu ancak aşağıdaki kriterler karşılandığında başlatılabilir:

* **`Önceki Değil`** bloğu geçti VE
* Ya **`Token A için Hedef Tedarik`** VEYA **`Token B için Hedef Tedarik`** karşılandı VE
* Hem Token A hem de Token >0 likiditeye sahiptir

## **Önyükleme Sırasında**

Önyükleme döneminde:

* **ticarete izin verilmez**, bu nedenle döviz kuru konsolide edilebilir
* Token A veya Token B veya Token A ve B için aynı anda likiditeye katkıda bulunabilirsiniz. Token A ve B'nin gerçek döviz kuru ancak Bootstrap tamamlandıktan sonra bilinebilir.
* Katkınız sırasında size bir dizi LP jetonu ve daha fazla likidite eklendikçe değişebilecek havuzun gösterge niteliğindeki LP payları tahsis edilir.
* **Yalnızca havuz için likidite sağlayıcısı olmak istiyorsanız katılmalısınız. Lütfen ** [**çeşitli riskler**](lp-returns-and-risks.md) **bir likidite sağlayıcı olmakla ilgili** farkında olun.

### LP Simgesi ve LP Paylaşımları

LP jetonları, bir havuza katkıda bulunan likidite makbuzlarıdır. LP Hisseleri \(= LP Jetonları / Toplam LP Jetonları\), belirli bir havuzun likidite katkısının orantılı temsilleridir, ör. Jeton A-Token B havuzu.

Token A-Token B havuzuna yapılan katkının ardından LP Jetonlarını hesaplamak için aşağıdaki formül kullanılır:

$$
LP Jetonları = Token A Katkısı * 1 + Token B Katkısı * Döviz Kuru
$$

Aşağıda, Bootstrap döneminde havuza daha fazla likidite eklendikçe bir kullanıcının havuzdaki LP Paylarının nasıl değişebileceğinin bir simülasyonu bulunmaktadır:

* Kullanıcı 1 yalnızca 1000 Token B'ye katkıda bulunur. LP Jetonları ancak havuzun her iki tarafı da biraz likiditeye sahip olduğunda hesaplanabilir.
* Kullanıcı 2 likiditesini ekledikten sonra \(Kullanıcı 2 yalnızca 50 Token A'ya katkıda bulunur\),
  * Token A-Token B'nin döviz kuru 0,05 \(=50/1000 [sabit ürüne](https://wiki.acala.network/karura/defi-hub/swap/protocol-overview#trading-and göre) -lps)\)
  * Kullanıcı 2'nin LP Simgesi 50'dir \(=50\*1 + 0 \* 0.05\)
  * Kullanıcı 1'in LP Simgesi de 50 \(=1\*0 + 1000 \* 0.05\)
  * Kullanıcı 2 LP Paylaşımı %50 \(=50/\(50+50\)\)
  * Kullanıcı 1'in LP Payları da %50'dir
* Kullanıcı 4 likiditesini ekledikten sonra \(Kullanıcı 4 hem Token A hem de B'ye katkıda bulunur\)
  * Token A-Token B'nin döviz kuru 2 \(=2200/1100\)
  * Kullanıcı 4'ün LP Payı %52,27'dir
  * Kullanıcı 2'nin LP Payları %1,14'e düştü.
  * Kullanıcı 1'in LP Payları %45,45'e düşüyor.
* Bootstrap bu noktada tamamlanırsa
  * Kullanıcı 1, 1000 Jeton A \(= 2200\*45,45%\) ve 500 Jeton B \(= 1100\*45,45%\) kullanabilir.
  * Kullanıcı 2, 25 Jeton A ve 12.5 Jeton B'yi kullanabilir
  * Kullanıcı 4, 1.150 Token A ve 575 Token B kullanabilir
  * LP'ler, çoğu getiri ticaret ücretlerinden geldiğinden, Bootstrap'ten hemen sonra kullanılabilir veya kullanılmayabilir. Daha fazlasını [buradan](lp-returns-and-risks.md) okuyun.

**Yani, havuzun yalnızca bir tarafına katkıda bulunuyorsanız \(Diyelim ki Token A\), Bootstrap sona erdiğinde \(ve havuz ticaret için açıldığında\) döviz kuruna bağlı olarak %50 Token A'yı Token B'ye etkili bir şekilde dönüştürüyorsunuz. .**

![Önyükleme sırasında LP Paylaşımı değişikliği](../../../.gitbook/assets/screen-shot-2021-07-20-at-2.36.47-pm.png)

![LP Token hesaplamaları](../../../.gitbook/assets/screen-shot-2021-07-20-at-2.37.00-pm.png)

## **Önyüklemeden Sonra**

Bootstrap havuzunun, 4. kullanıcının katkısından \(yukarıda gösterildiği gibi\) sonra tamamlandığını varsayalım, ardından LP jetonları her bir likidite sağlayıcısına tahsis edilir. LP Shares \(= LP Tokens / Total LP Tokens\), LP'nin belirli bir havuzun genel likiditesine katkısının orantılı bir temsilidir. LP Jetonları daha sonra herhangi bir zamanda temel alınan varlıklar \(Token A ve B\) için kullanılabilir. Örnek olarak, Kullanıcı 1, Simge A'nın %45,45'ini \(1000 Simge A = 2200\*%45,45\) ve Simge B'nin %45,45'ini \(500 Simge B = 1100\*%45,45\) kullanabilir.

* Bootstrap tamamlandıktan sonra LP jetonlarınızı talep etmeniz gerekir.
* Token A-Token B havuzu ticaret için etkinleştirilecek

İşte bunu göstermek için bir örnek:

![](../../../.gitbook/assets/screen-shot-2021-07-13-at-9.59.36-am%20%281%29.png)

## **Bir Havuzu Önyüklemek İçin Bir Teklif Gönderin**

Bu, bir havuzun ön yüklemesini önermenin ön görüntüsüdür. Bir teklifin nasıl gönderileceği hakkında daha fazla bilgiyi [buradan](../../get-started/governance/participate-in-democracy.md) okuyun.

![](../../../.gitbook/assets/screen-shot-2021-07-13-at-10.10.36-am.png)
