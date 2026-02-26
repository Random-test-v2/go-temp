# Environments

## Overview

### Available Operations

* [CreateEnvironment](#createenvironment) - Create environment
* [UpdateEnvironment](#updateenvironment) - Update environment

## CreateEnvironment

Use when setting up a new environment (e.g. production, staging) for the tenant. Ideal for separating billing or config per environment.

### Example Usage

<!-- UsageSnippet language="go" operationID="createEnvironment" method="post" path="/environments" -->
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

    res, err := s.Environments.CreateEnvironment(ctx, components.DtoCreateEnvironmentRequest{
        Name: "<value>",
        Type: "<value>",
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.DtoEnvironmentResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                        | Type                                                                                             | Required                                                                                         | Description                                                                                      |
| ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------ |
| `ctx`                                                                                            | [context.Context](https://pkg.go.dev/context#Context)                                            | :heavy_check_mark:                                                                               | The context to use for the request.                                                              |
| `request`                                                                                        | [components.DtoCreateEnvironmentRequest](../../models/components/dtocreateenvironmentrequest.md) | :heavy_check_mark:                                                                               | The request object to use for the request.                                                       |
| `opts`                                                                                           | [][operations.Option](../../models/operations/option.md)                                         | :heavy_minus_sign:                                                                               | The options for this request.                                                                    |

### Response

**[*operations.CreateEnvironmentResponse](../../models/operations/createenvironmentresponse.md), error**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| apierrors.ErrorsErrorResponse | 400                           | application/json              |
| apierrors.ErrorsErrorResponse | 500                           | application/json              |
| apierrors.APIError            | 4XX, 5XX                      | \*/\*                         |

## UpdateEnvironment

Use when changing environment name or settings (e.g. renaming or updating metadata).

### Example Usage

<!-- UsageSnippet language="go" operationID="updateEnvironment" method="put" path="/environments/{id}" -->
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

    res, err := s.Environments.UpdateEnvironment(ctx, "<id>", components.DtoUpdateEnvironmentRequest{})
    if err != nil {
        log.Fatal(err)
    }
    if res.DtoEnvironmentResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                        | Type                                                                                             | Required                                                                                         | Description                                                                                      |
| ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------ |
| `ctx`                                                                                            | [context.Context](https://pkg.go.dev/context#Context)                                            | :heavy_check_mark:                                                                               | The context to use for the request.                                                              |
| `id`                                                                                             | *string*                                                                                         | :heavy_check_mark:                                                                               | Environment ID                                                                                   |
| `body`                                                                                           | [components.DtoUpdateEnvironmentRequest](../../models/components/dtoupdateenvironmentrequest.md) | :heavy_check_mark:                                                                               | Environment                                                                                      |
| `opts`                                                                                           | [][operations.Option](../../models/operations/option.md)                                         | :heavy_minus_sign:                                                                               | The options for this request.                                                                    |

### Response

**[*operations.UpdateEnvironmentResponse](../../models/operations/updateenvironmentresponse.md), error**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| apierrors.ErrorsErrorResponse | 400, 404                      | application/json              |
| apierrors.ErrorsErrorResponse | 500                           | application/json              |
| apierrors.APIError            | 4XX, 5XX                      | \*/\*                         |