# KAR talebinde bulunun

**🔔 UTC 03:00 19 Temmuz 2021: beri** [**Karura çalışma zamanı yükseltmesinden**](https://acala.discourse.group/t/1-karura-runtime-upgrade-disable-sudo- enable-token-transfers/163) **- Sudo'yu devre dışı bırak ve aktarımı etkinleştir önümüzdeki 24-48 saat içinde yürürlüğe girecek, Talep KAR hizmeti şu andan itibaren hafta sonuna kadar geçici olarak çevrimdışı olacak. Anlayışın için teşekkürler.**

Resmi olarak desteklenenler dışındaki kanallardan Karura kitle kredisine katıldıysanız, belirteçlerinizi talep etmek için Şartlar ve Koşullarımızı okumanız ve kabul etmeniz gerekir. KAR talebinde bulunmanız gerekip gerekmediğini [buradan](https://distribution.acala.network/) kontrol edebilirsiniz.

## Polkadot{js} Uzantısını Kullanma

Talep Web Sitesine Dağıtım sitesinden veya doğrudan [buradan](https://distribution.acala.network/claim) gidebilirsiniz. Polkadot{js} Uzantınızı **Crowdloan etkinliğine katılan aynı hesabı kullanarak** bağlayın ve işlemi tamamlamak için talimatları izleyin.

Bir mesajı imzalamak için uzantıyı kullanmanızı gerektirir, ancak herhangi bir işlem ücreti gerektirmez. İşlem tamamlandıktan sonra, dağıtımın planlanması 48 saat kadar sürebilir.

## Manuel Talep

Talep Web Sitesine Dağıtım sitesinden veya doğrudan [buradan](https://distribution.acala.network/claim) gidebilirsiniz. Kitle kredisi etkinliğine Polkadot{js} uzantısıyla katılmadıysanız, "Manuel Olarak Talep Edin"i seçin ve **Karura kitle kredisine katılmak için kullandığınız adresi girin**.

![](../../.gitbook/assets/screen-shot-2021-07-12-at-12.38.19-pm.png)

iddia etmenin iki yolu var

1. Belirli bir mesajla Kusama'ya bir Sistem Açıklaması gönderin VEYA
2. Belirli mesajı imzalamak için İmzala ve Doğrula'yı kullanın

Aşağıda, hak talebinde bulunmak için nasıl kullanılacağına ilişkin kılavuzlar bulunmaktadır.

### İmzala ve Doğrula'yı Kullanma

[Polkadot Uygulaması - Geliştirici - İmzala ve Doğrula](https://polkadot.js.org/apps/#/signing) \(Polkadot, Kusama veya Karura'yı kullanmak sorun değil\) sayfasına gidebilirsiniz. İmzala ve Doğrula, yalnızca mesajı imzalar ve işlem maliyeti gerektirmez.

1. **Karura kitle kredisinde kullanılan hesabın aynısını** seçmelisiniz.

![](../../.gitbook/assets/screen-shot-2021-07-12-at-11.33.10-am.png)

2. `Aşağıdaki verileri imzalayın` alanına, \(Talep web sitesinde gösterilir\) imzalamak için gerekli mesajı kopyalayıp yapıştırın.

```metin
SHA-256 multihash'i QmSfG9pSE3eaQzFDQ1S421nj6sKJxFE8AYefwojg1Rkt2W olan ifadenin şartlarını kabul ediyorum. (Bu URL'de bulunabilir: https://acala.network/karura/terms)
```

3. İşlemi tamamlamak için imzalayın, hash'i kopyalayın ve Talep web sitesine geri yapıştırın

![](../../.gitbook/assets/screen-shot-2021-07-12-at-11.37.17-am.png)

İşlem tamamlandıktan sonra, dağıtımın planlanması 48 saat kadar sürebilir.

### Sistem Açıklamasını Kullanma

Mesajı imzalamak için İmzala ve doğrula'yı kullanamıyorsanız, ör. Katılmak için bir proxy hesabı kullandıysanız veya kitle kredisine katıldığınız ajansın \(ör. cüzdan\) bir imza ve doğrulama olanağı yoksa, KAR talep etmek için Kusama zincirine bir Sistem Açıklaması gönderebilirsiniz.

1. [Polkadot Uygulamaları - Kusama](https://polkadot.js.org/apps/#/explorer)'da oturum açın, **Kusama Uygulamasına geçmelisiniz.**

![](../../.gitbook/assets/screen-shot-2021-07-12-at-12.22.02-pm.png)

2. "Geliştirici-Dışsal Bilgiler" bölümüne gidin

![](https://i.imgur.com/ryY5FGa.png)

3. **Karura kitle kredisinde kullanılan hesabın aynısını** seçmelisiniz.

"Aşağıdaki harici bilgileri gönder" alanında, "sistem"i ve ardından açılır menüden "remarkWithEvent(_remark)" öğesini seçin

![](https://i.imgur.com/aRFAG4P.png)

4. `_remark: Bayt` alanına imzalamak için gerekli mesajı girin. \(Talep web sitesinde gösterilir\) imzalamak için gerekli mesajı kopyalayıp yapıştırın.

```metin
SHA-256 multihash'i QmSfG9pSE3eaQzFDQ1S421nj6sKJxFE8AYefwojg1Rkt2W olan ifadenin şartlarını kabul ediyorum. (Bu URL'de bulunabilir: https://acala.network/karura/terms)
```

5. Ve `İşlemi Gönder` düğmesine tıklayın.

![](https://i.imgur.com/DWzU3bg.png)

6. Parolanızı girin ve işlemi imzalayın. İşlemi başlatmak için küçük bir ücret ödemeniz gerekeceğini unutmayın, bu nedenle hesabınızda biraz para olduğundan emin olun.

![](https://i.imgur.com/33Yb0qW.png)

7. Yorum işleminiz Kusama'ya iletildi. İmzalı açıklamayı [Kusama Subscan Explorer](https://kusama.subscan.io/) adresinde görüntüleyebilirsiniz. İşlemi göndermek için kullandığınız Kusama adresinizi yapıştırın.

![](https://i.imgur.com/nCCwxXm.png)

8. İşlem geçmişinizde `system(remark_with_event)` göreceksiniz. İlgili 'Dış Kimliğe' tıklayın

![](../../.gitbook/assets/sdxvujr.png)

9. 'Extrinsic Hash'i kopyalayın

![](../../.gitbook/assets/5i1qfz3.png)

10. İşlemi tamamlamak için Extrinsic hash'i Claim web sitesine geri yapıştırın

İşlem tamamlandıktan sonra, dağıtımın planlanması 48 saat kadar sürebilir.
