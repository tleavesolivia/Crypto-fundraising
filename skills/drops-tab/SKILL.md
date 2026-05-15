---
name: drops-tab
description: |
  DropsTab API integration for crypto fundraising/VC data. 
  Query funding rounds, investors, venture capital deals across crypto projects.
  Use when user asks about: crypto funding rounds, VC investments, fundraising data,
  who invested in what, recent deals, project financing, or investor activity.
  Requires DropsTab API key (paid subscription from dropstab.com).
---

# DropsTab

DropsTab provides a comprehensive API for crypto fundraising data including funding rounds, investors, and VC activity.

## Prerequisites

- **API Key**: Obtain from [DropsTab Commercial API](https://dropstab.com/products/commercial-api) (starts at $19/month)
- Store the key in `.openclaw/secrets.env` as `DROPSTAB_API_KEY=your_key_here`

## API Base URL

```
https://public-api.dropstab.com/api/v1
```

**Authentication**: Pass API key via header `X-API-KEY: <your-key>`

---

## Endpoints

### 1. List Funding Rounds

**`GET /fundingRounds`**

Query parameters:

| Param | Type | Description |
|-------|------|-------------|
| `page` | int32 | Page number (default 0) |
| `pageSize` | int32 | Results per page (default 100) |
| `sortingOrder` | string | `ASC` / `DESC` (default `ASC`) |
| `sortingField` | string | Sort by: `FUNDS_RAISED`, `PRE_VALUATION`, `DATE`, `TWITTER_PERFORMANCE` |
| `coinSlug` | string | Filter by coin slug |
| `investorSlug` | string | Filter by investor slug |
| `investorsCountFrom`/`To` | int32 | Filter by investor count range |
| `fundsRaisedFrom`/`To` | int64 | Filter by funds raised range (USD) |
| `preValuationFrom`/`To` | number | Filter by pre-money valuation range |
| `dateFrom`/`To` | int64 | Filter by date range (unix ms) |
| `twitterPerformanceFrom`/`To` | number | Filter by Twitter follower growth |

### 2. Get Funding Round by ID

**`GET /fundingRounds/{id}`**

Returns a single funding round by its ID.

### 3. Get Funding Rounds for a Coin

**`GET /fundingRounds/coin/{coinSlug}`**

Returns all funding rounds associated with a specific coin.

### 4. List Investors

**`GET /investors`**

Query parameters:

| Param | Type | Description |
|-------|------|-------------|
| `page` | int32 | Page number |
| `pageSize` | int32 | Results per page |
| `sortingOrder` | string | `ASC` / `DESC` |
| `sortingField` | string | `NAME`, `FUNDS_INVESTED`, `DEALS_COUNT` |

### 5. Get Investor Details

**`GET /investors/{investorSlug}`**

Returns detailed info about a specific investor/VC.

### 6. List All Coins

**`GET /coins`**

Returns list of all tracked coins with market data.

### 7. Get Token Unlocks

**`GET /tokenUnlocks`** — list token unlock schedules
**`GET /tokenUnlocks/{coinSlug}`** — unlocks for a specific coin

---

## Common Queries

### Past 2 weeks funding rounds (descending by date)

```
GET /api/v1/fundingRounds?sortingField=DATE&sortingOrder=DESC&pageSize=50
```

### Top 10 largest rounds in a date range

```
GET /api/v1/fundingRounds?sortingField=FUNDS_RAISED&sortingOrder=DESC&dateFrom={14_days_ago_ms}&pageSize=10
```

### Funding rounds by specific investor (e.g., a16z)

```
GET /api/v1/fundingRounds?investorSlug=a16z&sortingField=DATE&sortingOrder=DESC
```

## Date to Unix Ms Conversion

| Time | Unix Ms |
|------|---------|
| Now (May 15, 2026) | 1778774400000 |
| 7 days ago | 1778169600000 |
| 14 days ago | 1777564800000 |
| 30 days ago | 1776182400000 |

---

## Security

- Never display full API key. Show only first 5 + last 4 chars.
- Store key in `.openclaw/secrets.env` as `DROPSTAB_API_KEY`
