# Upgrade Paths

## Rebase Core
**uFragments** & **uFragmentsSupply** use OZ Proxy + Logic, implementation can be upgraded by DAO. 

Every other contract in the system can be changed via admin function, ultimately starting from these two contracts.

Changed in **uFragmentsSupply**:
* MarketOracle
* CPIOracle
* Orchestrator

Each oracle can set it's data sources via admin function.

## Rebase Geyser
The Geyser is not upgradable, this is the intent of the system - it's a promise of releasing tokens over time according to the preset schedule. 

However, given that the token itself & rest of the system can be changed it does not actually provide any decentralization guarentee.

Full upgradability could be added by implementing OZ proxy + logic split w/ DAO ownership. This would invalidate the audited status of the contract.
* Inhereit Initializable
* constructor() -> initialize()