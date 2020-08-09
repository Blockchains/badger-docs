# Governance

The BASE token is governed by the Base DAO, an Aragon DAO with a transferrable governance token called gBASE.

## Configuration

| Parameter | Description | Value |
|-|-|-|
| *Support* | Relative percentage of tokens that are required to vote “Yes” for a proposal to be approved. For example, if “Support” is set to 50%, then more than 50% of the tokens used to vote on a proposal must vote “Yes” for it to pass. | 50% |
| *Minimum Approval* | Percentage of the total token supply that is required to vote “Yes” on a proposal before it can be approved. For example, if the “Minimum Approval” is set to 20%, then more than 20% of the outstanding token supply must vote “Yes” on a proposal for it to pass. | 20% |
| *Vote Duration* | Length of time that the vote will be open for participation. For example, if the Vote Duration is set to 7 days, then token holders have 7 days to participate in the vote. | 7 days |

## Apps
BASE DAO uses the following Apps:

- **Voting**: Used to create and participate in votes. Votes can be linked to an action, such as minting gBASE or transferring funds, or be purely informative.

- **Tokens**: Manages the supply and distribution of gBASE.

- **Finance**: Manages the organization's financial assets, including ETH and ERC20s.

- **Token Request**: Mint gBASE in exchange for payment. If the request is rejected, the user would receive their payment back and if it is approved the payment would be sent to the organization and new gBASE would be minted to the user.

- **Agent**: Enables the organization to interact directly with any other smart contract on Ethereum. For example, adding liquidity to a Uniswap or Balancer pool.

## Voting

Users can create and vote on Finance, Token, and Token Request votes through the Aragon App Panel.

Agent votes can only be created through the Aragon App Console:

- Syntax
  - `act/agentAddress/contractAddress/method(type: value)`

- Example
  - `act/0x77df6ca4cc96d16edc7858cfc00f70fdc98bb027/0xe96c9851773ec7adcb6a155c7d4acf19a4ede7ae/vote(uint256: 10, bool: true, bool: false)`

- [Documentation](https://github.com/aragon/aragon/blob/master/docs/CONSOLE.md#act)
