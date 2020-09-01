# Badger DAO
The Badger DAO is based on the Aragon [company template](https://github.com/aragon/dao-templates/tree/master/templates/company)

## Configuration
| Parameter | Description | Value |
|-|-|-|
| *Support* | Relative percentage of tokens that are required to vote “Yes” for a proposal to be approved. For example, if “Support” is set to 50%, then more than 50% of the tokens used to vote on a proposal must vote “Yes” for it to pass. | 50% |
| *Minimum Approval* | Percentage of the total token supply that is required to vote “Yes” on a proposal before it can be approved. For example, if the “Minimum Approval” is set to 20%, then more than 20% of the outstanding token supply must vote “Yes” on a proposal for it to pass. | 10% |
| *Vote Duration* | Length of time that the vote will be open for participation. For example, if the Vote Duration is set to 7 days, then token holders have 7 days to participate in the vote. | 7 days |

## Apps
Badger Finance DAO uses the following Aragon Apps:

- **[Voting](https://github.com/aragon/aragon-apps/tree/master/apps/voting)**: Used to create and participate in votes. Votes can be linked to an action, such as minting BADGER or transferring funds, or be purely informative.

- **[Tokens](https://github.com/aragon/aragon-apps/tree/master/apps/token-manager)**: Manages the supply and distribution of BADGER.

- **[Finance](https://github.com/aragon/aragon-apps/tree/master/apps/finance)**: Manages the organization's financial assets, including ETH and ERC20s.

- **[Agent](https://github.com/aragon/aragon-apps/tree/master/apps/agent)**: Enables the organization to interact directly with any other smart contract on Ethereum. For example, adding liquidity to a Uniswap or Balancer pool.

### App Panel
Users can create Finance, Token, and Token Request votes through the Aragon App Panel.

### Notes on configuration
The initial circumstances of the DAO are noteworthy in that there is a large initial supply of governance tokens minted, which are [locked & distributed over time](./Distribution.md). In Aragon DAOs, the 'canonical' way of distributing governance is to mint new tokens for participants entering the system as they join.

The effect of this initial minting is that during the first days of the DAO it will not be possible to pass actions via the governance process, as a vast majority of the governance weight will be locked. At least **Minimum Approval** % of tokens must be _distributed and used to vote_ in order for proposals to pass within the system with a relative majority. Proposals will not be able to _immediately_ pass until the **Support** threshold is able to be used within voting, and is used. This means that every proposal in the initial days of the system must pass via relative majority, and be subject to a 7 day waiting period before the action occurs.

In order to alleviate the duration of this effect, the **Minimum Approval** threshold has been reduced to 10% (from 20% default)

In the first thirty days, before the remaining 50% of tokens is released from the timelock, it will effectively take 20% of token holders to reach the minimum approval, and 100% to instantly pass a proposal. 

### Console
The Aragon Console can be used to propose arbitrary smart contract actions via the Aragon Agent.

- Syntax
  - `act/agentAddress/contractAddress/method(type: value)`

- Example
  - `act/0x77df6ca4cc96d16edc7858cfc00f70fdc98bb027/0xe96c9851773ec7adcb6a155c7d4acf19a4ede7ae/vote(uint256: 10, bool: true, bool: false)`

- Documentation
  - [Console](https://github.com/aragon/aragon/blob/master/docs/CONSOLE.md#act)
  - [Interacting with Aragon Agent](https://hack.aragon.org/docs/guides-use-agent#interacting-with-aragon-agent)
 

### What actions will the DAO want to take
- Providing liquidity in various pools
- Transferring tokens (this can also be handled via the Finance app in a more user-friendly way)