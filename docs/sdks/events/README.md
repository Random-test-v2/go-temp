# Events

## Overview

### Available Operations

* [IngestEvent](#ingestevent) - Ingest event
* [GetUsageAnalytics](#getusageanalytics) - Get usage analytics
* [IngestEventsBulk](#ingesteventsbulk) - Bulk ingest events
* [GetHuggingfaceInferenceData](#gethuggingfaceinferencedata) - Get Hugging Face inference data
* [ListRawEvents](#listrawevents) - List raw events
* [GetUsageStatistics](#getusagestatistics) - Get usage statistics
* [GetUsageByMeter](#getusagebymeter) - Get usage by meter
* [GetEvent](#getevent) - Get event

## IngestEvent

Use when sending a single usage event from your app (e.g. one API call or one GB stored). Events are processed asynchronously; returns 202 with event_id.

### Example Usage

<!-- UsageSnippet language="go" operationID="ingestEvent" method="post" path="/events" -->
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

    res, err := s.Events.IngestEvent(ctx, components.DtoIngestEventRequest{
        CustomerID: undefined.Pointer("customer456"),
        EventID: undefined.Pointer("event123"),
        EventName: "api_request",
        ExternalCustomerID: "customer456",
        Properties: map[string]string{
            ""response_status"": "200}",
            "{"request_size"": "100",
        },
        Source: undefined.Pointer("api"),
        Timestamp: undefined.Pointer("2024-03-20T15:04:05Z"),
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.Object != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                            | Type                                                                                 | Required                                                                             | Description                                                                          |
| ------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------ |
| `ctx`                                                                                | [context.Context](https://pkg.go.dev/context#Context)                                | :heavy_check_mark:                                                                   | The context to use for the request.                                                  |
| `request`                                                                            | [components.DtoIngestEventRequest](../../models/components/dtoingesteventrequest.md) | :heavy_check_mark:                                                                   | The request object to use for the request.                                           |
| `opts`                                                                               | [][operations.Option](../../models/operations/option.md)                             | :heavy_minus_sign:                                                                   | The options for this request.                                                        |

### Response

**[*operations.IngestEventResponse](../../models/operations/ingesteventresponse.md), error**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| apierrors.ErrorsErrorResponse | 400                           | application/json              |
| apierrors.ErrorsErrorResponse | 500                           | application/json              |
| apierrors.APIError            | 4XX, 5XX                      | \*/\*                         |

## GetUsageAnalytics

Use when building analytics views (e.g. usage by feature or customer over time). Supports filtering, grouping, and time-series breakdown.

### Example Usage

<!-- UsageSnippet language="go" operationID="getUsageAnalytics" method="post" path="/events/analytics" -->
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

    res, err := s.Events.GetUsageAnalytics(ctx, components.DtoGetUsageAnalyticsRequest{
        ExternalCustomerID: "<id>",
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.DtoGetUsageAnalyticsResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                        | Type                                                                                             | Required                                                                                         | Description                                                                                      |
| ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------ |
| `ctx`                                                                                            | [context.Context](https://pkg.go.dev/context#Context)                                            | :heavy_check_mark:                                                                               | The context to use for the request.                                                              |
| `request`                                                                                        | [components.DtoGetUsageAnalyticsRequest](../../models/components/dtogetusageanalyticsrequest.md) | :heavy_check_mark:                                                                               | The request object to use for the request.                                                       |
| `opts`                                                                                           | [][operations.Option](../../models/operations/option.md)                                         | :heavy_minus_sign:                                                                               | The options for this request.                                                                    |

### Response

**[*operations.GetUsageAnalyticsResponse](../../models/operations/getusageanalyticsresponse.md), error**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| apierrors.ErrorsErrorResponse | 400                           | application/json              |
| apierrors.ErrorsErrorResponse | 500                           | application/json              |
| apierrors.APIError            | 4XX, 5XX                      | \*/\*                         |

## IngestEventsBulk

Use when batching usage events (e.g. backfill or high-volume ingestion). More efficient than single event calls; returns 202 when accepted.

### Example Usage

<!-- UsageSnippet language="go" operationID="ingestEventsBulk" method="post" path="/events/bulk" -->
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

    res, err := s.Events.IngestEventsBulk(ctx, components.DtoBulkIngestEventRequest{
        Events: []components.DtoIngestEventRequest{},
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.Object != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                    | Type                                                                                         | Required                                                                                     | Description                                                                                  |
| -------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------- |
| `ctx`                                                                                        | [context.Context](https://pkg.go.dev/context#Context)                                        | :heavy_check_mark:                                                                           | The context to use for the request.                                                          |
| `request`                                                                                    | [components.DtoBulkIngestEventRequest](../../models/components/dtobulkingesteventrequest.md) | :heavy_check_mark:                                                                           | The request object to use for the request.                                                   |
| `opts`                                                                                       | [][operations.Option](../../models/operations/option.md)                                     | :heavy_minus_sign:                                                                           | The options for this request.                                                                |

### Response

**[*operations.IngestEventsBulkResponse](../../models/operations/ingesteventsbulkresponse.md), error**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| apierrors.ErrorsErrorResponse | 400                           | application/json              |
| apierrors.ErrorsErrorResponse | 500                           | application/json              |
| apierrors.APIError            | 4XX, 5XX                      | \*/\*                         |

## GetHuggingfaceInferenceData

Use when fetching Hugging Face inference usage or billing data (e.g. for HF-specific reporting or reconciliation).

### Example Usage

<!-- UsageSnippet language="go" operationID="getHuggingfaceInferenceData" method="post" path="/events/huggingface-inference" -->
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

    res, err := s.Events.GetHuggingfaceInferenceData(ctx)
    if err != nil {
        log.Fatal(err)
    }
    if res.DtoGetHuggingFaceBillingDataResponse != nil {
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

**[*operations.GetHuggingfaceInferenceDataResponse](../../models/operations/gethuggingfaceinferencedataresponse.md), error**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| apierrors.ErrorsErrorResponse | 500                           | application/json              |
| apierrors.APIError            | 4XX, 5XX                      | \*/\*                         |

## ListRawEvents

Use when debugging ingestion or exporting raw event data (e.g. support or audit). Returns a paginated list; supports time range and sorting.

### Example Usage

<!-- UsageSnippet language="go" operationID="listRawEvents" method="post" path="/events/query" -->
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

    res, err := s.Events.ListRawEvents(ctx, components.DtoGetEventsRequest{
        EndTime: undefined.Pointer("2024-12-09T00:00:00Z"),
        Order: undefined.Pointer("desc"),
        Sort: undefined.Pointer("timestamp"),
        StartTime: undefined.Pointer("2024-11-09T00:00:00Z"),
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.DtoGetEventsResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                        | Type                                                                             | Required                                                                         | Description                                                                      |
| -------------------------------------------------------------------------------- | -------------------------------------------------------------------------------- | -------------------------------------------------------------------------------- | -------------------------------------------------------------------------------- |
| `ctx`                                                                            | [context.Context](https://pkg.go.dev/context#Context)                            | :heavy_check_mark:                                                               | The context to use for the request.                                              |
| `request`                                                                        | [components.DtoGetEventsRequest](../../models/components/dtogeteventsrequest.md) | :heavy_check_mark:                                                               | The request object to use for the request.                                       |
| `opts`                                                                           | [][operations.Option](../../models/operations/option.md)                         | :heavy_minus_sign:                                                               | The options for this request.                                                    |

### Response

**[*operations.ListRawEventsResponse](../../models/operations/listraweventsresponse.md), error**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| apierrors.ErrorsErrorResponse | 400                           | application/json              |
| apierrors.ErrorsErrorResponse | 500                           | application/json              |
| apierrors.APIError            | 4XX, 5XX                      | \*/\*                         |

## GetUsageStatistics

Use when building usage reports or dashboards across events. Supports filters and grouping; defaults to last 7 days if no range provided.

### Example Usage

<!-- UsageSnippet language="go" operationID="getUsageStatistics" method="post" path="/events/usage" -->
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

    res, err := s.Events.GetUsageStatistics(ctx, components.DtoGetUsageRequest{
        AggregationType: components.TypesAggregationTypeCountUnique,
        BillingAnchor: undefined.Pointer("2024-03-05T14:30:45.123456789Z"),
        CustomerID: undefined.Pointer("customer456"),
        EndTime: undefined.Pointer("2024-03-20T00:00:00Z"),
        EventName: "api_request",
        ExternalCustomerID: undefined.Pointer("customer456"),
        PropertyName: undefined.Pointer("request_size"),
        StartTime: undefined.Pointer("2024-03-13T00:00:00Z"),
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.DtoGetUsageResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                      | Type                                                                           | Required                                                                       | Description                                                                    |
| ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------ |
| `ctx`                                                                          | [context.Context](https://pkg.go.dev/context#Context)                          | :heavy_check_mark:                                                             | The context to use for the request.                                            |
| `request`                                                                      | [components.DtoGetUsageRequest](../../models/components/dtogetusagerequest.md) | :heavy_check_mark:                                                             | The request object to use for the request.                                     |
| `opts`                                                                         | [][operations.Option](../../models/operations/option.md)                       | :heavy_minus_sign:                                                             | The options for this request.                                                  |

### Response

**[*operations.GetUsageStatisticsResponse](../../models/operations/getusagestatisticsresponse.md), error**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| apierrors.ErrorsErrorResponse | 400                           | application/json              |
| apierrors.ErrorsErrorResponse | 500                           | application/json              |
| apierrors.APIError            | 4XX, 5XX                      | \*/\*                         |

## GetUsageByMeter

Use when showing usage for a specific meter (e.g. dashboard or overage check). Supports time range, filters, and grouping by customer or subscription.

### Example Usage

<!-- UsageSnippet language="go" operationID="getUsageByMeter" method="post" path="/events/usage/meter" -->
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

    res, err := s.Events.GetUsageByMeter(ctx, components.DtoGetUsageByMeterRequest{
        BillingAnchor: undefined.Pointer("2024-03-05T14:30:45Z"),
        CustomerID: undefined.Pointer("customer456"),
        EndTime: undefined.Pointer("2024-12-09T00:00:00Z"),
        ExternalCustomerID: undefined.Pointer("user_5"),
        MeterID: "123",
        StartTime: undefined.Pointer("2024-11-09T00:00:00Z"),
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.DtoGetUsageResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                    | Type                                                                                         | Required                                                                                     | Description                                                                                  |
| -------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------- |
| `ctx`                                                                                        | [context.Context](https://pkg.go.dev/context#Context)                                        | :heavy_check_mark:                                                                           | The context to use for the request.                                                          |
| `request`                                                                                    | [components.DtoGetUsageByMeterRequest](../../models/components/dtogetusagebymeterrequest.md) | :heavy_check_mark:                                                                           | The request object to use for the request.                                                   |
| `opts`                                                                                       | [][operations.Option](../../models/operations/option.md)                                     | :heavy_minus_sign:                                                                           | The options for this request.                                                                |

### Response

**[*operations.GetUsageByMeterResponse](../../models/operations/getusagebymeterresponse.md), error**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| apierrors.ErrorsErrorResponse | 400, 404                      | application/json              |
| apierrors.ErrorsErrorResponse | 500                           | application/json              |
| apierrors.APIError            | 4XX, 5XX                      | \*/\*                         |

## GetEvent

Use when debugging a specific event (e.g. why it failed or how it was aggregated). Includes processing status and debug info.

### Example Usage

<!-- UsageSnippet language="go" operationID="getEvent" method="get" path="/events/{id}" -->
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

    res, err := s.Events.GetEvent(ctx, "<id>")
    if err != nil {
        log.Fatal(err)
    }
    if res.DtoGetEventByIDResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                | Type                                                     | Required                                                 | Description                                              |
| -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- |
| `ctx`                                                    | [context.Context](https://pkg.go.dev/context#Context)    | :heavy_check_mark:                                       | The context to use for the request.                      |
| `id`                                                     | *string*                                                 | :heavy_check_mark:                                       | Event ID                                                 |
| `opts`                                                   | [][operations.Option](../../models/operations/option.md) | :heavy_minus_sign:                                       | The options for this request.                            |

### Response

**[*operations.GetEventResponse](../../models/operations/geteventresponse.md), error**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| apierrors.ErrorsErrorResponse | 404                           | application/json              |
| apierrors.ErrorsErrorResponse | 500                           | application/json              |
| apierrors.APIError            | 4XX, 5XX                      | \*/\*                         |