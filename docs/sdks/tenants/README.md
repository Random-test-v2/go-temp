# Tenants

## Overview

### Available Operations

* [GetTenantBillingUsage](#gettenantbillingusage) - Get billing usage for the current tenant
* [CreateTenant](#createtenant) - Create a new tenant
* [UpdateTenant](#updatetenant) - Update a tenant
* [GetTenant](#gettenant) - Get tenant

## GetTenantBillingUsage

Use when showing the current tenant's billing usage (e.g. admin billing page or usage caps). Returns subscription and usage for the tenant.

### Example Usage

<!-- UsageSnippet language="go" operationID="getTenantBillingUsage" method="get" path="/tenant/billing" -->
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

    res, err := s.Tenants.GetTenantBillingUsage(ctx)
    if err != nil {
        log.Fatal(err)
    }
    if res.DtoTenantBillingUsage != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                | Type                                                     | Required                                                 | Description                                              |
| -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- |
| `ctx`                                                    | [context.Context](https://pkg.go.dev/context#Context)    | :heavy_check_mark:                                       | The context to use for the request.                      |
| `opts`                                                   | [][operations.Option](../../models/operations/option.md) | :heavy_minus_sign:                                       | The options for this request.                            |

### Response

**[*operations.GetTenantBillingUsageResponse](../../models/operations/gettenantbillingusageresponse.md), error**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| apierrors.ErrorsErrorResponse | 400, 404                      | application/json              |
| apierrors.ErrorsErrorResponse | 500                           | application/json              |
| apierrors.APIError            | 4XX, 5XX                      | \*/\*                         |

## CreateTenant

Use when provisioning a new tenant (e.g. new org or workspace). Tenants are top-level isolation boundaries.

### Example Usage

<!-- UsageSnippet language="go" operationID="createTenant" method="post" path="/tenants" -->
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

    res, err := s.Tenants.CreateTenant(ctx, components.DtoCreateTenantRequest{
        Name: "<value>",
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.DtoTenantResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                              | Type                                                                                   | Required                                                                               | Description                                                                            |
| -------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- |
| `ctx`                                                                                  | [context.Context](https://pkg.go.dev/context#Context)                                  | :heavy_check_mark:                                                                     | The context to use for the request.                                                    |
| `request`                                                                              | [components.DtoCreateTenantRequest](../../models/components/dtocreatetenantrequest.md) | :heavy_check_mark:                                                                     | The request object to use for the request.                                             |
| `opts`                                                                                 | [][operations.Option](../../models/operations/option.md)                               | :heavy_minus_sign:                                                                     | The options for this request.                                                          |

### Response

**[*operations.CreateTenantResponse](../../models/operations/createtenantresponse.md), error**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| apierrors.ErrorsErrorResponse | 400                           | application/json              |
| apierrors.ErrorsErrorResponse | 500                           | application/json              |
| apierrors.APIError            | 4XX, 5XX                      | \*/\*                         |

## UpdateTenant

Use when changing tenant details (e.g. name or billing info). Request body contains the fields to update.

### Example Usage

<!-- UsageSnippet language="go" operationID="updateTenant" method="put" path="/tenants/update" -->
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

    res, err := s.Tenants.UpdateTenant(ctx, components.DtoUpdateTenantRequest{})
    if err != nil {
        log.Fatal(err)
    }
    if res.DtoTenantResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                              | Type                                                                                   | Required                                                                               | Description                                                                            |
| -------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- |
| `ctx`                                                                                  | [context.Context](https://pkg.go.dev/context#Context)                                  | :heavy_check_mark:                                                                     | The context to use for the request.                                                    |
| `request`                                                                              | [components.DtoUpdateTenantRequest](../../models/components/dtoupdatetenantrequest.md) | :heavy_check_mark:                                                                     | The request object to use for the request.                                             |
| `opts`                                                                                 | [][operations.Option](../../models/operations/option.md)                               | :heavy_minus_sign:                                                                     | The options for this request.                                                          |

### Response

**[*operations.UpdateTenantResponse](../../models/operations/updatetenantresponse.md), error**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| apierrors.ErrorsErrorResponse | 400, 404                      | application/json              |
| apierrors.ErrorsErrorResponse | 500                           | application/json              |
| apierrors.APIError            | 4XX, 5XX                      | \*/\*                         |

## GetTenant

Use when you need to load a single tenant (e.g. for display or to check billing). Typically used in admin or multi-tenant contexts.

### Example Usage

<!-- UsageSnippet language="go" operationID="getTenant" method="get" path="/tenants/{id}" -->
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

    res, err := s.Tenants.GetTenant(ctx, "<id>")
    if err != nil {
        log.Fatal(err)
    }
    if res.DtoTenantResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                | Type                                                     | Required                                                 | Description                                              |
| -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- |
| `ctx`                                                    | [context.Context](https://pkg.go.dev/context#Context)    | :heavy_check_mark:                                       | The context to use for the request.                      |
| `id`                                                     | *string*                                                 | :heavy_check_mark:                                       | Tenant ID                                                |
| `opts`                                                   | [][operations.Option](../../models/operations/option.md) | :heavy_minus_sign:                                       | The options for this request.                            |

### Response

**[*operations.GetTenantResponse](../../models/operations/gettenantresponse.md), error**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| apierrors.ErrorsErrorResponse | 404                           | application/json              |
| apierrors.ErrorsErrorResponse | 500                           | application/json              |
| apierrors.APIError            | 4XX, 5XX                      | \*/\*                         |