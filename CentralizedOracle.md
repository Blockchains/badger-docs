# Centralized Oracle
* The on chain "oracle" address a Gnosis multisig
* This is a provider of the Market MedianOracle
* The multisig is 1 of N, with keys belonging to trusted participants
* The oracle server has one of the keys, calculates BTC/BASE Price, and hits pushReport() on the MedianOracle by proposing it through the Gnosis Multisig. (It is instantly executed because it's 1 of N)