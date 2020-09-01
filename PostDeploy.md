# Badger Actions
Once the system is deployed and 30% of the total Badger tokens in the pools are distributed, the DAO is capable of governance.

## Claiming tokens from timelock for DAO
The locked $BADGER and $DIGG tokens in the TimeLock contracts can be claimed by the DAO after the thirty day lock-up period via standard proposal.

A proposal to the DAOAgent to call release() on the respective TimeLock contracts must be created and passed. [(contract code)](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/token/ERC20/TokenTimelock.sol#L58)