# TaxAssociations

## Overview

### Available Operations

* [ListTaxAssociations](#listtaxassociations) - List tax associations
* [CreateTaxAssociation](#createtaxassociation) - Create Tax Association
* [GetTaxAssociation](#gettaxassociation) - Get Tax Association
* [UpdateTaxAssociation](#updatetaxassociation) - Update tax association
* [DeleteTaxAssociation](#deletetaxassociation) - Delete tax association

## ListTaxAssociations

Use when listing tax associations (e.g. tax config or audit). Returns list with optional filtering.

### Example Usage

<!-- UsageSnippet language="go" operationID="listTaxAssociations" method="get" path="/taxes/associations" -->
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

    res, err := s.TaxAssociations.ListTaxAssociations(ctx, nil, nil, nil)
    if err != nil {
        log.Fatal(err)
    }
    if res.DtoListTaxAssociationsResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                | Type                                                     | Required                                                 | Description                                              |
| -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- |
| `ctx`                                                    | [context.Context](https://pkg.go.dev/context#Context)    | :heavy_check_mark:                                       | The context to use for the request.                      |
| `entityType`                                             | **string*                                                | :heavy_minus_sign:                                       | Entity Type                                              |
| `entityID`                                               | **string*                                                | :heavy_minus_sign:                                       | Entity ID                                                |
| `taxRateID`                                              | **string*                                                | :heavy_minus_sign:                                       | Tax Rate ID                                              |
| `opts`                                                   | [][operations.Option](../../models/operations/option.md) | :heavy_minus_sign:                                       | The options for this request.                            |

### Response

**[*operations.ListTaxAssociationsResponse](../../models/operations/listtaxassociationsresponse.md), error**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| apierrors.ErrorsErrorResponse | 400                           | application/json              |
| apierrors.ErrorsErrorResponse | 500                           | application/json              |
| apierrors.APIError            | 4XX, 5XX                      | \*/\*                         |

## CreateTaxAssociation

Use when linking a tax rate to an entity (e.g. customer, product, or region) so that rate applies on invoices.

### Example Usage

<!-- UsageSnippet language="go" operationID="createTaxAssociation" method="post" path="/taxes/associations" -->
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

    res, err := s.TaxAssociations.CreateTaxAssociation(ctx, components.DtoCreateTaxAssociationRequest{
        EntityID: "<id>",
        EntityType: components.TypesTaxRateEntityTypeCustomer,
        TaxRateCode: "<value>",
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.DtoTaxAssociationResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                              | Type                                                                                                   | Required                                                                                               | Description                                                                                            |
| ------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------ |
| `ctx`                                                                                                  | [context.Context](https://pkg.go.dev/context#Context)                                                  | :heavy_check_mark:                                                                                     | The context to use for the request.                                                                    |
| `request`                                                                                              | [components.DtoCreateTaxAssociationRequest](../../models/components/dtocreatetaxassociationrequest.md) | :heavy_check_mark:                                                                                     | The request object to use for the request.                                                             |
| `opts`                                                                                                 | [][operations.Option](../../models/operations/option.md)                                               | :heavy_minus_sign:                                                                                     | The options for this request.                                                                          |

### Response

**[*operations.CreateTaxAssociationResponse](../../models/operations/createtaxassociationresponse.md), error**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| apierrors.ErrorsErrorResponse | 400                           | application/json              |
| apierrors.ErrorsErrorResponse | 500                           | application/json              |
| apierrors.APIError            | 4XX, 5XX                      | \*/\*                         |

## GetTaxAssociation

Use when you need to load a single tax association (e.g. for display or editing).

### Example Usage

<!-- UsageSnippet language="go" operationID="getTaxAssociation" method="get" path="/taxes/associations/{id}" -->
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

    res, err := s.TaxAssociations.GetTaxAssociation(ctx, "<id>")
    if err != nil {
        log.Fatal(err)
    }
    if res.DtoTaxAssociationResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                | Type                                                     | Required                                                 | Description                                              |
| -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- |
| `ctx`                                                    | [context.Context](https://pkg.go.dev/context#Context)    | :heavy_check_mark:                                       | The context to use for the request.                      |
| `id`                                                     | *string*                                                 | :heavy_check_mark:                                       | Tax Config ID                                            |
| `opts`                                                   | [][operations.Option](../../models/operations/option.md) | :heavy_minus_sign:                                       | The options for this request.                            |

### Response

**[*operations.GetTaxAssociationResponse](../../models/operations/gettaxassociationresponse.md), error**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| apierrors.ErrorsErrorResponse | 400                           | application/json              |
| apierrors.ErrorsErrorResponse | 500                           | application/json              |
| apierrors.APIError            | 4XX, 5XX                      | \*/\*                         |

## UpdateTaxAssociation

Use when changing a tax association (e.g. switch rate or entity). Request body contains the fields to update.

### Example Usage

<!-- UsageSnippet language="go" operationID="updateTaxAssociation" method="put" path="/taxes/associations/{id}" -->
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

    res, err := s.TaxAssociations.UpdateTaxAssociation(ctx, "<id>", components.DtoTaxAssociationUpdateRequest{})
    if err != nil {
        log.Fatal(err)
    }
    if res.DtoTaxAssociationResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                              | Type                                                                                                   | Required                                                                                               | Description                                                                                            |
| ------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------ |
| `ctx`                                                                                                  | [context.Context](https://pkg.go.dev/context#Context)                                                  | :heavy_check_mark:                                                                                     | The context to use for the request.                                                                    |
| `id`                                                                                                   | *string*                                                                                               | :heavy_check_mark:                                                                                     | Tax Config ID                                                                                          |
| `body`                                                                                                 | [components.DtoTaxAssociationUpdateRequest](../../models/components/dtotaxassociationupdaterequest.md) | :heavy_check_mark:                                                                                     | Tax Config Request                                                                                     |
| `opts`                                                                                                 | [][operations.Option](../../models/operations/option.md)                                               | :heavy_minus_sign:                                                                                     | The options for this request.                                                                          |

### Response

**[*operations.UpdateTaxAssociationResponse](../../models/operations/updatetaxassociationresponse.md), error**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| apierrors.ErrorsErrorResponse | 400                           | application/json              |
| apierrors.ErrorsErrorResponse | 500                           | application/json              |
| apierrors.APIError            | 4XX, 5XX                      | \*/\*                         |

## DeleteTaxAssociation

Use when removing a tax association (e.g. entity no longer subject to that rate).

### Example Usage

<!-- UsageSnippet language="go" operationID="deleteTaxAssociation" method="delete" path="/taxes/associations/{id}" -->
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

    res, err := s.TaxAssociations.DeleteTaxAssociation(ctx, "<id>")
    if err != nil {
        log.Fatal(err)
    }
    if res.DtoTaxAssociationResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                | Type                                                     | Required                                                 | Description                                              |
| -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- |
| `ctx`                                                    | [context.Context](https://pkg.go.dev/context#Context)    | :heavy_check_mark:                                       | The context to use for the request.                      |
| `id`                                                     | *string*                                                 | :heavy_check_mark:                                       | Tax Config ID                                            |
| `opts`                                                   | [][operations.Option](../../models/operations/option.md) | :heavy_minus_sign:                                       | The options for this request.                            |

### Response

**[*operations.DeleteTaxAssociationResponse](../../models/operations/deletetaxassociationresponse.md), error**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| apierrors.ErrorsErrorResponse | 400                           | application/json              |
| apierrors.ErrorsErrorResponse | 500                           | application/json              |
| apierrors.APIError            | 4XX, 5XX                      | \*/\*                         |