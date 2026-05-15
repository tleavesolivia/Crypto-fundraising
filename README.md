# Crypto Fundraising Skill

OpenClaw skill for crypto fundraising / VC deal research via public web data.

**No API keys required.** Data is scraped from DropsTab and Crypto-Fundraising.info.

## What it does

- Query recent fundraising rounds across crypto
- Get detailed project funding history (amount, valuation, investors, source links)
- Look up investor / VC profiles
- Cross-reference data from two sources for accuracy

## Data sources

| Source | Strength | Weakness |
|--------|----------|----------|
| **DropsTab** | Full fundraising history per project, investor profiles, source links | VC names in images on list pages |
| **Crypto-Fundraising.info** | Clean text, investor names readable, project descriptions | Fewer projects |

## Installation

```bash
npx skills add https://github.com/tleavesolivia/Crypto-fundraising

# Or install without prompts
npx skills add https://github.com/tleavesolivia/Crypto-fundraising --yes
```

## Manual installation

Copy the `skills/` folder into your OpenClaw workspace:

```bash
cp -r skills/* /path/to/workspace/skills/
```
