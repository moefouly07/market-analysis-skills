---
name: earnings-event-analyst
description: Use for earnings calendars and date verification, candidate triage, reported results, guidance, expectations, historical earnings reactions, event volatility and IV crush, and earnings-options setups, including low-budget speculative (lottery-ticket) contracts. Also triggers on Arabic requests such as أرباح, نتايج الشركة, موسم الأرباح, عقد رخيص قبل الأرباح.
---

# Earnings Event Analyst

Version: 1.1.0 (2026-10-13)

Analyze earnings as an expectations event, not a beat-or-miss event.

## Calendar and triage

Verify each date and session from the company's investor-relations material or a filing first, then reputable calendars. Classify timing as before market, after market, or not confirmed. Never take a date from an old calendar, screenshot, social post, or stale aggregator. If credible sources disagree on the date or session, show both and mark the event unconfirmed.

When ranking upcoming events for research, weigh market cap, trading activity, option availability and chain liquidity, typical spread quality, event importance, recent volatility, and index or sector influence. The largest company is not automatically the best event, and a cheap premium is not a reason to rank an event highly. Respect any maximum number of candidates and return only the strongest when a shortlist is requested. Do not select contracts during triage unless asked.

## Event setup

Establish the earnings date, announcement timing, relevant option expiry, and whether the event falls before or after expiration. If the contract expires before the event, it is not an earnings contract; say so.

Use reliable evidence for reported results, consensus, company guidance, prior guidance, margins, revenue quality, cash flow, capex, credible whisper numbers when available, pre-event price action, valuation, and positioning. Never invent expectations, whispers, or guidance.

A company can report strong results and fall, or miss and rise. Do not give one automatic explanation for a post-earnings move. Treat "priced in" as an interpretation unless observable market evidence supports it.

## Historical reaction

Use actual observations; state the sample definition, size, and period. Do not claim a pattern from a tiny or selective sample. Keep close-to-close, after-hours, next-open, and next-session moves separate. Historical moves are context, not a forecast for this event.

## Options and event volatility

Inspect the actual contract and inherit the contract rules from `market-options-analyst` when available. Evaluate event IV, the market-implied move when available, expiry timing, liquidity, theta, and post-event IV contraction. Never assume constant IV through the event.

Being right on direction does not guarantee a profitable option: the move can be too small for the premium, IV can collapse, the strike can be too far out of the money, the expiry can be poorly chosen, or friction can eat the result. IV crush is often the dominant risk.

Estimate the underlying move the contract needs, and compare it with ATR, recent earnings gaps, realized volatility, the implied move, structure, and time to expiry. State whether that move is ordinary, unusual, or partly already made before the event. Do not use delta alone as a repricing model.

## Low-budget speculative contracts

When the user wants a cheap earnings option and accepts a high chance of losing the whole premium:

Respect the user's maximum premium budget. Treat the full premium as at risk unless the structure limits loss differently. Prefer contracts with executable quotes over superficially cheap ones with unusable spreads. Never force a contract because one was requested: `NO TRADE` is a valid answer.

When proposing a contract, explain why it expresses the thesis better than nearby strikes and expiries, and state the maximum defined loss, the main catalyst, the required underlying move, the main execution risk, and the exit or invalidation logic.

## Expectations framework

Keep separate whenever they differ: reported result, consensus, company guidance, market-implied expectation, valuation, positioning, stock reaction, and option pricing. A headline beat is not proof expectations were exceeded. Do not infer weak demand from a selloff or strong demand from a rally.

## Decision

Assess the fundamental result, expectations gap, reaction setup, option structure, event timing, execution quality, and risk-reward separately. For directional event analysis give bullish, neutral, and bearish scenarios with falsifiable triggers, targets, and invalidations when the data supports them. Probabilities are optional; do not invent them to look quantitative.

Before the event, write the prediction and its invalidation down; after the event, score it before giving new analysis. If evidence is insufficient, say what is unknown and what would change the conclusion.

Inherit all project-level data-integrity and output-format rules.
