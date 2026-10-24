# Changelog

## Unreleased — 2026-10-23

Output format replaced at the user's direction, from his own supplied example report: structured desk reports with a title and subtitle, one section per instrument headed by the official ticker in English capitals plus an Arabic headline, a short Cairene analysis paragraph per section, data as Arabic-labeled lines with English-digit values, grouped market, system and open-position sections, and a bulleted الخلاصة التنفيذية followed by the governing-rule line and the standing disclaimer. Tickers are always the official traded symbol (ZM, not ZOOM). The previous prose-only format (no bullets, figures in code blocks, closing heading الخلاصة) is retired for desk reports.

## 1.1.0 — 2026-10-13

market-options-analyst: restored the contract formulas (friction, intrinsic, extrinsic, breakeven) and the bid-below-intrinsic check that the deployed copy had and this repository had lost; added short-hold scalp rules (required exit bid, theta burn per day, exit liquidity), quote-freshness checks, interpolated-bar handling, an explicit realized-volatility definition, pattern base rates, catalyst-already-fired check, fact / interpretation / estimate labels, scoring of earlier calls, a guard for frozen strategies, and two on-demand references (data-source quirks, answer skeleton).

earnings-event-analyst: restored calendar verification and triage (formerly earnings-scanner) and the low-budget speculative rules (formerly earnings-lottery-hunter): budget, NO TRADE, expiry-before-event rejection, required move, maximum defined loss, comparison with nearby contracts.

market-claim-validator: pattern base rates, in-sample disclosure, pre-registered forward tests, no attribution of a post's stance to the user.

Project instructions and router: extended watchlist, short-hold style, quote timestamps, raw-bar indicators, claim labels, plain-Arabic term definitions, one conflict order, trigger examples including Arabic, overlap rules.

Added `evals/EVALS.md` regression checks and version lines in every skill.

## 1.0.0 — 2026-09-15

Initial skills, router, project instructions, setup guide.
