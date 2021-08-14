---
tanım: Likidite sağlayıcı, değişim ücreti ve ek bir ödül ile ödüllendirilir.
---

# Likidite Sağlayın

* [Genel Bakış](https://wiki.acala.network/learn/basics/deposit-and-earn#overview)
* [Mandala Test Ağı](https://wiki.acala.network/learn/basics/deposit-and-earn#mandala-test-network)
  * [Web DApp ile](https://wiki.acala.network/learn/basics/deposit-and-earn#via-web-dapp)
    * [Mevduat Likiditesi](https://wiki.acala.network/learn/basics/deposit-and-earn#deposit-liquidity)
    * [Likidite Çekme](https://wiki.acala.network/learn/basics/deposit-and-earn#withdraw-liquidity)
    * [Ödülü Çekme](https://wiki.acala.network/learn/basics/deposit-and-earn#withdraw-reward)

## Genel Bakış

Acala'daki DeX \(Merkezi Olmayan Değişim\), kullanıcıların bir jetonu diğerine hızlı bir şekilde değiştirmesine olanak tanır ve platform için üç katlı amaca hizmet eder:

1. **ekosistemi önyüklemek için likidite sağlayın**: BTC ve ETH gibi varlıkların yanı sıra DOT, ACA ve aUSD gibi köprülü varlıklar için pazarlar olacaktır.
2. **kararlılığı artırmak ve riski azaltmak için stabilcoin tasfiye mekanizması için ücretsiz bir tesis olarak**: bir tasfiye tetiklendiğinde, kayma kabul edilebilirse, Honzon stabilcoin protokolü varlıkları açık artırma yerine DeX'te satacaktır.
3. **kullanılabilirliği iyileştirin**: kullanıcılar işlem tokeninde ücret ödeyebilir, ör. ağ belirteci ACA ile sınırlandırılmak yerine aUSD

Uniswap'tan ilham alan Acala DeX, sabit ürün mekanizmasını kullanır ve çalışma zamanı modülleri olarak uygulanır, dolayısıyla diğer protokollerle daha iyi entegre olur. Temel token olarak USD kullanan her işlem çifti, ör. BTC/aUSD bir değişim havuzu olarak temsil edilir. Döviz kuru, ilk likidite sağlayıcısı tarafından yatırdığı her bir token miktarına göre belirlenir ve zaman içinde arbitraj yoluyla ayarlanır.

Likidite sağlayıcısı **değişim ücreti** ve **ek bir ödül** \(istikrar ücreti kar payından\) ile ödüllendirilir, çünkü buradaki likidite yalnızca kullanıcılara token takası için değil, aynı zamanda tasfiye için Honzon stabilcoin protokolüne de hizmet eder.

## Mandala Test Ağı

### Web DApp ile

#### Mevduat Likiditesi

![Dapp](../../../.gitbook/assets/depositearn_deposit.png)

#### Likidite Çekin

 Not: çekilen miktar, jeton miktarı DEĞİLDİR, ancak belirli bir likidite havuzuna katkınızı yansıtan bir hisse miktarıdır.

![](../../../.gitbook/assets/depositearn_withdraw.png)

#### Ödülü Çekin

 Bunlar, DeX likiditesinin USD'nin istikrarına katkısını tanımak için istikrar ücreti gelirinden ek kar payıdır.

![](../../../.gitbook/assets/depositearn_reward.png)
