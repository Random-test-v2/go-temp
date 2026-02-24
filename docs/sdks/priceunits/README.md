# PriceUnits

## Overview

### Available Operations

* [ListPriceUnits](#listpriceunits) - List price units
* [CreatePriceUnit](#createpriceunit) - Create price unit
* [GetPriceUnitByCode](#getpriceunitbycode) - Get price unit by code
* [QueryPriceUnit](#querypriceunit) - Query price units
* [GetPriceUnit](#getpriceunit) - Get price unit
* [UpdatePriceUnit](#updatepriceunit) - Update price unit
* [DeletePriceUnit](#deletepriceunit) - Delete price unit

## ListPriceUnits

Use when listing price units (e.g. in a catalog or when creating prices). Returns a paginated list; supports status, sort, and pagination.

### Example Usage

<!-- UsageSnippet language="go" operationID="listPriceUnits" method="get" path="/prices/units" -->
```go
package main

import(
	"context"
	flexprice "github.com/flexprice/flexprice-go"
	"github.com/flexprice/flexprice-go/models/operations"
	"log"
)

func main() {
    ctx := context.Background()

    s := flexprice.New(
        "https://api.example.com",
        flexprice.WithSecurity("<YOUR_API_KEY_HERE>"),
    )

    res, err := s.PriceUnits.ListPriceUnits(ctx, operations.ListPriceUnitsRequest{})
    if err != nil {
        log.Fatal(err)
    }
    if res.DtoListPriceUnitsResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                            | Type                                                                                 | Required                                                                             | Description                                                                          |
| ------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------ |
| `ctx`                                                                                | [context.Context](https://pkg.go.dev/context#Context)                                | :heavy_check_mark:                                                                   | The context to use for the request.                                                  |
| `request`                                                                            | [operations.ListPriceUnitsRequest](../../models/operations/listpriceunitsrequest.md) | :heavy_check_mark:                                                                   | The request object to use for the request.                                           |
| `opts`                                                                               | [][operations.Option](../../models/operations/option.md)                             | :heavy_minus_sign:                                                                   | The options for this request.                                                        |

### Response

**[*operations.ListPriceUnitsResponse](../../models/operations/listpriceunitsresponse.md), error**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| apierrors.ErrorsErrorResponse | 400                           | application/json              |
| apierrors.ErrorsErrorResponse | 500                           | application/json              |
| apierrors.APIError            | 4XX, 5XX                      | \*/\*                         |

## CreatePriceUnit

Use when defining a new unit of measure for pricing (e.g. GB, API call, seat). Ideal for metered or usage-based prices.

### Example Usage

<!-- UsageSnippet language="go" operationID="createPriceUnit" method="post" path="/prices/units" -->
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

    res, err := s.PriceUnits.CreatePriceUnit(ctx, components.DtoCreatePriceUnitRequest{
        BaseCurrency: "<value>",
        Code: "<value>",
        ConversionRate: "<value>",
        Name: "<value>",
        Symbol: "<value>",
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.DtoCreatePriceUnitResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                    | Type                                                                                         | Required                                                                                     | Description                                                                                  |
| -------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------- |
| `ctx`                                                                                        | [context.Context](https://pkg.go.dev/context#Context)                                        | :heavy_check_mark:                                                                           | The context to use for the request.                                                          |
| `request`                                                                                    | [components.DtoCreatePriceUnitRequest](../../models/components/dtocreatepriceunitrequest.md) | :heavy_check_mark:                                                                           | The request object to use for the request.                                                   |
| `opts`                                                                                       | [][operations.Option](../../models/operations/option.md)                                     | :heavy_minus_sign:                                                                           | The options for this request.                                                                |

### Response

**[*operations.CreatePriceUnitResponse](../../models/operations/createpriceunitresponse.md), error**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| apierrors.ErrorsErrorResponse | 400                           | application/json              |
| apierrors.ErrorsErrorResponse | 500                           | application/json              |
| apierrors.APIError            | 4XX, 5XX                      | \*/\*                         |

## GetPriceUnitByCode

Use when resolving a price unit by code (e.g. from an external catalog or config). Ideal for integrations.

### Example Usage

<!-- UsageSnippet language="go" operationID="getPriceUnitByCode" method="get" path="/prices/units/code/{code}" -->
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

    res, err := s.PriceUnits.GetPriceUnitByCode(ctx, "<value>")
    if err != nil {
        log.Fatal(err)
    }
    if res.DtoPriceUnitResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                | Type                                                     | Required                                                 | Description                                              |
| -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- |
| `ctx`                                                    | [context.Context](https://pkg.go.dev/context#Context)    | :heavy_check_mark:                                       | The context to use for the request.                      |
| `code`                                                   | *string*                                                 | :heavy_check_mark:                                       | Price unit code                                          |
| `opts`                                                   | [][operations.Option](../../models/operations/option.md) | :heavy_minus_sign:                                       | The options for this request.                            |

### Response

**[*operations.GetPriceUnitByCodeResponse](../../models/operations/getpriceunitbycoderesponse.md), error**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| apierrors.ErrorsErrorResponse | 400, 404                      | application/json              |
| apierrors.ErrorsErrorResponse | 500                           | application/json              |
| apierrors.APIError            | 4XX, 5XX                      | \*/\*                         |

## QueryPriceUnit

Use when searching or listing price units (e.g. admin catalog). Returns a paginated list; supports filtering and sorting.

### Example Usage

<!-- UsageSnippet language="go" operationID="queryPriceUnit" method="post" path="/prices/units/search" -->
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

    res, err := s.PriceUnits.QueryPriceUnit(ctx, components.TypesPriceUnitFilter{})
    if err != nil {
        log.Fatal(err)
    }
    if res.DtoListPriceUnitsResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                          | Type                                                                               | Required                                                                           | Description                                                                        |
| ---------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- |
| `ctx`                                                                              | [context.Context](https://pkg.go.dev/context#Context)                              | :heavy_check_mark:                                                                 | The context to use for the request.                                                |
| `request`                                                                          | [components.TypesPriceUnitFilter](../../models/components/typespriceunitfilter.md) | :heavy_check_mark:                                                                 | The request object to use for the request.                                         |
| `opts`                                                                             | [][operations.Option](../../models/operations/option.md)                           | :heavy_minus_sign:                                                                 | The options for this request.                                                      |

### Response

**[*operations.QueryPriceUnitResponse](../../models/operations/querypriceunitresponse.md), error**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| apierrors.ErrorsErrorResponse | 400                           | application/json              |
| apierrors.ErrorsErrorResponse | 500                           | application/json              |
| apierrors.APIError            | 4XX, 5XX                      | \*/\*                         |

## GetPriceUnit

Use when you need to load a single price unit (e.g. for display or when creating a price).

### Example Usage

<!-- UsageSnippet language="go" operationID="getPriceUnit" method="get" path="/prices/units/{id}" -->
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

    res, err := s.PriceUnits.GetPriceUnit(ctx, "<id>")
    if err != nil {
        log.Fatal(err)
    }
    if res.DtoPriceUnitResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                | Type                                                     | Required                                                 | Description                                              |
| -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- |
| `ctx`                                                    | [context.Context](https://pkg.go.dev/context#Context)    | :heavy_check_mark:                                       | The context to use for the request.                      |
| `id`                                                     | *string*                                                 | :heavy_check_mark:                                       | Price unit ID                                            |
| `opts`                                                   | [][operations.Option](../../models/operations/option.md) | :heavy_minus_sign:                                       | The options for this request.                            |

### Response

**[*operations.GetPriceUnitResponse](../../models/operations/getpriceunitresponse.md), error**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| apierrors.ErrorsErrorResponse | 400, 404                      | application/json              |
| apierrors.APIError            | 4XX, 5XX                      | \*/\*                         |

## UpdatePriceUnit

Use when renaming or updating metadata for a price unit. Code is immutable once created.

### Example Usage

<!-- UsageSnippet language="go" operationID="updatePriceUnit" method="put" path="/prices/units/{id}" -->
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

    res, err := s.PriceUnits.UpdatePriceUnit(ctx, "<id>", components.DtoUpdatePriceUnitRequest{})
    if err != nil {
        log.Fatal(err)
    }
    if res.DtoPriceUnitResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                    | Type                                                                                         | Required                                                                                     | Description                                                                                  |
| -------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------- |
| `ctx`                                                                                        | [context.Context](https://pkg.go.dev/context#Context)                                        | :heavy_check_mark:                                                                           | The context to use for the request.                                                          |
| `id`                                                                                         | *string*                                                                                     | :heavy_check_mark:                                                                           | Price unit ID                                                                                |
| `body`                                                                                       | [components.DtoUpdatePriceUnitRequest](../../models/components/dtoupdatepriceunitrequest.md) | :heavy_check_mark:                                                                           | Price unit details to update                                                                 |
| `opts`                                                                                       | [][operations.Option](../../models/operations/option.md)                                     | :heavy_minus_sign:                                                                           | The options for this request.                                                                |

### Response

**[*operations.UpdatePriceUnitResponse](../../models/operations/updatepriceunitresponse.md), error**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| apierrors.ErrorsErrorResponse | 400, 404                      | application/json              |
| apierrors.APIError            | 4XX, 5XX                      | \*/\*                         |

## DeletePriceUnit

Use when removing a price unit that is no longer needed. Fails if any price references this unit.

### Example Usage

<!-- UsageSnippet language="go" operationID="deletePriceUnit" method="delete" path="/prices/units/{id}" -->
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

    res, err := s.PriceUnits.DeletePriceUnit(ctx, "<id>")
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
| `id`                                                     | *string*                                                 | :heavy_check_mark:                                       | Price unit ID                                            |
| `opts`                                                   | [][operations.Option](../../models/operations/option.md) | :heavy_minus_sign:                                       | The options for this request.                            |

### Response

**[*operations.DeletePriceUnitResponse](../../models/operations/deletepriceunitresponse.md), error**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| apierrors.ErrorsErrorResponse | 400, 404                      | application/json              |
| apierrors.APIError            | 4XX, 5XX                      | \*/\*                         |