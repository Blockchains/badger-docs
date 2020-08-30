# Market Oracle

## Market Data
The Market oracle suggesting BASE/BTC exchange rate will initially be operated by a trusted party, with a chainlink integration pending.

* The centralized oracle is a Gnosis safe.
* This is a provider of the MarketMedianOracle.
* The multisig is 1 of N, with keys belonging to trusted participants.
* The oracle server has one of the keys, calculates BTC/BASE Price, and hits pushReport() on the MedianOracle by proposing it through the Gnosis Multisig. (It is instantly executed because it's 1 of N).

## CPI Data
- The CPI oracle from Ampleforth is effectively unused. There is a custom ConstantOracle that always returns 1 on update.