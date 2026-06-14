# Flotiq GraphQL

Flotiq provides a GraphQL API that is automatically generated from your content type definitions. The schema evolves dynamically as you add or modify content types in your account.

## Endpoints

| Purpose               | Method | URL                                            |
|-----------------------|--------|------------------------------------------------|
| Execute GraphQL query | POST   | `https://api.flotiq.com/api/v2/graphql`        |
| Retrieve schema       | GET    | `https://api.flotiq.com/api/v2/graphql/schema` |

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

The SDL schema file for the built-in system types and the documented demo content types is at:
[flotiq-schema.graphql](flotiq-schema.graphql)

Retrieve the live schema for your account:
```
GET https://api.flotiq.com/api/v2/graphql/schema
```

## Query Parameters

When querying content objects the following optional arguments are supported on every root query field:

| Parameter         | Description                                        | Default |
|-------------------|----------------------------------------------------|---------|
| `id`              | Fetch a single object by its ID                    | —       |
| `field`           | Field name to match (used with `value`)            | —       |
| `value`           | Value to match against `field`                     | —       |
| `first`           | Number of results per page (max 1000)              | 10      |
| `offset`          | Number of records to skip                          | 0       |
| `order_by`        | Field name to sort results by                      | —       |
| `order_direction` | `asc` or `desc`                                    | asc     |
| `filter`          | Typed filter input object for field-level filtering | —      |

## Example Queries

### Fetch a single object by ID
```graphql
{
  product(id: "product-1") {
    edges {
      node {
        id
        name
      }
    }
  }
}
```

### List with pagination and sorting
```graphql
query {
  product(first: 2, order_by: "name", order_direction: "asc") {
    edges {
      node {
        id
        name
      }
    }
  }
}
```

### Query with relations resolved
```graphql
query Product {
  product(first: 1) {
    edges {
      node {
        id
        name
        categories {
          id
          name
        }
      }
    }
  }
}
```

### Query with filtering (using variables)
```graphql
query Products($productsFilter: productFilterInput) {
  product(filter: $productsFilter) {
    edges {
      node {
        id
        name
        internal {
          createdAt
        }
      }
    }
    totalCount
    pageInfo {
      hasNextPage
    }
  }
}
```

Variables:
```json
{
  "productsFilter": {
    "name": {
      "type": "contains",
      "filter": "Rooibos"
    }
  }
}
```

## Connection Pattern

All list queries return a connection type with:

- `edges` — array of `{ node: <ContentType> }` objects
- `pageInfo` — `{ hasNextPage: Boolean }`
- `totalCount` — total number of matching records

## Relation Resolution (Hydration)

Related objects are automatically resolved based on the `DataSource` type stored in the content object. For example, a `product` with a `categories` relation will return the full `category` objects nested inside the query response.

## Legacy GraphQL

Flotiq also maintains a legacy GraphQL endpoint (`/api/v1/graphql`) for backwards compatibility. New integrations should use the v2 endpoint documented above.

## Notes

- The GraphQL API counts toward the same account-level API call quota as REST endpoints
- GraphQL is available on all paid plans and the Free plan
- Using GraphQL field selection can reduce over-fetching compared to equivalent REST calls
- Only "public" status objects are returned by default; draft/preview content requires a preview mode flag

## Source

https://flotiq.com/docs/API/graph-ql/
