# Security Notes & Concerns

## Flow of Funds
- Digg & Badger tokens are placed in the distribution geysers.
- External funds are placed in the distribution geysers. 
- Digg & Badger tokens are released from the distribution geysers to users.
- External funds are withdrawn from the distribution geysers
- After the staking period, large portions or Digg and Badger are released from time lock contracts to the DAO.

## Scenario: Catastrophic loss of funds 🚨
The distribution geysers are the only place where ETH & external tokens are pooled. This is the place to watch for the worst of all possible outcomes.

### Properties to Maintain 👾
- The Geyser must not allow users to withdraw funds that they did not deposit.
- The Geyser must allow users to withdraw their own depositied funds, in full.
- The Geyser must allow users to claim the correct amount of rewards token in relation to their desposited share.

Governance Collusion?
- If the Geysers were upgradable, an early colluding majority of Goverance holders could decide to upgrade the Geysers and steal the staked funds before some users noticed (Solution: The Geysers are NOT upgradable)

## Scenario: Issues w/ Timelocked funds
A very sizable percentage of Digg and Badger tokens are placed within OpenZeppelin TimeLock contracts. If these were to fail, it could have a major effect on the stability of the system.

### Properties to Maintain 👾
- Only the DAO must be able to withdraw the locked tokens.
- The locked tokens must be withdrawable in full.
- The locked tokens must only be able to be unlocked after the proper time.

## Scenario: Incorrect allocation of Badger and Digg from distribution pools
Math errors in these contracts could lead to unexpected results in the distribution of tokens, potentially diminishing the reputation of the project and leading to instability in the nascent system.

## Governance Attacks
These attacks are considered unlikely to succeed, because of the public nature of everything happening on the DAO. A prerequisite is a mega-whale / colluding cartel providing sufficient voting power to make a proposal instantly pass in the DAO. This 'support threshold' could be made impossibly high in the mature system. This would prevent 'insta-passing' from ever happening, so there would be a 7 day warning for any action that occurs. However, this prevents people rallying around emergency actions. The vote duration could also be revisited.

* **Digg Mint**: A colluding majority of goverance holders upgrades the DIGG contract to increase the supply, or transfer supply from other users to the colluders. They attempt to dump it on the market before the attack becomes sufficiently known.

* **Badger Mint**: A colluding majority of goverance holders re-enables token minting on the DAO, and increases the supply of badger in order to take 

* **Sneaky Contract Call**: An action is taken on a smart contract that is intended to perform a malicious action, such as draining treasury from the DAO. The called contract is designed in such a way to attempt to disgiuse the action through obfuscation. An alternative is a complex series of calls that results in the fund transfer.
