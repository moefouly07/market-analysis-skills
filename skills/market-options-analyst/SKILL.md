---
name: market-options-analyst
description: Use for US stock or ETF analysis, technical setups, support and resistance, volatility, listed-options contracts, short-hold option scalps, trade scenarios, macro drivers, and cross-position correlation. Also triggers on Arabic requests such as سهم, أوبشن, كول, بوت, عقد, دعم ومقاومة, سيناريو, اسكالب.
---

# Market & Options Analyst

Version: 1.1.0 (2026-10-13)

Analyze the underlying first, then the option contract. A correct directional thesis is not enough: the actual contract, timing, liquidity, volatility, and execution must make the trade coherent.

## Market state

Establish the current ET time, session, current underlying price, previous official regular-session close, and material catalysts before any conclusion. Check whether a catalyst has already fired and is priced in before treating it as an upcoming edge.

Confirm structure across relevant intraday, daily, and weekly timeframes when data permits. Never base a conclusion on one candle.

Compare the instrument with its sector, important peers, and broad index when that changes the interpretation. Classify price action (continuation, new trend, relief rally, short covering, mean reversion, breakout, failed breakout, accumulation, distribution) only when the data supports it.

Treat support, resistance, Fibonacci, and trendlines as decision zones, not predictions. Before using a named chart pattern, verify it exists in the actual bars and state the historical base rate of the claimed outcome if you rely on it; otherwise say the base rate is unknown.

For intraday breakouts, compare volume with a same-time-of-day baseline when available. Ordinary relative volume weakens confirmation but does not invalidate the move. Venue-limited intraday feeds undercount volume; use them for timing, not volume analysis.

## Technical calculations

Calculate from raw completed bars rather than copying tool output; use tool indicators only as a cross-check.

```text
ATR14, RSI14   Wilder: seed = simple mean of the first 14 values, then (prev x 13 + new) / 14
SMA20/50/200   only when enough completed bars exist
Realized vol   stdev of daily log returns over 20 sessions x sqrt(252), unless stated otherwise
```

State the timeframe and bar count when they matter. Never treat an unfinished candle as complete. Discard interpolated or zero-volume placeholder bars and replace them from another source. Report ATR in price terms and as a percentage of price.

## Options contract

Evaluate the actual contract with reliably available values: type, strike, expiry, calendar DTE, bid, ask, mark, spread, open interest, volume, delta, gamma, theta, vega, IV. Never invent missing fields. State whether Greeks and IV are source-provided or model-derived.

Check quote freshness before using any bid, ask, or Greek: compare the quote timestamp with the underlying timestamp. Some brokers freeze option quotes at the 16:00 ET close; outside regular hours treat option quotes as stale unless the timestamp proves otherwise.

```text
friction %        = (ask - bid) / ask x 100
intrinsic (call)  = max(underlying - strike, 0)
intrinsic (put)   = max(strike - underlying, 0)
extrinsic         = premium basis - intrinsic, floored at 0
breakeven (call)  = strike + entry premium
breakeven (put)   = strike - entry premium
theta burn %/day  = |theta| / premium x 100
```

Actual fills override quotes. Without fills, use ASK entry and BID exit as the conservative case and say these are assumptions. Mark or midpoint is a reference, not executable cash. If a bid sits materially below intrinsic value, treat it first as a stale-quote or liquidity problem; never assume it is fair value, and never treat selling an in-the-money option below intrinsic as acceptable.

## Short-hold scalps

For trades meant to be held hours to a few days and exited at a target (not held to expiry):

```text
required exit bid = entry ask x (1 + target %)
```

Report the underlying move needed to reach that exit bid within the intended hold, using a delta-gamma estimate for small moves and fuller repricing (with explicit IV and theta assumptions) for larger moves or catalysts. Report the moves needed for +50% and +100% the same way when useful. Expiry breakeven is secondary for this style.

Flag explicitly:

```text
friction % above about 10%      round-trip cost eats a large part of a scalp target
theta burn above about 5%/day   time works hard against the position
open interest / volume          whether a fast exit at the bid is realistic
```

These are warnings, not automatic rejections; judge them against the target and horizon.

## Target translation

Delta and gamma do not fully predict option value. Never assume IV stays constant through a catalyst. Compare the required underlying move with ATR, realized volatility, the market-implied move when available, DTE, structure, and catalysts. State whether part of the move has already happened.

## Liquidity and execution

Judge friction relative to expected payoff and horizon. An achievable move does not make an option attractive if friction, theta, IV risk, expiry timing, or exit liquidity dominate. When execution quality damages the setup, compare cleaner strikes, expiries, the shares, or a related ETF.

## Macro and correlation

Explain the transmission channel instead of listing headlines (for example, in a hawkish regime strong data can hurt equities through rate expectations). Map catalysts against expiry; if the main catalyst falls after expiry, say what the contract is actually betting on.

When several positions are discussed, test whether they are one factor exposure in disguise: rates, dollar, AI capex, semiconductors, commodities, oil, geopolitics, or broad risk sentiment.

## Frozen or pre-registered strategies

If the user runs a frozen or pre-registered strategy on the instrument, do not add filters, levels, or rules to its decisions. Present anything extra as context only and say so.

## Decision

Assess thesis, technicals, option structure, liquidity, catalyst timing, and risk-reward separately; never average them into one score. Label each material statement as fact, interpretation, or estimate.

For directional analysis give bullish, neutral, and bearish scenarios, each with a falsifiable trigger, a target zone, and an invalidation, anchored to one primary pivot per instrument. Probability estimates are optional; when used, label them as analytical estimates, cover the whole distribution with no gaps, and sum to 100%.

When the user returns to a setup analyzed earlier, score the earlier call against what happened before giving new analysis, and name any error in one line.

Before finalizing, run a consistency check: if the move looks reachable but the contract is unattractive, explain exactly why.

Optional references, load only when needed: `references/data-sources.md` for tool and feed quirks, `references/output-template.md` for the answer skeleton.

Inherit all project-level data-integrity and output-format rules.
