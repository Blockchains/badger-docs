# Badger DAO Deployment
The Badger system has a number of moving parts, and requires a fairly elaborate setup. This setup is handled by the [deploy script](https://github.com/Badger-Finance/badger-deploy).

These include deploying and configuring:
- [Badger DAO](https://github.com/Badger-Finance/badger-dao)
- [Distribution Geysers](https://github.com/Badger-Finance/badger-geyser) (which are a slightly modified version of the Ampleforth Token Geyser)
- [Digg Core system](https://github.com/Badger-Finance/digg-core)
- [Digg Oracles](https://github.com/Badger-Finance/digg-oracles)
- TimeLock contracts to lock up a portion of $BADGER and $DIGG tokens for the DAO
- Additional required infrastructure, if on a local instance (Uniswap, Gnosis Safe, ENS, AragonPM, etc...)

In the code, the segments of the deployment process are shown clearly in the [deploy system file](https://github.com/Badger-Finance/badger-deploy/blob/develop/deploy/deploySystem.ts), with the initial configuration coming from the [config file](https://github.com/Badger-Finance/badger-deploy/blob/develop/deploy/badgerConfig.ts).

## System Roles 
#### Deployer 🏗
This is an EOA that handles the initial deploys and wiring up of the system, using the deploy script. It transfers ownership of all owned contracts to the DAO Agent after initialization is complete.

#### DAOAgent 🤖
This is the DAO contract that interacts with other contracts. It is the 'avatar' of the DAO to the outside Ethereum world. It will be the owner of the Digg system, distribution geysers.

#### DAOFinance 💵
This is the DAO contract that handles financial transactions of ETH and ERC20s. It provides a nicer interface for these common actions than the DAOAgent. The DAOAgent is able to utilize funds in the DAOFinance to interact with external contracts.

## [Local only] Deploy Infrastructure
External components used by the contracts are deployed, such as the Uniswap factory & router, Gnosis safe master copy, ENS, AragonPM, Staking assets etc..

## [Public network] Connect Infrastructure
Existing external components used by the contracts are connected to, using addresses specified in the config fig.

## Deploy DAO 
The DAO is deployed via the Badger DAO template. This will deploy the initial set of Aragon apps, including the DAOAgent and DAOFinance. The initial supply of BADGER is minted to the deployer, to be placed into the various staking & locking contracts. 

>⚠️ Note that once the Deployer sends their governance tokens and no longer controls >50% of the voting rights, actions cannot be taken immediately and must wait for the DAO voting period (1 week)

## Deploy & Initialize Digg System
The Digg Core and Digg Oracles are deployed, initialized, and configured.

## Deploy Liquidity Pools
Uniswap pools for WETH/BADGER and WETH/DIGG are created using the UniswapV2Factory. No liquidity is provided at deploy time.

A Balancer pool for WETH/BADGER is deployed, and provided with the minimum possible liquidity as per the [BPool](https://github.com/balancer-labs/balancer-core/blob/master/contracts/BPool.sol) requirements.

## Deploy Distribution Geysers 
Distribution Geysers are deployed and appropriate amounts of tokens are locked within, as per the configuration.

## Deploy Token Timelocks 
Distribution Geysers are deployed and appropriate amounts of tokens are locked within, as per the configuration.

## Confirm Deployment Parameters
We're ready to go:
This will ensure all parameters of the system are what we expect
The geyser parameters will be tested using confirmGeyserParams() function

#### Transfer ownership to DAO
This will transfer ownership of all contracts from the **Deployer** to the **DAO Agent**. 

## Final Checks
Confirm that the ownership of contracts is successfully transferred. (Including the ProxyAdmin for the upgradable contracts, uFragments and uFragmentsSupply)

# The Complete Badger & Digg Systems

