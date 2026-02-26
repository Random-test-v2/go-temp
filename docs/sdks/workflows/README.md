# Workflows

## Overview

### Available Operations

* [QueryWorkflow](#queryworkflow) - Query workflows

## QueryWorkflow

Use when listing or auditing workflow runs (e.g. ops dashboard or debugging). Returns a paginated list; supports filtering by workflow type and status.

### Example Usage

<!-- UsageSnippet language="go" operationID="queryWorkflow" method="post" path="/workflows/search" -->
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

    res, err := s.Workflows.QueryWorkflow(ctx, components.TypesWorkflowExecutionFilter{})
    if err != nil {
        log.Fatal(err)
    }
    if res.DtoListWorkflowsResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                          | Type                                                                                               | Required                                                                                           | Description                                                                                        |
| -------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------- |
| `ctx`                                                                                              | [context.Context](https://pkg.go.dev/context#Context)                                              | :heavy_check_mark:                                                                                 | The context to use for the request.                                                                |
| `request`                                                                                          | [components.TypesWorkflowExecutionFilter](../../models/components/typesworkflowexecutionfilter.md) | :heavy_check_mark:                                                                                 | The request object to use for the request.                                                         |
| `opts`                                                                                             | [][operations.Option](../../models/operations/option.md)                                           | :heavy_minus_sign:                                                                                 | The options for this request.                                                                      |

### Response

**[*operations.QueryWorkflowResponse](../../models/operations/queryworkflowresponse.md), error**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| apierrors.ErrorsErrorResponse | 400                           | application/json              |
| apierrors.ErrorsErrorResponse | 500                           | application/json              |
| apierrors.APIError            | 4XX, 5XX                      | \*/\*                         |