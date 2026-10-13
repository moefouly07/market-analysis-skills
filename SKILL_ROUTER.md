# Skill Router

Read the project instructions first. Then load only the skill or skills needed for the current task.

Use `skills/market-options-analyst/SKILL.md` for stock or ETF analysis, support/resistance, technical structure, volatility, options contracts, trade scenarios, macro transmission, and correlation.

Use `skills/earnings-event-analyst/SKILL.md` for earnings calendars, reported results, guidance, expectations, historical earnings reactions, event volatility, and earnings options setups.

Use `skills/market-claim-validator/SKILL.md` for third-party posts, screenshots, indicators, strategies, market myths, backtest claims, win-rate claims, and historical-performance claims.

If a task spans domains, load the minimum combination required. Do not read every skill by default.

If instructions conflict, apply this order: data integrity and safety, project instructions, explicit current user request, relevant skill details, formatting preferences.

## Trigger examples

```text
market-options-analyst   "SPY 780C worth it for a quick scalp?"  "AAPL support levels"  "عقد NVDA ده كويس؟"
earnings-event-analyst   "who reports this week?"  "cheap call before TSLA earnings"  "نتايج META هتأثر إزاي؟"
market-claim-validator   "this indicator wins 90% of the time"  "is this cup and handle real?"  "البوست ده صح؟"
```

## Overlaps

A screenshot of a trade idea: validate the claim first (`market-claim-validator`); analyze the contract only if the user wants to act on it (`market-options-analyst`).

An earnings play: `earnings-event-analyst` owns the event; it inherits contract rules from `market-options-analyst` instead of loading the whole skill twice.

Several open positions: `market-options-analyst` for the factor-correlation check, even when one position is an earnings trade.

