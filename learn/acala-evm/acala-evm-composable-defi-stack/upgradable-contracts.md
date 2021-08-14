# Yükseltilebilir Sözleşmeler

### **Yükseltilebilir Akıllı Sözleşmeler.**

Acala EVM'de geliştiricilerin artık hataları düzeltmek veya mevcut uygulamalarda iyileştirmeler yapmak için karmaşık geçiş sözleşmeleri yazmalarına gerek yok. Sözleşmeyi yürüten kişi, kullanıcıları veya likiditeyi "geçmeye" gerek kalmadan sözleşmeleri sorunsuz bir şekilde yükseltmek için yeni sözleşme bayt koduyla bir işlem gönderebilir.

Ayrıca, ana ağ üzerinde halkla doğrudan test etme riskini azaltmak için iki aşamalı bir dağıtım süreci vardır.

* **Dağıtılan Özel Sözleşme**: Bir sözleşme dağıtıldıktan sonra, varsayılan olarak herkese özeldir ve yalnızca 'Sözleşme Sorumlusu' \(sözleşmeyi dağıtan\) ve kaydolan geliştiriciler tarafından görülebilir. Gerekli tüm testler ve nihai doğrulama, kamuya açıklanmadan önce yapılabilir. 'Sözleşme Sorumlusu' da gerekirse bu aşamada sözleşmeyi kaldırabilir.
* **Dağıtılmış Kamu Sözleşmesi**: 'Sözleşme Sorumlusu' sözleşmeyi kamuya açık hale getirebilir, yani işi halka açık hale getirebilir.

Kullanıcıları halka açık bir defterde depolama elde etme konusunda dikkatli olmaya teşvik etmek ve aynı zamanda dolandırıcılığı azaltmak için "Devlet Kiralama" mekanizmasını kullanıyoruz. 'Sözleşme Sorumlusu', bir sözleşmeyi dağıtırken, sözleşme zincirden kaldırıldığında iade edilecek bir teminat koymak zorundadır.

Bazı giriş engelleri daha sorumlu davranışları teşvik eder ve bunu başarmak için sürekli olarak daha iyi mekanizmalar için alan araştırıyoruz.
