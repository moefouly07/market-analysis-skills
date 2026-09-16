# Market Analysis Skills

Canonical source for reusable US equity, options, earnings, and market-claim analysis skills.

## Files

`PROJECT_INSTRUCTIONS.md` contains the compact project-level behavior and output rules.

`SKILL_ROUTER.md` maps common market tasks to the minimum relevant skill.

`skills/market-options-analyst/SKILL.md` handles stock, ETF, technical, volatility, options, macro, and trade-setup analysis.

`skills/earnings-event-analyst/SKILL.md` handles earnings, guidance, expectations, historical reactions, event volatility, and earnings options.

`skills/market-claim-validator/SKILL.md` handles third-party claims, indicators, strategies, screenshots, social posts, and backtest/performance claims.

## Operating model

GitHub is the source of truth and version-control layer. Do not assume a model automatically discovers or reads this repository merely because it exists.

For ChatGPT surfaces that support Skills, install or upload the relevant skill so ChatGPT can invoke it automatically when useful. Keep this repository as the canonical editable copy.

For workflows that read directly from GitHub, read `PROJECT_INSTRUCTIONS.md` first and then only the relevant `SKILL.md`. Avoid loading all skills by default.

## Local workflow

Clone the repository to the laptop and edit it with VS Code or another text editor. Commit and push changes back to GitHub so the repository remains authoritative.

Example:

```powershell
git clone https://github.com/moefouly07/market-analysis-skills.git
cd market-analysis-skills
code .
```

To update later:

```powershell
git pull
```

After editing:

```powershell
git add .
git commit -m "Update market analysis skills"
git push
```

## Skill installation

When a product supports skill upload, upload the individual skill directory or package required by that product. The exact installation and synchronization behavior can vary by product and interface.

Keep project-level rules short. Put specialized domain logic in the skill files rather than duplicating it into the project prompt.