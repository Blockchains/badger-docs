# Contracts
The Rebase system leverages code from a number of repos. The pre-compiled artifacts of contracts are included in the rebase-contracts deployment repo.

## AMPL Core
https://github.com/ampleforth/uFragments

Used contracts:
- UFragments (for BaseToken)
- UFragmentsSupply (for SupplyPolicy)
- Orchestrator

> Note that the UFragments needs to be modified to replace ERC20 name & symbol with Rebase and BASE, because these are hardcoded in the contract
___
## AMPL Oracles
https://github.com/ampleforth/market-oracle

Used contracts:
- MedianOracle (for market & cpi oracles)
___
## AMPL Geyser
https://github.com/ampleforth/token-geyser

Used contracts:
- TokenGeyser

> Note in Rebase, gBase governance tokens are distributed from the Geyser rather than the BASE token
___
## Rebase Custom Oracles
https://github.com/Rebase-Finance/rebase-oracles/

The only piece of custom code in the system, this oracle always returns the value '1' to the CPIOracle, as that functionality is unused for a BTC-based currency.

Used contracts:
- Constant Oracle
___
## Uniswap Core & Periphery

https://github.com/Uniswap/uniswap-v2-core

https://github.com/Uniswap/uniswap-v2-periphery/

The system creates a uniswap pool, interacting with the uniswap v2 system


___
## Aragon DAO
https://github.com/aragon/aragonOS

The system is managed via an Aragon DAO
___
## Gnosis Multisig
Used as on-chain portion of centralized oracle

https://github.com/gnosis/MultiSigWallet