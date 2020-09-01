# Upgrade Paths

![Upgrade](/images/badger-upgrades.png)

## Digg Core
**uFragments** & **uFragmentsSupply** use OZ Proxy + Logic, implementation can be upgraded by DAO. 

Every other contract in the Digg system can be changed via admin function, ultimately starting from these two contracts.

Changed in **uFragmentsSupply**:
* MarketOracle
* CPIOracle
* Orchestrator

Each oracle can set it's data sources via admin function.

## Distribution Pools (Geysers)
The Geysers are not upgradable, this is the intent of the system - it's a promise of releasing tokens over time according to the preset schedule. 
