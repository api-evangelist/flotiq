# Flotiq

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Flotiq is an API-first headless CMS that auto-generates RESTful and GraphQL APIs from user-defined content type definitions. It supports both cloud-hosted and self-managed deployments.

## Overview

- **Website**: https://flotiq.com/
- **Documentation**: https://flotiq.com/docs/
- **API Base URL**: https://api.flotiq.com/api/v1/
- **GraphQL Endpoint**: https://api.flotiq.com/api/v2/graphql
- **GitHub Organization**: https://github.com/flotiq
- **LinkedIn**: https://www.linkedin.com/company/flotiq
- **Pricing**: https://flotiq.com/pricing/

## Key Features

- Auto-generated RESTful and GraphQL APIs from content type definitions
- Dynamic OpenAPI schema that updates with every content type change
- Full-text search engine built in
- SDK generation (JavaScript/TypeScript and custom)
- CLI tools for data migration and project setup
- Integrations with Gatsby, Next.js, Netlify, Vercel, and more
- Webhooks for event-driven workflows
- Scoped API keys for fine-grained access control

## Plans

| Plan   | Price        | API Calls/Month | Content Objects |
|--------|-------------|-----------------|-----------------|
| Free   | $0          | 100,000         | 1,000           |
| Basic  | $37/month   | 300,000         | 10,000          |
| Growth | $114/month  | 1,000,000       | 100,000         |
| Custom | Contact sales | Custom         | Custom          |

See [plans/flotiq-plans.md](plans/flotiq-plans.md) for full plan details.

## Repository Contents

- `apis.yml` — API catalog index (apis.io format)
- `plans/flotiq-plans.md` — Detailed plan and pricing breakdown
- `rate-limits/flotiq-rate-limits.md` — Rate limiting policies and quotas
- `finops/flotiq-finops.md` — Cost management and optimization guidance
- `graphql/flotiq-graphql.md` — GraphQL API reference

## Maintainer

Kin Lane — kin@apievangelist.com
