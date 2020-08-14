# Overview
The Rebase protocol is based on the Ampleforth protocol, with the following high level changes:

- The BASE token value is pegged to BASE/BTC exchange rate, rather than BASE/USD
- The protocol is operated by a DAO, rather than by a centralized team
- The Geyser distributes gBase (DAO governance tokens), rather than BASE

### Oracles
- CPI oracle is effectively unused. There is a custom ConstantOracle that always returns 1 on update
- Market oracle suggesting BASE/BTC exchange rate will be centralized at first, with chainlink integration pending.

![Deploy](/images/rebase-upgrades.png)

// TODO: Add new images