# Badger Assistant
The Digg system requires regular updates in order to react to market prices. The process of updating the supply in response to market forces is known as rebasing. This process is designed to occur daily, though the system can operate perfectly fine without it.

## How do we rebase?
Two things need to happen:
- Updated market data reports need to be pushed to the CpiMedianOracle and MarketMedianOracle.
- Rebase needs to be called on the Orchestrator.

The flow of actions within the system looks like this. The 'person' components represent off-chain actions. First, updated data is pushed to the oracles. Then, the rebase can occur.


![Action flow](/images/digg-system.png)

## How do we know when to rebase?
Rebasing needs to happen within a certain time window daily, as defined by the contract parameters.

- The lastRebaseTimestampSec is publicly available from the SupplyPolicy.
- The rebase window time can be calculated from on-chain values.
- inRebaseWindow() can also be called to confirm rebase window.
- The rebase window is short with default parameters, there are only 20 minutes in which it can be called.

## Oracle data preconditions
In order for the rebase to succeed, the cpi & market median oracles must report valid, sufficiently fresh data.

The data providers (the centralized market oracle for MarketMedianOracle, and the ConstantOracle for the CpiMedianOracle) push data to the oracles. These push operations are initiated by external actors.

The ConstantOracle is trustless and can be called by any party. This service will be provided by the Badger Assistant.

Data for the centralized oracle must be pushed by the trusted parties who operate the corresponding Gnosis safe.

The Oracle data must be published some time before the rebase in order to be valid, based on the reportDelaySec parameter. This _minimum_ live time of a report is in addition to the _maximum_ staleness of a report. Oracle reports become stale (are no longer valid for use in rebasing) after 24.5 hours by default. This data should be as fresh as possible when the rebase window opens.

## Parameters Notes
The initialize function in SupplyPolicy sets these parameters:
```
// deviationThreshold = 0.05e18 = 5e16
deviationThreshold = 5 * 10 ** (DECIMALS-2);

rebaseLag = 30,
minRebaseTimeIntervalSec = 1 days;
rebaseWindowOffsetSec = 72000;  // 8PM UTC
rebaseWindowLengthSec = 15 minutes;
```

On the live AMPL system, the following parameters have been changed from defaults
```
rebaseLag = 10,
rebaseWindowOffsetSec = 7200 // 2AM UTC
rebaseWindowLengthSec = 20 minutes
```

The live AMPL system maintains these parameters now. The reduced rebase lag means that the supply snaps 1/10th of the way to the new price target per day, rather than 1/30th. The time of the rebase window as changed, as well as the window for the action (slightly).
___


## How do we update the Geyser calculations?
Geyser calculations are updated anytime anyone does a stake / unstake / claim. They can also be manually updated by anyone by calling updateAccounting(). This assistant can check whether the contracts have been updated once a day, and if it hasn't - can push a manual update.

## Rolling back an invalid oracle calculation

See AMPL incident:
https://github.com/ampleforth/Ampleforth-Wiki/blob/master/incident-reports/2020-03-03-market-oracle.md


