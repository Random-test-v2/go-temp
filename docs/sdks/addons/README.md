# Addons

## Overview

### Available Operations

* [CreateAddon](#createaddon) - Create addon
* [GetAddonByLookupKey](#getaddonbylookupkey) - Get addon by lookup key
* [QueryAddon](#queryaddon) - Query addons
* [GetAddon](#getaddon) - Get addon
* [UpdateAddon](#updateaddon) - Update addon
* [DeleteAddon](#deleteaddon) - Delete addon

## CreateAddon

Use when defining an optional purchasable item (e.g. extra storage or support tier). Ideal for add-ons that customers can attach to a subscription.

### Example Usage

<!-- UsageSnippet language="go" operationID="createAddon" method="post" path="/addons" -->
```go
package main

import(
	"context"
	flexprice "github.com/flexprice/flexprice-go"
	"github.com/flexprice/flexprice-go/models/components"
	"log"
)

func main() {
    ctx := context.Background()

    s := flexprice.New(
        "https://api.example.com",
        flexprice.WithSecurity("<YOUR_API_KEY_HERE>"),
    )

    res, err := s.Addons.CreateAddon(ctx, components.DtoCreateAddonRequest{
        LookupKey: "<value>",
        Name: "<value>",
        Type: components.TypesAddonTypeMultipleInstance,
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.DtoCreateAddonResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                            | Type                                                                                 | Required                                                                             | Description                                                                          |
| ------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------ |
| `ctx`                                                                                | [context.Context](https://pkg.go.dev/context#Context)                                | :heavy_check_mark:                                                                   | The context to use for the request.                                                  |
| `request`                                                                            | [components.DtoCreateAddonRequest](../../models/components/dtocreateaddonrequest.md) | :heavy_check_mark:                                                                   | The request object to use for the request.                                           |
| `opts`                                                                               | [][operations.Option](../../models/operations/option.md)                             | :heavy_minus_sign:                                                                   | The options for this request.                                                        |

### Response

**[*operations.CreateAddonResponse](../../models/operations/createaddonresponse.md), error**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| apierrors.ErrorsErrorResponse | 400                           | application/json              |
| apierrors.ErrorsErrorResponse | 500                           | application/json              |
| apierrors.APIError            | 4XX, 5XX                      | \*/\*                         |

## GetAddonByLookupKey

Use when resolving an addon by external id (e.g. from your product catalog). Ideal for integrations.

### Example Usage

<!-- UsageSnippet language="go" operationID="getAddonByLookupKey" method="get" path="/addons/lookup/{lookup_key}" -->
```go
package main

import(
	"context"
	flexprice "github.com/flexprice/flexprice-go"
	"log"
)

func main() {
    ctx := context.Background()

    s := flexprice.New(
        "https://api.example.com",
        flexprice.WithSecurity("<YOUR_API_KEY_HERE>"),
    )

    res, err := s.Addons.GetAddonByLookupKey(ctx, "<value>")
    if err != nil {
        log.Fatal(err)
    }
    if res.DtoAddonResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                | Type                                                     | Required                                                 | Description                                              |
| -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- |
| `ctx`                                                    | [context.Context](https://pkg.go.dev/context#Context)    | :heavy_check_mark:                                       | The context to use for the request.                      |
| `lookupKey`                                              | *string*                                                 | :heavy_check_mark:                                       | Addon Lookup Key                                         |
| `opts`                                                   | [][operations.Option](../../models/operations/option.md) | :heavy_minus_sign:                                       | The options for this request.                            |

### Response

**[*operations.GetAddonByLookupKeyResponse](../../models/operations/getaddonbylookupkeyresponse.md), error**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| apierrors.ErrorsErrorResponse | 400                           | application/json              |
| apierrors.ErrorsErrorResponse | 500                           | application/json              |
| apierrors.APIError            | 4XX, 5XX                      | \*/\*                         |

## QueryAddon

Use when listing or searching addons (e.g. catalog or subscription builder). Returns a paginated list; supports filtering and sorting.

### Example Usage

<!-- UsageSnippet language="go" operationID="queryAddon" method="post" path="/addons/search" -->
```go
package main

import(
	"context"
	flexprice "github.com/flexprice/flexprice-go"
	"github.com/flexprice/flexprice-go/models/components"
	"log"
)

func main() {
    ctx := context.Background()

    s := flexprice.New(
        "https://api.example.com",
        flexprice.WithSecurity("<YOUR_API_KEY_HERE>"),
    )

    res, err := s.Addons.QueryAddon(ctx, components.TypesAddonFilter{})
    if err != nil {
        log.Fatal(err)
    }
    if res.DtoListAddonsResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                  | Type                                                                       | Required                                                                   | Description                                                                |
| -------------------------------------------------------------------------- | -------------------------------------------------------------------------- | -------------------------------------------------------------------------- | -------------------------------------------------------------------------- |
| `ctx`                                                                      | [context.Context](https://pkg.go.dev/context#Context)                      | :heavy_check_mark:                                                         | The context to use for the request.                                        |
| `request`                                                                  | [components.TypesAddonFilter](../../models/components/typesaddonfilter.md) | :heavy_check_mark:                                                         | The request object to use for the request.                                 |
| `opts`                                                                     | [][operations.Option](../../models/operations/option.md)                   | :heavy_minus_sign:                                                         | The options for this request.                                              |

### Response

**[*operations.QueryAddonResponse](../../models/operations/queryaddonresponse.md), error**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| apierrors.ErrorsErrorResponse | 400                           | application/json              |
| apierrors.ErrorsErrorResponse | 500                           | application/json              |
| apierrors.APIError            | 4XX, 5XX                      | \*/\*                         |

## GetAddon

Use when you need to load a single addon (e.g. for display or to attach to a subscription).

### Example Usage

<!-- UsageSnippet language="go" operationID="getAddon" method="get" path="/addons/{id}" -->
```go
package main

import(
	"context"
	flexprice "github.com/flexprice/flexprice-go"
	"log"
)

func main() {
    ctx := context.Background()

    s := flexprice.New(
        "https://api.example.com",
        flexprice.WithSecurity("<YOUR_API_KEY_HERE>"),
    )

    res, err := s.Addons.GetAddon(ctx, "<id>")
    if err != nil {
        log.Fatal(err)
    }
    if res.DtoAddonResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                | Type                                                     | Required                                                 | Description                                              |
| -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- |
| `ctx`                                                    | [context.Context](https://pkg.go.dev/context#Context)    | :heavy_check_mark:                                       | The context to use for the request.                      |
| `id`                                                     | *string*                                                 | :heavy_check_mark:                                       | Addon ID                                                 |
| `opts`                                                   | [][operations.Option](../../models/operations/option.md) | :heavy_minus_sign:                                       | The options for this request.                            |

### Response

**[*operations.GetAddonResponse](../../models/operations/getaddonresponse.md), error**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| apierrors.ErrorsErrorResponse | 400                           | application/json              |
| apierrors.ErrorsErrorResponse | 500                           | application/json              |
| apierrors.APIError            | 4XX, 5XX                      | \*/\*                         |

## UpdateAddon

Use when changing addon details (e.g. name, pricing, or metadata).

### Example Usage

<!-- UsageSnippet language="go" operationID="updateAddon" method="put" path="/addons/{id}" -->
```go
package main

import(
	"context"
	flexprice "github.com/flexprice/flexprice-go"
	"github.com/flexprice/flexprice-go/models/components"
	"log"
)

func main() {
    ctx := context.Background()

    s := flexprice.New(
        "https://api.example.com",
        flexprice.WithSecurity("<YOUR_API_KEY_HERE>"),
    )

    res, err := s.Addons.UpdateAddon(ctx, "<id>", components.DtoUpdateAddonRequest{})
    if err != nil {
        log.Fatal(err)
    }
    if res.DtoAddonResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                            | Type                                                                                 | Required                                                                             | Description                                                                          |
| ------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------ |
| `ctx`                                                                                | [context.Context](https://pkg.go.dev/context#Context)                                | :heavy_check_mark:                                                                   | The context to use for the request.                                                  |
| `id`                                                                                 | *string*                                                                             | :heavy_check_mark:                                                                   | Addon ID                                                                             |
| `body`                                                                               | [components.DtoUpdateAddonRequest](../../models/components/dtoupdateaddonrequest.md) | :heavy_check_mark:                                                                   | Update Addon Request                                                                 |
| `opts`                                                                               | [][operations.Option](../../models/operations/option.md)                             | :heavy_minus_sign:                                                                   | The options for this request.                                                        |

### Response

**[*operations.UpdateAddonResponse](../../models/operations/updateaddonresponse.md), error**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| apierrors.ErrorsErrorResponse | 400                           | application/json              |
| apierrors.ErrorsErrorResponse | 500                           | application/json              |
| apierrors.APIError            | 4XX, 5XX                      | \*/\*                         |

## DeleteAddon

Use when retiring an addon (e.g. end-of-life). Returns 200 with success message.

### Example Usage

<!-- UsageSnippet language="go" operationID="deleteAddon" method="delete" path="/addons/{id}" -->
```go
package main

import(
	"context"
	flexprice "github.com/flexprice/flexprice-go"
	"log"
)

func main() {
    ctx := context.Background()

    s := flexprice.New(
        "https://api.example.com",
        flexprice.WithSecurity("<YOUR_API_KEY_HERE>"),
    )

    res, err := s.Addons.DeleteAddon(ctx, "<id>")
    if err != nil {
        log.Fatal(err)
    }
    if res.DtoSuccessResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                | Type                                                     | Required                                                 | Description                                              |
| -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- |
| `ctx`                                                    | [context.Context](https://pkg.go.dev/context#Context)    | :heavy_check_mark:                                       | The context to use for the request.                      |
| `id`                                                     | *string*                                                 | :heavy_check_mark:                                       | Addon ID                                                 |
| `opts`                                                   | [][operations.Option](../../models/operations/option.md) | :heavy_minus_sign:                                       | The options for this request.                            |

### Response

**[*operations.DeleteAddonResponse](../../models/operations/deleteaddonresponse.md), error**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| apierrors.ErrorsErrorResponse | 400                           | application/json              |
| apierrors.ErrorsErrorResponse | 500                           | application/json              |
| apierrors.APIError            | 4XX, 5XX                      | \*/\*                         |