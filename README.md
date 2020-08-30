# Badger Finance
Badger Finance is a DAO focused on enhancing the Bitcoin ecosystem on Ethereum. 

The DAOs debut product is Digg, a BTC-pegged elastic supply currency.

# Overview
![Architecture](/images/badger-architecture.png)

- [**Badger DAO**](./Governance.md) The governance of Badger Finance is managed via an Aragon DAO.

- [**Token Distribution**](./Distribution.md) The Badger governance token ($BADGER) and the Digg token ($DIGG) will be initially distributed via staking pools. The launch will be fair, with no pre-mint.

- [**Digg Core**](./DiggCore.md) Digg is a BTC-pegged elastic supply currency, based on the Ampleforth protocoll

- [**Digg Oracles**](./DiggOracles.md) External
market data for the Digg system is provided via Oracles.

- [**Updater Service**](./Assistant.md) External service to ensure system updates (oracle date, rebases) occur when appropriate.

## System Overview (w/ Upgradability Notes)
![Deploy](/images/rebase-upgrades.png)

## Further reading
![Upgradability](/images/rebase-upgrades.png)

- [Deployment scripts](https://github.com/Badger-Finance/badger-deploy)
- [System upgrade notes](/Upgrade.md)
