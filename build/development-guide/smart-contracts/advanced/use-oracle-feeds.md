# Oracle Geribildirimlerini Kullanın

Acala'nın [Open Oracle Gateway](https://wiki.acala.network/learn/basics/oracle), Acala'nın DeFi optimize edilmiş oracle altyapısından yararlanarak ve Acala, Polkadot'ta herhangi bir DApp'e hizmet vererek, Acala ağında birden fazla oracle'ın kurulmasına izin verir. Örneğin Kusama ve diğerleri. Açık Oracle Ağ Geçidi, Hizmet Kalitesini sağlar, yani oracle işlemleri sistem işlemleri olarak sınıflandırılır ve bir bloğa dahil edilmeleri garanti edilir. [Oracle Temelleri](https://wiki.acala.network/learn/basics/oracle) bölümünde daha fazlasını okuyun.

Bu önceden derlenmiş sözleşme, Acala EVM içinde bulunan çeşitli varlıklar için çeşitli fiyat beslemelerinin sorgulanmasını sağlar. Şu anda "getPrice" yöntemi, belirli bir varlık için toplu fiyatı döndürür. Daha fazla fiyat besleme seçeneği de sunulabilir.

Sözleşme kaynak kodu burada bulunmaktadır: [evm-examples/oracle](https://github.com/AcalaNetwork/evm-examples/tree/master/oracle).

> _**NOT:**_ EVM oyun alanına sahip yerel bir Acala düğümü çalıştırıyorsanız, tüm belirteçler için 0 fiyatına sahip olmak istersiniz.

## Sözleşme Adresi

Oracle sözleşme adresi: `0x00000000000000000000000000000000000000000807`

## Sözleşme Yöntemleri
```javascript
// Get the price of the currency_id.
// Returns the (price, timestamp)
function getPrice(address token) public view returns (uint256, uint256);
```

## Çalışma Alanında Deneyin

[EVM Playground](https://evm.acala.network/#/execute) - "Yürütme sekmesi"ne gidin.

'Oracle Fiyat Beslemesi' sözleşmesini bulun ve 'Yürüt' Düğmesine tıklayın.

![](../../../../.gitbook/assets/screen-shot-2021-02-03-at-12.55.05-pm%20%281%29.png)

`token: address` alanına, ilgilenilen jeton için ERC20 sözleşme adresini \(örnek DOT adresinde `0x000000000000000000000000000000000000000000000802`\ olarak) girin. DOT, RenBTC ve XBTC için beslemeler mevcuttur.

Mevcut tüm jeton sözleşme adreslerine [buradan](https://wiki.acala.network/build/development-guide/smart-contracts/advanced/use-native-tokens) ulaşabilirsiniz.

![](../../../../.gitbook/assets/screen-shot-2021-02-03-at-12.27.16-pm.png)

"Ara" Düğmesine tıklayın, "Arama sonuçları" fiyat ve zaman damgasını göstermelidir.

![](../../../../.gitbook/assets/screen-shot-2021-02-03-at-12.27.29-pm.png)
