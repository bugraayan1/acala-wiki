# Zincir Üzerinde Zamanlayıcıyı Kullanma

Belirli bir akıllı sözleşmeyi yürütmek üzere yinelenen bir çağrı planlamak için zincir üstü zamanlayıcı sözleşmesini kullanabilirsiniz. Zincir üstü otomatik zamanlayıcı için kullanım örnekleri hakkında daha fazla bilgi edinin [buradan](https://wiki.acala.network/learn/basics/acala-evm/acala-evm-composable-defi-stack/on-chain-scheduler ).

Sözleşme kaynak kodu [burada](https://wiki.acala.network/learn/basics/acala-evm/acala-evm-composable-defi-stack/on-chain-scheduler).

Not: "min_delay", planlanmış arama çağrılmadan önceki mevcut bloklardan sonraki minimum blok sayısıdır. yani Pass 0, sonraki blokta çağrılması planlanacağı anlamına gelir. Blok 10'da "min_delay = 5" ile "scheduleCall" çağrılması, çağrıyı "10 + 1 + 5 = 16" bloğunda programlayacaktır. Blok doluysa veya çok fazla başka zamanlanmış görev varsa, zamanlanmış çağrı blokta yeterli alan kalana kadar sonraki bloklara ertelenebilir..

## Sözleşme Adresi

ScheduleCall sözleşme adresi: `0x0000000000000000000000000000000000000808`

## Sözleşme Yöntemleri

```javascript
// Schedule call the contract.
// Returns the task_address(block_number, index).
function scheduleCall(
  address contract_address, // The contract address to be called in future.
  uint256 value, // How much native token to send alone with the call.
  uint256 gas_limit, // The gas limit for the call. Corresponding fee will be reserved upfront and refunded after call.
  uint256 storage_limit, // The storage limit for the call. Corresponding fee will be reserved upfront and refunded after call.
  uint256 min_delay, // Minimum number of blocks before the scheduled call will be called.
  bytes memory input_data // The input data to the call.
)
public
returns (uint256, uint256); // Returns a task id that can be used to cancel or reschedule call.
```

## Örnek

[İşte](https://github.com/AcalaNetwork/evm-examples/tree/master/scheduler) zamanlayıcıyı kullanan bir yinelenen ödeme sözleşmesi örneği.

## Eğitim

Acala EVM'de temel bir otomatik abonelik sözleşmesi yazmak ve dağıtmak için bu eğitimi izleyin.
