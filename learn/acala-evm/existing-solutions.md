# Mevcut Çözümler

Mevcut Substrate EVM uyumluluk çözümü, yani [Frontier](https://github.com/paritytech/frontier), Ethereum düğümünü taklit eder. Tüm Ethereum RPC setini uygulamayı ve Ethereum blok üretim sürecini taklit etmeyi amaçlar. Bu, Metamask ve Remix gibi mevcut Ethereum araçlarının Frontier özellikli bir düğümle sorunsuz bir şekilde çalışmasına olanak tanır.

Integrating Frontier, aşağıdaki zorlukları önem derecelerine göre aşağıda sıralamıştır:

## **1. EVM Sandbox'ın içine hapsedilmiş**

Frontier, kullanıcıların Metamask veya hiçbiri henüz Substrate'ı tam olarak desteklemeyen diğer mevcut Ethereum araçları aracılığıyla EVM ile etkileşime girmesine olanak tanır. Acala DeX gibi yerel Substrate modüllerinden, birden fazla para birimini ve çapraz zincir kabiliyetini destekleyen token paletlerinden ve Laminar'ın marj ticaret paleti gibi herhangi bir parachain tarafından oluşturulan diğer paletlerden herhangi bir işlevselliğe Metamask veya diğer mevcut Ethereum aracılığıyla erişilemez. araçlar.

Bu, kullanıcıların bu konuda Acala, Substrate veya Polkadot'un gerçek gücünü tatmak isterlerse, bir Substrate wallet \(örneğin Polkadot-js Extension\) ve Metamask'ı aynı anda kullanmaları gerektiği anlamına gelir. Bu kesinlikle bizim için bir anlaşma kırıcı.

## **2. Düğümleri Daha Pahalı Hale Getirmek**

[Frontier](https://github.com/paritytech/frontier) tasarımı gereği ağırdır. Substrat, işlemleri hash veya geçmiş olaylara göre saklamaz ve herhangi bir olay filtreleme yeteneği sağlamaz. Substrat düğümleri, kaynak kullanımını \(disk alanı ve CPU\) en aza indirmek için tasarım gereği hafiftir.

Ethereum düğümleri ise, kullanıcıların işlemleri hash ile sorgulamasına izin verir ve güçlü olay günlüğü sorgulama API'si sunar. Frontier, Ethereum'un gerektirdiği sorgu API'sini güçlendirmek için işlemleri ve olayları zincir dışı bir yardımcı depoya depolayarak özel blok içe aktarma mantığı enjekte eder.

Bu, bir düğümü çalıştırmak için daha güçlü makineler ve daha büyük disk alanı gerektirdiğinden bakım maliyetlerini artırır. Bu, ağın daha merkezi olmayan hale gelmesine yardımcı olan, herhangi bir yerden insanların düğümleri çalıştırması için engelleri azaltmak için hafif bir düğüme sahip olma hedefine aykırıdır.
