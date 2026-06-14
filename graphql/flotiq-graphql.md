# Flotiq GraphQL

Flotiq provides a GraphQL API that is automatically generated from your content type definitions. The schema evolves dynamically as you add or modify content types in your account.

## Endpoints

| Purpose              | Method | URL                                             |
|----------------------|--------|-------------------------------------------------|
| Execute GraphQL query | POST   | `https://api.flotiq.com/api/v2/graphql`         |
| Retrieve schema       | GET    | `https://api.flotiq.com/api/v2/graphql/schema`  |

## Authentication

GraphQL endpoints require an **Application Key** (read-write or read-only). User Defined (scoped) API keys are **not accepted** for GraphQL.

Pass your key via header:
```
X-AUTH-TOKEN: YOUR_API_KEY
```

Or as a query parameter:
```
https://api.flotiq.com/api/v2/graphql?auth_token=YOUR_API_TOKEN
```

## Schema

The GraphQL schema is derived from your Content Type Definitions (CTDs). Every time you create or modify a content type in Flotiq, the GraphQL schema updates automatically to reflect:

- Attribute types and names
- Required fields
- Relations between content types

Retrieve the current schema:
```
GET https://api.flotiq.com/api/v2/graphql/schema
```

## Query Parameters

When listing content objects, GraphQL queries support the following optional parameters:

| Parameter         | Description                                      |
|-------------------|--------------------------------------------------|
| `page`            | Page number for pagination                       |
| `limit`           | Number of results per page                       |
| `order_by`        | Field name to sort results by                    |
| `order_direction` | `asc` or `desc`                                  |
| `filter`          | Filter expression for narrowing results          |

## Example Query

```graphql
{
  blogpostList(page: 1, limit: 10, order_by: "internal.createdAt", order_direction: "desc") {
    id
    title
    slug
    excerpt
    internal {
      createdAt
      updatedAt
    }
  }
}
```

## Legacy GraphQL

Flotiq also maintains a legacy GraphQL endpoint for backwards compatibility. New integrations should use the v2 endpoint documented above.

## Notes

- The GraphQL API counts toward the same account-level API call quota as REST endpoints
- GraphQL is available on all paid plans and the Free plan
- Using GraphQL's field selection can reduce over-fetching compared to equivalent REST calls

## Source

https://flotiq.com/docs/API/graph-ql/
