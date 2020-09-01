# Badger Finance
Badger Finance is a product-owning DAO, initially focused on enhancing the Bitcoin ecosystem on Ethereum. 
The DAO's debut product is Digg, a BTC-pegged elastic supply currency.

# Overview
The system can be logically divided into the following components

- [**Badger DAO**](./Governance.md) The governance of Badger Finance is managed via an Aragon DAO, with a liquid governance token. This DAO can make arbitrary smart contract calls to interact with external systems.

- [**Badger Distribution**](./Distribution.md) The Badger governance token ($BADGER) and the Digg token ($DIGG) will be initially distributed via staking pools, known as Geysers, after the Ampleforth mechanics they are based on. The launch will be fair, with no pre-mint. A significant portion of $BADGER and $DIGG tokens will be held in timelocked contracts, able to be released back to the DAO after the staking pool distribution.

- [**Digg Core**](./DiggCore.md) Digg is a BTC-pegged elastic supply currency, based on the Ampleforth protocol.

- [**Digg Oracles**](./DiggOracles.md) External market data for the Digg system is provided via Oracles.

- [**Updater Service**](./Assistant.md) External service to ensure required data updates for the Digg system (oracle date, rebases) occur when appropriate.

# System Architecture
![Architecture](/images/badger-finance.png)

## Further reading
- [Deployment scripts](https://github.com/Badger-Finance/badger-deploy)
- [System upgrade notes](/Upgrade.md)
