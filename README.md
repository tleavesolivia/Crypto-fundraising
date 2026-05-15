# Crypto Fundraising Skills Hub

OpenClaw skills for crypto fundraising / VC deal research.

## Skills included

### 1. crypto-fundraising (no API key needed)

Unified skill for crypto fundraising and VC data from DropsTab and Crypto-Fundraising.info. Query funding rounds, VC investments, project fundraising history, and investor details by scraping public web pages. No API key required.

**Use when:** asking about recent funding rounds, VC deals, who invested in what, project financing details, investor information.

**Data sources:**
- **DropsTab** (dropstab.com) — full fundraising history per project, investor profiles, source links
- **Crypto-Fundraising.info** — clean text data with investor names, project descriptions

### 2. drops-tab (requires API key)

Direct DropsTab API integration for structured data access. Requires a paid DropsTab API subscription ($19/mo starting).

**Use when:** you need programmatic access to funding rounds, investors, token unlocks via API endpoints.

## Installation

```bash
# Install all skills
npx skills add https://github.com/tleavesolivia/Crypto-fundraising

# Or install without prompts
npx skills add https://github.com/tleavesolivia/Crypto-fundraising --yes
```

## Manual installation

Copy the `skills/` folder into your OpenClaw workspace:

```bash
cp -r skills/* /path/to/workspace/skills/
```
