# Flotiq Rate Limits

Flotiq enforces API call quotas at the account level using a rolling 30-day window. All API keys (Application Keys and User Defined Keys) under the same account share a single quota pool.

## API Call Quotas by Plan

| Plan    | API Calls (30-day rolling) |
|---------|---------------------------|
| Free    | 100,000                   |
| Basic   | 300,000                   |
| Growth  | 1,000,000                 |
| Custom  | Up to 15,000,000+         |

## Rolling Window Calculation

- Limits are based on a **30-day rolling window** from the current date, not a fixed calendar month
- Usage is tracked continuously — the oldest day's usage drops off as a new day begins
- This means consumption is smoothed rather than resetting hard on the 1st of each month

## Per-Account Enforcement

- Rate limits apply to the **entire account**, not individual API keys
- All keys' usage is aggregated toward the account's total quota
- There are no per-key or per-endpoint sub-limits documented

## API Key Types

**Application Keys** (read-write and read-only): System-wide keys with full account access. Cannot be removed, only regenerated if compromised.

**User Defined Keys**: Custom-scoped keys restricted to specific content types and CRUD actions. Availability depends on subscription plan. Can be revoked at any time.

## Authentication

Keys are passed via:
- HTTP header: `X-AUTH-TOKEN: YOUR_API_KEY`
- Query parameter: `?auth_token=YOUR_API_TOKEN`

GraphQL endpoints (`/api/v2/graphql`) require Application Keys — User Defined (scoped) keys are not accepted for GraphQL.

## Key Validation Endpoint

```
GET https://api.flotiq.com/api/auth-context
```

Use this endpoint to validate any API key and confirm its scope and permissions.

## Source

https://flotiq.com/docs/API/
