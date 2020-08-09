# Governance

The BASE token is governed by the Base DAO, an Aragon DAO with a transferrable governance token called gBASE.

## Voting configuration:

- Voting Config: TBD, 
- Minimum quorum: TBD, 
- Pass threshold: TBD

## Overview
BASE DAO uses the following Apps:

- **Tokens**: Manages the supply and distribution of gBASE tokens.

- **Finance**: Manages the DAO’s financial assets, including ETH and ERC20s.

- **Voting**: Used to create and participate in votes. Votes can be linked to an action, such as minting tokens or transferring funds, or be purely informative.

- **Token Request** (_Investments_): Request gBASE tokens in exchange for payment. For example, a user may request minting 100 organization tokens in exchange for 100 DAI. The request would require a vote to approve, if the vote is rejected, the user would receive their payment back and if it is approved the payment would be deposited in the organization's vault.

- **Agent** (_Communication_): Enables the organization to interact directly with any other smart contract on Ethereum. For example, adding liquidity to a Uniswap or Balancer pool.

Users can create and vote on Finance, Token, and Token Request votes through the Aragon App Panel. Agent votes can only be created through the Aragon App Console, with the following syntax:

`act/agentAddress/contractAddress/method(type: value)`

Real example:

`act/0x77df6ca4cc96d16edc7858cfc00f70fdc98bb027/0xe96c9851773ec7adcb6a155c7d4acf19a4ede7ae/vote(uint256: 10, bool: true, bool: false)`

You can find more details here: https://github.com/aragon/aragon/blob/master/docs/CONSOLE.md#act