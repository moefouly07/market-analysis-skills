# Skill Regression Checks

Run these prompts after every change to a skill or to the project instructions, in a fresh chat with the skills installed. Record pass or fail per case in `evals/RESULTS.md` with the date, the model, and the skill versions. A change that turns a pass into a fail is not merged until fixed.

Market data changes daily, so the checks test behavior, not numbers.

## Data integrity

E01. "What's SPY trading at and is the 780 call a buy?" asked on a Saturday.
Pass: states the ET time and that the market is closed; separates Friday's official close from any weekend quote; treats option bid/ask as frozen or stale; does not present a stale quote as live.

E02. "Give me the Greeks for NVDA 200C expiring Friday." when the option-quote tool returns an error.
Pass: says the source failed; either stops or labels any Greeks as model estimates with their inputs; never presents invented values as quotes.

E03. "RSI on AAPL?" when a tool returns a pre-computed RSI.
Pass: computes Wilder RSI14 from raw completed bars, or says it could not; reports the tool's value only as a cross-check.

## Options mechanics

E04. "SPY 0DTE 785C bid 0.05 ask 0.12, scalp it?"
Pass: friction about 58% computed and flagged; required exit bid for the target stated; explains that the spread alone makes a quick profitable exit unlikely.

E05. "My ITM put shows bid below intrinsic, should I sell at the bid?"
Pass: treats the bid as a possible stale or illiquid quote; does not endorse selling below intrinsic; suggests checking the timestamp and depth.

E06. "$0.50 call, theta -0.05, I'll hold it a week."
Pass: theta burn 10% per day computed and explained in plain Arabic.

## Analysis discipline

E07. "Bullish, neutral, bearish for TSLA with probabilities."
Pass: one named pivot; each scenario has trigger, target, invalidation; probabilities labeled as estimates, cover the whole range, sum to 100%.

E08. Return to a setup analyzed in an earlier chat.
Pass: scores the earlier call before new analysis; names any error in one line.

E09. "AAPL calls, SLV calls, and KKR calls: am I diversified?"
Pass: identifies the shared rates and risk-sentiment channel.

## Earnings

E10. "Cheap call under $50 for ZM earnings."
Pass: verifies date and session from a primary source or marks it unconfirmed; respects the budget; checks that expiry is after the event; addresses IV crush; `NO TRADE` allowed.

E11. "Who reports this week?"
Pass: before-market, after-market, or unconfirmed for each; no dates from screenshots or stale aggregators; disagreements shown.

## Claims

E12. Screenshot: "This indicator has a 92% win rate."
Pass: separates mechanical facts from performance claims; mentions expectancy versus win rate; classifies the evidence state; does not attribute the claim to the user.

E13. "Is this a cup and handle?" with a chart.
Pass: checks the pattern in the actual bars; asks for or states the base rate; no probability without a base rate.

## Format

E14. Any market answer.
Pass: Egyptian Arabic; no Arabic and English on the same line; numbers and tickers on separate lines or in code blocks; no bullets; new terms explained in plain Arabic; ends with الخلاصة without new information.
