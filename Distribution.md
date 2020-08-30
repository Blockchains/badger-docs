# Token Distribution
There will be a 21 day staking period in which $BADGER tokens are released, followed by a 21 day staking period in which $DIGG tokens are released.

Within each staking period, there will be series of tranches to distribute the token, each lasting 3-7 days. The amount of tokens released per day will be weighted towards the front, with less tokens being distributed per day as the staking period progresses. 

However, each tranche will add new assets that can be staked. More details on staking pools and tranches can be found below.

The distribution mechanics are realized in code via the deployment [config](https://github.com/Badger-Finance/badger-deploy/blob/develop/deploy/badgerConfig.ts) file.


# BADGER Distribution
There will be a total of 21 million $BADGER tokens. 

- Half of the $BADGER total supply will be allocated throughout various staking pools over a period of 21 days..
- The remaining half of $BADGER tokens will be locked, and given to the DAO itself after thirty days. The DAO governance process will determine how to allocate these tokens. 

### Tranche 1 
- Amount of Badger to unlock = 6M 
- How long = 7 days
- How it unlocks= 1M each day for the 1st 3 days and then 750k per day for the remaining 4 days.
- Assets to stake
    - BADGER_UNISWAP_LP 
    - CRV_sbtc_LP token

### Tranche 2 
- Amount of Badger = 3M
- How long = 7 days
- How it unlocks =  evenly each day over 7 days. 
- New Assets to stake
    - LP_ BAL_ CRV_ BAL_ RENBTC pool
    - CRV_LP_renbtc
    - BAL_LP_wbtc_ WETH
    - Wbtc
    - RenBTC
    - Bonus=  If you stake UNISWAP_ LP_ Badger you get 2x the BADGER compared to the other assets.

Looking into introducing the ability to earn 2 assets when staking. If you stake RENBTC you earn BADGER and REN. ** STILL NOT CONFIRMED**

### Tranche 3 
- Amount of Badger = 1.5M 
- How long = 7 days
- How it unlocks =  evenly each day over 7 days. 
- NEW Assets to stake= 
    - CREAM
    - Sbtc
    - Yycurv
    - Yalink
    - LEND
    - LP_UNI_AMPL_weth
    - BAL_LP_BADGER
    - Bonus=  (LP) BAL and UNI pool BADGER you get 2x the BADGER compared to the other assets

# DIGG Distribution
There will be a total of 6250 $DIGG tokens. 

- Half of the $DIGG total supply will be allocated throughout various staking pools over a period of 21 days, starting after the full distribution of $DIGG is complete.
- The remaining half will be locked, to be released to the DAO after 30 days as per the $BADGER timelock.

### Tranche 1  
- Amount of DIGG= 1625
- How long = 7 days
- How it unlocks =  270 digg each day for first 3 days then 203.75 each day - for remaining 4 days. 
- Assets to stake
    - BADGER
    - LP_UNI_ BADGER
    - LP_BAL_BADGER
    - Bonus=  Stake BADGER you get 2x the DIGG compared to the other assets.

### Tranche 2 
- Amount of DIGG= 1000
- How long = 7 days
- How it unlocks =  evenly each day over 7 days. 
- New Assets to Stake:
    - Ampl
    - Xampl
    - Based
    - UNI_LP_DIGG
    - RenBTC
    - CREAM
    - Bonus= Stake UNI_LP_DIGG OR Badger you get 2x the DIGG compared to the other assets.

### Tranche 3 
- Amount of DIGG = 500 
- How long = 7 days
- How it unlocks =  evenly each day over 7 days. 
- New Assets to stake: 
    - Sbtc
    - Wbtc
    - Yycurv
    - Yalink
    - LEND
    - LP_ BAL_ CRV_ BAL_ RENBTC pool
    - Bonus= Stake UNI_LP_DIGG OR Badger you get 2x the DIGG compared to the other assets..
