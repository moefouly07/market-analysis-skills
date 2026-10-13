# Data Sources and Known Quirks

Observed behavior, not vendor guarantees. Plans and endpoints change: re-verify before relying on an entry, and update this file with the date when something changes.

## General rules

Label every quote with source, feed, and timestamp. Never mix volume from different venues or feeds. Keep the previous official close separate from pre-market, after-hours, and overnight prices. When two sources disagree, show both with their timestamps instead of choosing silently.

## Robinhood (MCP)

```text
equity quotes                live price reliable; bid/ask stale on weekends
equity historicals           interval=day, bounds=regular, adjustment_type=split for indicator bars;
                             the last bar is often interpolated: check and discard
weekly bars                  drop the current incomplete week; resample daily bars to W-FRI instead
intraday bars                venue-limited, undercount consolidated volume: timing only
option chain sequence        get_option_chains -> get_option_instruments -> get_option_quotes
strike format                exact string with four decimals, e.g. "110.0000"
option quotes                freeze at the 16:00 ET close; always check updated_at
option quotes 403            persistent for some symbols (seen: NVDA); if Greeks are then
                             model-derived, label them as model estimates
option instrument IDs        go stale; re-fetch every session
multi-date instrument calls  silently omit dates without listings; verify dates one by one
technical indicators         diverge from Wilder values; cross-check only
fundamentals                 float does not update after lock-up expirations
index quotes (VIX)           need the instrument ID from search first
```

## Webull

```text
daily bars (single)   authoritative official OHLCV; returned newest-first, reverse before computing
weekend snapshots     only price, close, pre_close, volume are reliable
```

## Alpaca (free market-data plan)

```text
real-time               IEX only, a single venue (about 2-3% of trades); not consolidated
consolidated SIP        refused for the most recent 15 minutes
daily bars              a request ending on the current ET date is refused, even after the close
                        (observed 2026-10-12)
```

## Alpha Vantage

```text
TIME_SERIES_DAILY       outputsize=full for 200-day work
HISTORICAL_OPTIONS      per-contract Greeks and IV by expiration
REALTIME_OPTIONS        permission error on the current plan
```

## FMP

```text
VIX                     indexes -> index-quote with ^VIX
GCUSD commodities       COMEX futures with a basis premium over spot; never interchangeable
                        with spot gold for GLD/IAU work; calibrate from a known ratio first
analyst data            price-target-consensus and grades-summary reliable
quote endpoint          access error on the current plan
intraday charts         require a higher plan (observed 2026-10-12)
```

## Web search

Needed for earnings dates, macro calendars, analyst actions, lock-ups, and short interest. Very recent items (under about 30 minutes) may not be indexed yet; say so instead of guessing.
