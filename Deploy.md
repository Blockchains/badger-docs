## System Roles 
#### Deployer 🏗
This is an EOA that handles the initial deploys and wiring up of the system, using the deploy script. It trasfers ownership of everything to the DAO Agent after initialization is complete.

#### DAOAgent 🤖
This is the DAO contract that interacts with other contracts. It is the 'avatar' of the DAO to the outside Ethereum world. It will be the owner of the system.

#### DAOFinance 💵
This is the DAO contract that handles financial transactions of ETH and ERC20s. All of the BASE tokens are initially given to this address.

## Deploy Core
The deployment script currently involves some manual phases and some automated parts for speed of development, subject to further automation.

#### Manual step: Deploy DAO 

via Aragon UI:
[Rinkeby](https://rinkeby.aragon.org/#/)
[Mainnet](https://aragon.org/#/)

Or Aragon console

- Determine how many gBase should be distributed total (21,000,000 total for early contributors + Geyser)
- Subtract the early contributor distribution from the total, mint this gBase to the Deployer initially. The majority of this will be sent to the Geyser.
- Minimum voting threshold should be 10%

>⚠️ Note that once the Deployer no longer controls >50% of the voting rights, actions cannot be taken immediately and must wait for the DAO voting period (1 week)

Take note of the addresses of the Agent app, Finance app, and governance token.

#### Manual step: Deploy BaseToken & SupplyPolicy via OZ CLI
- Before deploy, ensure the proper token name and symbol are set in contract (They are hardcoded)
- Do not initialize SupplyPolicy, it will be taken care of by deploy script

Add these contract addresses to the config.ts file.

#### Manual step: Deploy RebaseBtcBaseOracle
Deploy a Gnosis Multisig on Rinkeby w/ desired keys.
Add these contract addresses to config.


### Run deploySystem() script
Note that everywhere the script is involved, those actions could also be taken manually if desired

#### Core System
This will deploy the...
- BaseToken
- SupplyPolicy
- Orchestrator
- MarketMedianOracle
- CpiMedianOracle
- ConstantOracle
- Centralized Market Oracle
    - (This oracle is a Gnosis multisig, and will be operated pro-bono by trusted early adopters.)

Once the system is deployed, the deployed.json file will be updated with the contract addresses (rinkeby.json for rinkeby).
After deployment, it will then configure these contracts according to the config.

- Initialize BaseToken to the deployer address
- Initialize SupplyPolicy (owned by deployer address, managing supply for BaseToken)

#### Pool & Geyser
Uses the **UniswapV2Factory** to create a WETH-BASE Pair. The created UniswapV2Pair contract is *also* the LP token.

#### Test the parameters using confirmRebaseParams() script
We're ready to go:
This will ensure all parameters of the system are what we expect
The geyser parameters will be tested using confirmGeyserParams() function

## Manual DAO Actions: Bringing Users into the system

#### Transfer all BASE tokens
The Deployer will deposit all BASE tokens to the DAO Finance App through the Aragon UI. This will register the BASE token in the UI

#### Allow contributors to request gBase
Using the TokenRequestApp of the DAO, contributors can request gBase tokens, and optionally offer ETH for this request. This ETH will be used to seed initial liquidity in the Uniswap Pool, along with the BASE tokens.

#### Deploy Liquidity
Use the DAO Agent console to put ETH & BASE into the Uniswap Pool.

##### Approve Uniswap Router to use BASE tokens.
```
act/<agent>/<baseToken>/approve(address: <uniswapV2Router>
 , uint256: <baseAmount>)
```

##### Add liquidity to Uniswap Pool via router.
```
act/<agent>/<uniswapV2Router>/addLiquidityETH(address: <baseToken>, uint256: <baseAmount>, uint256: 0, uint256: 0, address: <agent>, uint256: <deadline>)/<ethAmount>
```

The LP tokens will be sent back to the DAO. It's presumed the DAO will not stake it's own LP tokens in Geyser to harvest gBase.

#### Send gBase to Geyser
The Deployer now sends the bulk of gBase (75% of total supply) to the Geyser. Once the gBase is deployed to the geyser, it will have a 75% voting capacity.
There's a 20% threshold, so initially the DAO will need high participateion to get things done.

>⚠️ This needs to be done after the liquidity provision actions, because once the Deployer no longer controls >50% of the voting rights, actions cannot be taken immediately and must wait for the DAO voting period (1 week)

If it's ok to wait a week for Liquidity & Geyser to be live, these operations can happen via the DAO in a more trustless manner.
Unfortunately the DAO cannot change it's voting period after Deploy.

#### Run the tranferOwnership() script
This will transfer ownership of all contracts from the **Deployer** to the **DAO Agent**.

## Final Checks
Send the ProxyAdmin for the upgradable contracts (BaseToken, SupplyPolicy) to the DAO Agent!

//TODO Aragon Command Tempales
//TODO Diagrams


