# Setup and Usage

## Keep GitHub as the source of truth

Do not maintain separate edited copies of the same skill if you can avoid it. Clone this repository to the laptop, edit locally, then commit and push changes back to GitHub.

## Windows / PowerShell

Choose a parent folder, then run:

```powershell
cd D:\Projects
git clone https://github.com/moefouly07/market-analysis-skills.git
cd market-analysis-skills
code .
```

If `D:\Projects` does not exist, use any folder you prefer.

To get the latest repository version later:

```powershell
git pull
```

After editing:

```powershell
git add .
git commit -m "Update market skills"
git push
```

## ChatGPT project instructions

Copy the contents of `PROJECT_INSTRUCTIONS.md` into the project's instruction field. Keep this section short; specialized logic belongs in the skills.

## ChatGPT Skills

If the ChatGPT surface you use supports Skills, create or upload each skill from its own directory:

```text
skills/market-options-analyst/
skills/earnings-event-analyst/
skills/market-claim-validator/
```

Each directory contains its own `SKILL.md`.

After a skill is installed, allow ChatGPT to invoke it automatically when relevant. You can still explicitly request a skill when you want deterministic routing or are testing it.

GitHub remains the canonical editable copy. Installing a skill into ChatGPT does not mean future GitHub edits automatically synchronize into every product surface unless that surface explicitly supports synchronization.

## Claude projects and custom skills

Use the same folders. Each skill folder (with its `SKILL.md` and any `references/`) is the unit to install. Paste `PROJECT_INSTRUCTIONS.md` into the project instructions. Check the product's current documentation for the exact upload steps, then confirm the installed version line matches GitHub.

Install only these three skills. Older separately installed copies of `earnings-scanner` or `earnings-lottery-hunter` are now covered by `earnings-event-analyst` and should be removed so two versions of the same rules do not compete.

## Direct GitHub workflow

When using a GitHub-connected agent rather than installed Skills, instruct it to read `PROJECT_INSTRUCTIONS.md` first, then load only the relevant `SKILL.md` for the task.

Do not load all skills for every question.

## Recommended routing

Stock, ETF, technical, support/resistance, volatility, options, macro, or trade setup:

```text
market-options-analyst
```

Earnings, guidance, expectations, historical earnings reactions, event volatility, or earnings contracts:

```text
earnings-event-analyst
```

Trading claims, indicators, strategies, screenshots, social posts, win-rate claims, or backtests:

```text
market-claim-validator
```

Use multiple skills only when the request genuinely crosses domains.