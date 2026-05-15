---
name: crypto-fundraising
description: |
  Unified skill for crypto fundraising/VC data from DropsTab and Crypto-Fundraising.info.
  Query funding rounds, VC investments, project fundraising history, investor details.
  Use when user asks about: funding rounds, VC deals, fundraising data, who invested,
  recent rounds, project financing details, investor information.
  No API key needed — data is scraped from public web pages.
---

# Crypto Fundraising Skill

Fetches crypto fundraising data from two public sources for cross-validation:

| Source | Strength | Weakness |
|--------|----------|----------|
| **DropsTab** (dropstab.com) | Full history per project, investor profiles, source links | Some images without alt text for VCs on list pages |
| **Crypto-Fundraising.info** | Clean text, investor names readable, project descriptions | Fewer projects, less historical data |

---

## Query Patterns

### 1. Recent Funding Rounds (last N days)

Use DropsTab list page:

```
https://dropstab.com/latest-fundraising-rounds
```

For upcoming rounds, use Crypto-Fundraising.info:

```
https://crypto-fundraising.info
```

### 2. Specific Project Details

DropsTab (full detail with investor list):
```
https://dropstab.com/coins/{slug}/fundraising
```

Crypto-Fundraising.info (description + history):
```
https://crypto-fundraising.info/projects/{slug}/
```

### 3. Investor / VC Profile

DropsTab:
```
https://dropstab.com/investors/{slug}
```

### 4. Filter by Category

DropsTab list page supports filter parameters - navigate to:
```
https://dropstab.com/latest-fundraising-rounds
```
and apply category filters in the URL (e.g., DeFi, AI, Infrastructure).

---

## Slug Mapping (Common Projects)

| Project | Dropstab Slug | CFI Slug |
|---------|---------------|----------|
| Elliptic | `elliptic` | `elliptic` |
| Arc | `arc-network` | `arc-chain` |
| Reap | `reap` | `reap` |
| Hidden Road | `hidden-road` | `hiddenroad` |
| Fun | `fun-xyz` | `fun` |

When slug is unknown, search by project name on the site.

---

## Tool Use Instructions

When the user asks about fundraising:

1. **"List fundraising rounds" / "Recent funding"** → Fetch DropsTab list page
2. **"Project X details"** → Try DropsTab detail page first, then CFI for description
3. **"Who invested in X"** → Fetch both pages and cross-reference
4. **"Past 2 weeks funding"** → Fetch DropsTab list, filter by date from response

Extract data carefully:
- Amounts may be in raw numbers (e.g., `120000000` → $120M)
- Convert to human-readable format
- Dates may be relative or in various formats — normalize
- If VC names are missing on DropsTab list pages (image-only with "+N" counts), use DETAIL PAGE (`/coins/{slug}/fundraising`) first; if still incomplete, search online for "{project name} {round type} {amount} {date} investors" to find the latest round's investors
- Always use the MOST RECENT round's investor list — do not mix investors from previous rounds
- Verify the news date roughly matches the DropsTab record date before including investor names

---

## Security

No API keys required. All data is from publicly accessible web pages.
Rate limiting is handled by the scraping tool — avoid excessive requests.
