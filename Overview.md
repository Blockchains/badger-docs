# Overview
The Rebase protocol is based on the Ampleforth protocol, with the following high level changes:

- The BASE token value is pegged to BASE/BTC exchange rate, rather than BASE/USD
- The protocol is operated by a DAO, rather than by a centralized team
- The Geyser distributes gBase (DAO governance tokens), rather than BASE

### Oracles
- CPI oracle is effectively unused. There is a custom ConstantOracle that always returns 1 on update
- Market oracle suggesting BASE/BTC exchange rate will be centralized at first, with chainlink integration pending.

## System Overview (w/ Upgradability Notes)
![Deploy](/images/rebase-upgrades.png)

## Geyser details
![Geyser](/images/geyser.png)

## Rebase action flow
![Rebase](/images/rebase-flow.png)

## Daily system updates
Updates can be made by anyone, though it's expected the early contributors will provide this functionality 

![Update](/images/update.png)