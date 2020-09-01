# Digg Oracles
The purpose of oracles in the Digg system is to track the market price of Digg relative to Bitcoin, and adjusts the Digg supply to maintain it's peg.

The market median oracle is the ultimately 'source of truth' for this data.

The median oracle is named as such because it can take in multiple sources for the same data, and will report the median of the values as the official value.

The implmentation used is the [Ampleforth median oracle](https://github.com/ampleforth/market-oracle)

## Data Sources
Initially, A centralized oracle, represented on-chain by a Gnosis safe, provides data to the marketMedianOracle. The trusted operators of this centralized oracle will calculate the TWAP (24-hour weighted average price) of Digg relative to BTC off-chain and submit this data.

New data sources, beyond the centralized oracle, are intended to be added to the market median oracle over time. A chainlink integration is a likely next step.

## CPI Oracle
In addition to the **marketMedianOracle**, the **cpiMedianOracle** plays a role in understanding the market value of Digg. This oracle is used in the Ampleforth system to track the consumer price index in order to understand the relative purchasing power of a USD over time. In Digg, as BTC is the peg rather than a 2019 USD, the CPI Oracle is effectively unused. Rather than modify the audited Ampleforth code, it was considered perferable to 'disable' this functionality by having the CPI oracle always return "1".

A trustless [ConstantOracle](https://github.com/Badger-Finance/digg-oracles/blob/master/contracts/ConstantOracle.sol) is deployed and used as a data provider to provide this static information to the cpiMedianOracle.

## System Overview
![Oracles](/images/badger-oracles.png)

- MarketMedianOracle: the entry point of the rebase actions, can forward notifications of the rebase to other contracts
- CpiMedianOracle: Unused in the Digg system, always returning one
- Centralized Oracle: External,trusted service that publishes market data to the MarketMedianOracle via a Gnosis safe
- ConstantOracle: Trustless Oracle that always returns 1 to the CpiMedianOracle

## Centralized Market Oracle Details
* The centralized oracle is a Gnosis safe.
* The multisig is 1 of N, with keys belonging to trusted participants.
* The oracle server has one of the keys, calculates BTC/BADGER Price, and calls pushReport() on the MedianOracle by proposing it through the Gnosis safe. (It is instantly executed because it's 1 of N).
* The remaining N-1 keys are used for backup purposes, and to fix incorrect data pushes from the server.