# Integrations

## Overview

### Available Operations

* [GetIntegration](#getintegration) - Get integration details
* [CreateOrUpdateIntegration](#createorupdateintegration) - Create or update an integration
* [ListLinkedIntegrations](#listlinkedintegrations) - List linked integrations
* [DeleteIntegration](#deleteintegration) - Delete an integration

## GetIntegration

Use when you need to check or display integration config (e.g. which provider is linked). Sensitive values may be redacted.

### Example Usage

<!-- UsageSnippet language="go" operationID="getIntegration" method="get" path="/secrets/integrations/by-provider/{provider}" -->
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

    res, err := s.Integrations.GetIntegration(ctx, "<value>")
    if err != nil {
        log.Fatal(err)
    }
    if res.DtoSecretResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                | Type                                                     | Required                                                 | Description                                              |
| -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- |
| `ctx`                                                    | [context.Context](https://pkg.go.dev/context#Context)    | :heavy_check_mark:                                       | The context to use for the request.                      |
| `provider`                                               | *string*                                                 | :heavy_check_mark:                                       | Integration provider                                     |
| `opts`                                                   | [][operations.Option](../../models/operations/option.md) | :heavy_minus_sign:                                       | The options for this request.                            |

### Response

**[*operations.GetIntegrationResponse](../../models/operations/getintegrationresponse.md), error**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| apierrors.ErrorsErrorResponse | 404                           | application/json              |
| apierrors.ErrorsErrorResponse | 500                           | application/json              |
| apierrors.APIError            | 4XX, 5XX                      | \*/\*                         |

## CreateOrUpdateIntegration

Use when storing or updating credentials for an external integration (e.g. Stripe, HubSpot). Secrets are encrypted at rest.

### Example Usage

<!-- UsageSnippet language="go" operationID="createOrUpdateIntegration" method="post" path="/secrets/integrations/create/{provider}" -->
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

    res, err := s.Integrations.CreateOrUpdateIntegration(ctx, "<value>", components.DtoCreateIntegrationRequest{
        Credentials: map[string]string{
            "key": "<value>",
        },
        Name: "<value>",
        Provider: components.TypesSecretProviderChargebee,
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.DtoSecretResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                        | Type                                                                                             | Required                                                                                         | Description                                                                                      |
| ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------ |
| `ctx`                                                                                            | [context.Context](https://pkg.go.dev/context#Context)                                            | :heavy_check_mark:                                                                               | The context to use for the request.                                                              |
| `provider`                                                                                       | *string*                                                                                         | :heavy_check_mark:                                                                               | Integration provider                                                                             |
| `body`                                                                                           | [components.DtoCreateIntegrationRequest](../../models/components/dtocreateintegrationrequest.md) | :heavy_check_mark:                                                                               | Integration creation request                                                                     |
| `opts`                                                                                           | [][operations.Option](../../models/operations/option.md)                                         | :heavy_minus_sign:                                                                               | The options for this request.                                                                    |

### Response

**[*operations.CreateOrUpdateIntegrationResponse](../../models/operations/createorupdateintegrationresponse.md), error**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| apierrors.ErrorsErrorResponse | 400                           | application/json              |
| apierrors.ErrorsErrorResponse | 500                           | application/json              |
| apierrors.APIError            | 4XX, 5XX                      | \*/\*                         |

## ListLinkedIntegrations

Use when showing which integrations are connected (e.g. settings page). Returns providers that have valid linked credentials.

### Example Usage

<!-- UsageSnippet language="go" operationID="listLinkedIntegrations" method="get" path="/secrets/integrations/linked" -->
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

    res, err := s.Integrations.ListLinkedIntegrations(ctx)
    if err != nil {
        log.Fatal(err)
    }
    if res.DtoLinkedIntegrationsResponse != nil {
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

**[*operations.ListLinkedIntegrationsResponse](../../models/operations/listlinkedintegrationsresponse.md), error**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| apierrors.ErrorsErrorResponse | 500                           | application/json              |
| apierrors.APIError            | 4XX, 5XX                      | \*/\*                         |

## DeleteIntegration

Use when disconnecting an integration (e.g. switching provider or removing OAuth). Deletes stored credentials.

### Example Usage

<!-- UsageSnippet language="go" operationID="deleteIntegration" method="delete" path="/secrets/integrations/{id}" -->
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

    res, err := s.Integrations.DeleteIntegration(ctx, "<id>")
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
| `id`                                                     | *string*                                                 | :heavy_check_mark:                                       | Integration ID                                           |
| `opts`                                                   | [][operations.Option](../../models/operations/option.md) | :heavy_minus_sign:                                       | The options for this request.                            |

### Response

**[*operations.DeleteIntegrationResponse](../../models/operations/deleteintegrationresponse.md), error**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| apierrors.ErrorsErrorResponse | 404                           | application/json              |
| apierrors.ErrorsErrorResponse | 500                           | application/json              |
| apierrors.APIError            | 4XX, 5XX                      | \*/\*                         |