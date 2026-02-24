# Customers

## Overview

### Available Operations

* [UpdateCustomer](#updatecustomer) - Update customer
* [CreateCustomer](#createcustomer) - Create customer
* [GetCustomerByExternalID](#getcustomerbyexternalid) - Get customer by external ID
* [QueryCustomer](#querycustomer) - Query customers
* [GetCustomerUsageSummary](#getcustomerusagesummary) - Get customer usage summary
* [GetCustomer](#getcustomer) - Get customer
* [DeleteCustomer](#deletecustomer) - Delete customer
* [GetCustomerEntitlements](#getcustomerentitlements) - Get customer entitlements
* [GetCustomerUpcomingGrants](#getcustomerupcominggrants) - Get upcoming credit grant applications

## UpdateCustomer

Use when updating customer details (e.g. name, email, or metadata). Identify by id or external_customer_id.

### Example Usage

<!-- UsageSnippet language="go" operationID="updateCustomer" method="put" path="/customers" -->
```go
package main

import(
	"context"
	"undefined"
	"undefined/models/components"
	"log"
)

func main() {
    ctx := context.Background()

    s := undefined.New(
        "https://api.example.com",
        undefined.WithSecurity("<YOUR_API_KEY_HERE>"),
    )

    res, err := s.Customers.UpdateCustomer(ctx, components.DtoUpdateCustomerRequest{}, nil, nil)
    if err != nil {
        log.Fatal(err)
    }
    if res.DtoCustomerResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                  | Type                                                                                       | Required                                                                                   | Description                                                                                |
| ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ |
| `ctx`                                                                                      | [context.Context](https://pkg.go.dev/context#Context)                                      | :heavy_check_mark:                                                                         | The context to use for the request.                                                        |
| `body`                                                                                     | [components.DtoUpdateCustomerRequest](../../models/components/dtoupdatecustomerrequest.md) | :heavy_check_mark:                                                                         | Customer                                                                                   |
| `id`                                                                                       | **string*                                                                                  | :heavy_minus_sign:                                                                         | Customer ID                                                                                |
| `externalCustomerID`                                                                       | **string*                                                                                  | :heavy_minus_sign:                                                                         | Customer External ID                                                                       |
| `opts`                                                                                     | [][operations.Option](../../models/operations/option.md)                                   | :heavy_minus_sign:                                                                         | The options for this request.                                                              |

### Response

**[*operations.UpdateCustomerResponse](../../models/operations/updatecustomerresponse.md), error**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| apierrors.ErrorsErrorResponse | 400                           | application/json              |
| apierrors.ErrorsErrorResponse | 500                           | application/json              |
| apierrors.APIError            | 4XX, 5XX                      | \*/\*                         |

## CreateCustomer

Use when onboarding a new billing customer (e.g. sign-up or CRM sync). Ideal for linking via external_customer_id to your app's user id.

### Example Usage

<!-- UsageSnippet language="go" operationID="createCustomer" method="post" path="/customers" -->
```go
package main

import(
	"context"
	"undefined"
	"undefined/models/components"
	"log"
)

func main() {
    ctx := context.Background()

    s := undefined.New(
        "https://api.example.com",
        undefined.WithSecurity("<YOUR_API_KEY_HERE>"),
    )

    res, err := s.Customers.CreateCustomer(ctx, components.DtoCreateCustomerRequest{
        ExternalID: "<id>",
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.DtoCustomerResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                  | Type                                                                                       | Required                                                                                   | Description                                                                                |
| ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ |
| `ctx`                                                                                      | [context.Context](https://pkg.go.dev/context#Context)                                      | :heavy_check_mark:                                                                         | The context to use for the request.                                                        |
| `request`                                                                                  | [components.DtoCreateCustomerRequest](../../models/components/dtocreatecustomerrequest.md) | :heavy_check_mark:                                                                         | The request object to use for the request.                                                 |
| `opts`                                                                                     | [][operations.Option](../../models/operations/option.md)                                   | :heavy_minus_sign:                                                                         | The options for this request.                                                              |

### Response

**[*operations.CreateCustomerResponse](../../models/operations/createcustomerresponse.md), error**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| apierrors.ErrorsErrorResponse | 400                           | application/json              |
| apierrors.ErrorsErrorResponse | 500                           | application/json              |
| apierrors.APIError            | 4XX, 5XX                      | \*/\*                         |

## GetCustomerByExternalID

Use when resolving a customer by your app's id (e.g. from your user table). Ideal for integrations that key by external id.

### Example Usage

<!-- UsageSnippet language="go" operationID="getCustomerByExternalId" method="get" path="/customers/external/{external_id}" -->
```go
package main

import(
	"context"
	"undefined"
	"log"
)

func main() {
    ctx := context.Background()

    s := undefined.New(
        "https://api.example.com",
        undefined.WithSecurity("<YOUR_API_KEY_HERE>"),
    )

    res, err := s.Customers.GetCustomerByExternalID(ctx, "<id>")
    if err != nil {
        log.Fatal(err)
    }
    if res.DtoCustomerResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                | Type                                                     | Required                                                 | Description                                              |
| -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- |
| `ctx`                                                    | [context.Context](https://pkg.go.dev/context#Context)    | :heavy_check_mark:                                       | The context to use for the request.                      |
| `externalID`                                             | *string*                                                 | :heavy_check_mark:                                       | Customer External ID                                     |
| `opts`                                                   | [][operations.Option](../../models/operations/option.md) | :heavy_minus_sign:                                       | The options for this request.                            |

### Response

**[*operations.GetCustomerByExternalIDResponse](../../models/operations/getcustomerbyexternalidresponse.md), error**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| apierrors.ErrorsErrorResponse | 400, 404                      | application/json              |
| apierrors.ErrorsErrorResponse | 500                           | application/json              |
| apierrors.APIError            | 4XX, 5XX                      | \*/\*                         |

## QueryCustomer

Use when listing or searching customers (e.g. admin CRM or reporting). Returns a paginated list; supports filtering and sorting.

### Example Usage

<!-- UsageSnippet language="go" operationID="queryCustomer" method="post" path="/customers/search" -->
```go
package main

import(
	"context"
	"undefined"
	"undefined/models/components"
	"log"
)

func main() {
    ctx := context.Background()

    s := undefined.New(
        "https://api.example.com",
        undefined.WithSecurity("<YOUR_API_KEY_HERE>"),
    )

    res, err := s.Customers.QueryCustomer(ctx, components.TypesCustomerFilter{})
    if err != nil {
        log.Fatal(err)
    }
    if res.DtoListCustomersResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                        | Type                                                                             | Required                                                                         | Description                                                                      |
| -------------------------------------------------------------------------------- | -------------------------------------------------------------------------------- | -------------------------------------------------------------------------------- | -------------------------------------------------------------------------------- |
| `ctx`                                                                            | [context.Context](https://pkg.go.dev/context#Context)                            | :heavy_check_mark:                                                               | The context to use for the request.                                              |
| `request`                                                                        | [components.TypesCustomerFilter](../../models/components/typescustomerfilter.md) | :heavy_check_mark:                                                               | The request object to use for the request.                                       |
| `opts`                                                                           | [][operations.Option](../../models/operations/option.md)                         | :heavy_minus_sign:                                                               | The options for this request.                                                    |

### Response

**[*operations.QueryCustomerResponse](../../models/operations/querycustomerresponse.md), error**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| apierrors.ErrorsErrorResponse | 400                           | application/json              |
| apierrors.ErrorsErrorResponse | 500                           | application/json              |
| apierrors.APIError            | 4XX, 5XX                      | \*/\*                         |

## GetCustomerUsageSummary

Use when showing a customer's usage (e.g. portal or overage alerts). Identify by customer_id or customer_lookup_key; supports filters.

### Example Usage

<!-- UsageSnippet language="go" operationID="getCustomerUsageSummary" method="get" path="/customers/usage" -->
```go
package main

import(
	"context"
	"undefined"
	"undefined/models/operations"
	"log"
)

func main() {
    ctx := context.Background()

    s := undefined.New(
        "https://api.example.com",
        undefined.WithSecurity("<YOUR_API_KEY_HERE>"),
    )

    res, err := s.Customers.GetCustomerUsageSummary(ctx, operations.GetCustomerUsageSummaryRequest{})
    if err != nil {
        log.Fatal(err)
    }
    if res.DtoCustomerUsageSummaryResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                              | Type                                                                                                   | Required                                                                                               | Description                                                                                            |
| ------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------ |
| `ctx`                                                                                                  | [context.Context](https://pkg.go.dev/context#Context)                                                  | :heavy_check_mark:                                                                                     | The context to use for the request.                                                                    |
| `request`                                                                                              | [operations.GetCustomerUsageSummaryRequest](../../models/operations/getcustomerusagesummaryrequest.md) | :heavy_check_mark:                                                                                     | The request object to use for the request.                                                             |
| `opts`                                                                                                 | [][operations.Option](../../models/operations/option.md)                                               | :heavy_minus_sign:                                                                                     | The options for this request.                                                                          |

### Response

**[*operations.GetCustomerUsageSummaryResponse](../../models/operations/getcustomerusagesummaryresponse.md), error**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| apierrors.ErrorsErrorResponse | 400                           | application/json              |
| apierrors.ErrorsErrorResponse | 500                           | application/json              |
| apierrors.APIError            | 4XX, 5XX                      | \*/\*                         |

## GetCustomer

Use when you need to load a single customer (e.g. for a billing portal or to attach a subscription).

### Example Usage

<!-- UsageSnippet language="go" operationID="getCustomer" method="get" path="/customers/{id}" -->
```go
package main

import(
	"context"
	"undefined"
	"log"
)

func main() {
    ctx := context.Background()

    s := undefined.New(
        "https://api.example.com",
        undefined.WithSecurity("<YOUR_API_KEY_HERE>"),
    )

    res, err := s.Customers.GetCustomer(ctx, "<id>")
    if err != nil {
        log.Fatal(err)
    }
    if res.DtoCustomerResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                | Type                                                     | Required                                                 | Description                                              |
| -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- |
| `ctx`                                                    | [context.Context](https://pkg.go.dev/context#Context)    | :heavy_check_mark:                                       | The context to use for the request.                      |
| `id`                                                     | *string*                                                 | :heavy_check_mark:                                       | Customer ID                                              |
| `opts`                                                   | [][operations.Option](../../models/operations/option.md) | :heavy_minus_sign:                                       | The options for this request.                            |

### Response

**[*operations.GetCustomerResponse](../../models/operations/getcustomerresponse.md), error**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| apierrors.ErrorsErrorResponse | 400                           | application/json              |
| apierrors.ErrorsErrorResponse | 500                           | application/json              |
| apierrors.APIError            | 4XX, 5XX                      | \*/\*                         |

## DeleteCustomer

Use when removing a customer (e.g. GDPR or churn). Returns 204 No Content on success.

### Example Usage

<!-- UsageSnippet language="go" operationID="deleteCustomer" method="delete" path="/customers/{id}" -->
```go
package main

import(
	"context"
	"undefined"
	"log"
)

func main() {
    ctx := context.Background()

    s := undefined.New(
        "https://api.example.com",
        undefined.WithSecurity("<YOUR_API_KEY_HERE>"),
    )

    res, err := s.Customers.DeleteCustomer(ctx, "<id>")
    if err != nil {
        log.Fatal(err)
    }
    if res != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                | Type                                                     | Required                                                 | Description                                              |
| -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- |
| `ctx`                                                    | [context.Context](https://pkg.go.dev/context#Context)    | :heavy_check_mark:                                       | The context to use for the request.                      |
| `id`                                                     | *string*                                                 | :heavy_check_mark:                                       | Customer ID                                              |
| `opts`                                                   | [][operations.Option](../../models/operations/option.md) | :heavy_minus_sign:                                       | The options for this request.                            |

### Response

**[*operations.DeleteCustomerResponse](../../models/operations/deletecustomerresponse.md), error**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| apierrors.ErrorsErrorResponse | 400                           | application/json              |
| apierrors.ErrorsErrorResponse | 500                           | application/json              |
| apierrors.APIError            | 4XX, 5XX                      | \*/\*                         |

## GetCustomerEntitlements

Use when checking what a customer can access (e.g. feature gating or usage limits). Supports optional filters (feature_ids, subscription_ids).

### Example Usage

<!-- UsageSnippet language="go" operationID="getCustomerEntitlements" method="get" path="/customers/{id}/entitlements" -->
```go
package main

import(
	"context"
	"undefined"
	"log"
)

func main() {
    ctx := context.Background()

    s := undefined.New(
        "https://api.example.com",
        undefined.WithSecurity("<YOUR_API_KEY_HERE>"),
    )

    res, err := s.Customers.GetCustomerEntitlements(ctx, "<id>")
    if err != nil {
        log.Fatal(err)
    }
    if res.DtoCustomerEntitlementsResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                | Type                                                     | Required                                                 | Description                                              |
| -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- |
| `ctx`                                                    | [context.Context](https://pkg.go.dev/context#Context)    | :heavy_check_mark:                                       | The context to use for the request.                      |
| `id`                                                     | *string*                                                 | :heavy_check_mark:                                       | Customer ID                                              |
| `opts`                                                   | [][operations.Option](../../models/operations/option.md) | :heavy_minus_sign:                                       | The options for this request.                            |

### Response

**[*operations.GetCustomerEntitlementsResponse](../../models/operations/getcustomerentitlementsresponse.md), error**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| apierrors.ErrorsErrorResponse | 400                           | application/json              |
| apierrors.ErrorsErrorResponse | 500                           | application/json              |
| apierrors.APIError            | 4XX, 5XX                      | \*/\*                         |

## GetCustomerUpcomingGrants

Use when showing upcoming or pending credits for a customer (e.g. in a portal or for forecasting).

### Example Usage

<!-- UsageSnippet language="go" operationID="getCustomerUpcomingGrants" method="get" path="/customers/{id}/grants/upcoming" -->
```go
package main

import(
	"context"
	"undefined"
	"log"
)

func main() {
    ctx := context.Background()

    s := undefined.New(
        "https://api.example.com",
        undefined.WithSecurity("<YOUR_API_KEY_HERE>"),
    )

    res, err := s.Customers.GetCustomerUpcomingGrants(ctx, "<id>")
    if err != nil {
        log.Fatal(err)
    }
    if res.DtoListCreditGrantApplicationsResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                | Type                                                     | Required                                                 | Description                                              |
| -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- |
| `ctx`                                                    | [context.Context](https://pkg.go.dev/context#Context)    | :heavy_check_mark:                                       | The context to use for the request.                      |
| `id`                                                     | *string*                                                 | :heavy_check_mark:                                       | Customer ID                                              |
| `opts`                                                   | [][operations.Option](../../models/operations/option.md) | :heavy_minus_sign:                                       | The options for this request.                            |

### Response

**[*operations.GetCustomerUpcomingGrantsResponse](../../models/operations/getcustomerupcominggrantsresponse.md), error**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| apierrors.ErrorsErrorResponse | 400, 404                      | application/json              |
| apierrors.ErrorsErrorResponse | 500                           | application/json              |
| apierrors.APIError            | 4XX, 5XX                      | \*/\*                         |