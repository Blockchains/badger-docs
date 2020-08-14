# Rebase Assistant

## How do we rebase()?
Two things need to happen:
- Push updated reports to CpiMedianOracle and MarketMedianOracle.
- Call rebase() on Orchestrator

## How do we know when to rebase()?
- The lastRebaseTimestampSec is publicly available from the SupplyPolicy
- inRebaseWindow() can be called to confirm rebase window
- The rebase window is short, there are only 20 minutes in which it can be called
-

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

The live AMPL system has these parameters

## How do we update the Geyser calculations?

## Rolling back an invalid oracle calculation

See AMPL incident:
https://github.com/ampleforth/Ampleforth-Wiki/blob/master/incident-reports/2020-03-03-market-oracle.md


