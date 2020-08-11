## System Roles 
#### Deployer 🏗
This is an EOA that handles the initial deploys and wiring up of the system, using the deploy script. It trasfers ownership of everything to the DAO Agent after initialization is complete.

#### DAOAgent 🤖
This is the DAO contract that interacts with other contracts. It is the 'avatar' of the DAO to the outside Ethereum world. It will be the owner of the system.

#### DAOFinance 💵
This is the DAO contract that handles financial transactions of ETH and ERC20s. All of the initial BASE tokens are given to this address.


## Deploy Core
#### Prepare the config for deployment script
This will specify the initial parameters of the system

#### Deploy DAO via Aragon UI

#### Deploy BaseToken & SupplyPolicy via OZ CLI from ampl/uFragments repo
- Before deploy, ensure the proper token name and symbol are set in contract (They are hardcoded)
- Initialize BaseToken to the deployer address
- Do not initialize SupplyPolicy, it will be taken care of by deploy script

#### Run deploySystem() script
This will deploy the...
- Orchestrator
- MarketMedianOracle
- CpiMedianOracle
- ConstantOracle

And configure these contracts & the SupplyPolicy The MarketMedianOracle will have no data source initially.

#### Run the tranferOwnership() script
This will transfer ownership of all contracts from the **Deployer** to the **DAO Agent**. All the $BASE tokens will be given to the **DAO Finance**.

#### Test the parameters using confirmRebaseParams() script
This will ensure all parameters of the system are what we expect so far

## Deploy Pools
#### Deploy Uniswap Pool
Use the **UniswapV2Factory** to create a WETH-BASE Pair. The created UniswapV2Pair contract is *also* the LP token.

#### Deploy Geyser using deployGeyser() script
This will deploy the Token Geyser. The stakingToken will be the Uniswap LP token, the distributed token will be the gBase Token (governance token of DAO). The rest of the parameters will come from the config.

#### Test the geyser parameters using confirmGeyserParams() script


## Bringing Users into the system
The system is 'live' once BASE and WETH are added to the uniswap pool. At that point, anyone can buy BASE tokens and stake the LP tokens in the Geyser to farm gBase.

Before this happens, a few things should be configured

#### Configure Oracles w/ Data sources
Initial oracles will be centralized, with Chainlink integration hopefully down the line.

#### Allow contributors to request gBase
Using the TokenRequestApp of the DAO, contributors can request gBase tokens for ETH. This ETH will be used to seed initial liquidity in the Uniswap Pool, along with the BASE tokens.

(Note: Ensure ETH goes to the DAO Finance app)

#### Deploy Liquidity
Send the LP tokens back to the individual contributors pro-rata via proposals, rather than stake it in Geyser directly. Contributors can then stake their LP tokens to farm gBase individually.

