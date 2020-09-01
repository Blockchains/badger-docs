## Badger Distribution
A series of BadgerGeyser contracts, organized into tranches, with parameters set in the deployment config file.
Each one has a specific start time and duration, defined by it's single UnlockSchedule.

## Digg Core
Is composed of an Orchestrator, uFragmentsPolicy, and uFragments as per the Ampleforth system.

- Orchestrator: the entry point of the rebase actions, can forward notifications of the rebase to other contracts
- uFragmentsPolicy (i.e. SupplyPolicy): Consumes data from the Oracles, to determine the market value of Digg token. Has unique permission to inform the Digg token about this.
- uFragments: Core Digg token. Maintains balances / approval data as per ERC20, and modulates it's displayed supply as per Ampleforth mechanics

## Digg Oracles
Is composed of an MarketMedianOracle, CpiMedianOracle, and their data sources.
