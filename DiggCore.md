# Digg Core 
The Digg Core is based on the [Ampleforth](https://www.ampleforth.org/) system. At a smart contract level, it is composed of an [Orchestrator](https://github.com/Badger-Finance/digg-core/blob/master/contracts/Orchestrator.sol), [uFragmentsPolicy](https://github.com/Badger-Finance/digg-core/blob/master/contracts/UFragmentsPolicy.sol), and [uFragments](https://github.com/Badger-Finance/digg-core/blob/master/contracts/UFragments.sol).

![Core](/images/digg-core.png)

- Orchestrator: the entry point of the rebase actions, can forward notifications of the rebase to other contracts
- uFragmentsPolicy (i.e. SupplyPolicy): Consumes data from the Oracles, to determine the market value of Digg token. Has unique permission to inform the Digg token about this.
- uFragments: Core Digg token. Maintains balances / approval data as per ERC20, and modulates it's displayed supply as per Ampleforth mechanics

