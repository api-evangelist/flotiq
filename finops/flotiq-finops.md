# Flotiq FinOps

This document covers cost management, billing practices, and optimization strategies for Flotiq API usage.

## Pricing Summary

| Plan    | Monthly Price | Annual Price | Savings |
|---------|--------------|--------------|---------|
| Free    | $0           | $0           | —       |
| Basic   | $37          | $444         | ~15%    |
| Growth  | $114         | $1,368       | ~15%    |
| Custom  | Contact sales | Contact sales | Negotiable |

Annual billing saves approximately 15% over monthly billing for Basic and Growth plans.

## Cost Drivers

### API Calls
The primary metered resource. All plans enforce a 30-day rolling window quota:
- Free: 100k calls — suitable for prototyping
- Basic: 300k calls — suitable for moderate-traffic production apps
- Growth: 1M calls — suitable for high-traffic production apps

### Content Objects
- Free: 1,000 objects — strictly for testing
- Basic: 10,000 objects — small to mid-size content libraries
- Growth: 100,000 objects — large editorial or e-commerce catalogs

### File Storage
- Free: 200 MB
- Basic: 15 GB
- Growth: 500 GB

Storage overages and additional file hosting costs are not explicitly documented; contact Flotiq sales for overage pricing.

### Team Seats
- Base seats included: 2 (Free), 3 (Basic), 6 (Growth)
- Extra seats: **$12/month per seat** on paid plans
- For teams larger than 6, the Growth plan with additional seats is the most cost-effective pre-Enterprise option

## Cost Optimization Strategies

1. **Use annual billing** — saves ~15% on Basic and Growth plans
2. **Cache API responses** — Flotiq's quota counts every API call; client-side or CDN caching reduces consumption significantly
3. **Scope API keys** — User Defined Keys let you restrict access to specific content types, reducing accidental over-fetching
4. **Use GraphQL** — GraphQL queries return only requested fields, potentially reducing payload size and the need for multiple REST calls
5. **Monitor rolling usage** — Because limits use a 30-day rolling window, spikes in one period carry forward; monitor usage trends via the Flotiq dashboard
6. **Start on Free** — Free plan is genuinely functional for development; delay upgrading until approaching the 100k call or 1k object limits
7. **Batch content imports** — Use the Flotiq CLI or bulk import tools to populate content objects in batch rather than individual API calls

## Plan Selection Guide

| Use Case | Recommended Plan |
|----------|-----------------|
| Development / prototyping | Free |
| Small production site (<300k API calls/month) | Basic |
| High-traffic site or large content library | Growth |
| Enterprise, regulated, or high-volume | Custom |

## Sources

- https://flotiq.com/pricing/
- https://flotiq.com/blog/headless-cms-api-calls-cost-comparision/
