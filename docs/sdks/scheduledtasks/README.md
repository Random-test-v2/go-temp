# ScheduledTasks

## Overview

### Available Operations

* [ListScheduledTasks](#listscheduledtasks) - List scheduled tasks
* [CreateScheduledTask](#createscheduledtask) - Create scheduled task
* [ScheduleUpdateBillingPeriod](#scheduleupdatebillingperiod) - Schedule update billing period
* [GetScheduledTask](#getscheduledtask) - Get scheduled task
* [UpdateScheduledTask](#updatescheduledtask) - Update a scheduled task
* [DeleteScheduledTask](#deletescheduledtask) - Delete a scheduled task
* [TriggerScheduledTaskRun](#triggerscheduledtaskrun) - Trigger force run

## ListScheduledTasks

Use when listing or managing scheduled tasks in an admin UI. Returns a list; supports filtering by status, type, and pagination.

### Example Usage

<!-- UsageSnippet language="go" operationID="listScheduledTasks" method="get" path="/tasks/scheduled" -->
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

    res, err := s.ScheduledTasks.ListScheduledTasks(ctx, operations.ListScheduledTasksRequest{})
    if err != nil {
        log.Fatal(err)
    }
    if res.DtoListScheduledTasksResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                    | Type                                                                                         | Required                                                                                     | Description                                                                                  |
| -------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------- |
| `ctx`                                                                                        | [context.Context](https://pkg.go.dev/context#Context)                                        | :heavy_check_mark:                                                                           | The context to use for the request.                                                          |
| `request`                                                                                    | [operations.ListScheduledTasksRequest](../../models/operations/listscheduledtasksrequest.md) | :heavy_check_mark:                                                                           | The request object to use for the request.                                                   |
| `opts`                                                                                       | [][operations.Option](../../models/operations/option.md)                                     | :heavy_minus_sign:                                                                           | The options for this request.                                                                |

### Response

**[*operations.ListScheduledTasksResponse](../../models/operations/listscheduledtasksresponse.md), error**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| apierrors.ErrorsErrorResponse | 400                           | application/json              |
| apierrors.ErrorsErrorResponse | 500                           | application/json              |
| apierrors.APIError            | 4XX, 5XX                      | \*/\*                         |

## CreateScheduledTask

Use when setting up recurring data exports or other scheduled jobs. Ideal for report generation or syncing data on a schedule.

### Example Usage

<!-- UsageSnippet language="go" operationID="createScheduledTask" method="post" path="/tasks/scheduled" -->
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

    res, err := s.ScheduledTasks.CreateScheduledTask(ctx, components.DtoCreateScheduledTaskRequest{
        ConnectionID: "<id>",
        EntityType: components.TypesScheduledTaskEntityTypeCreditTopups,
        Interval: components.TypesScheduledTaskIntervalHourly,
        JobConfig: components.TypesS3JobConfig{},
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.DtoScheduledTaskResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                            | Type                                                                                                 | Required                                                                                             | Description                                                                                          |
| ---------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------- |
| `ctx`                                                                                                | [context.Context](https://pkg.go.dev/context#Context)                                                | :heavy_check_mark:                                                                                   | The context to use for the request.                                                                  |
| `request`                                                                                            | [components.DtoCreateScheduledTaskRequest](../../models/components/dtocreatescheduledtaskrequest.md) | :heavy_check_mark:                                                                                   | The request object to use for the request.                                                           |
| `opts`                                                                                               | [][operations.Option](../../models/operations/option.md)                                             | :heavy_minus_sign:                                                                                   | The options for this request.                                                                        |

### Response

**[*operations.CreateScheduledTaskResponse](../../models/operations/createscheduledtaskresponse.md), error**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| apierrors.ErrorsErrorResponse | 400                           | application/json              |
| apierrors.ErrorsErrorResponse | 500                           | application/json              |
| apierrors.APIError            | 4XX, 5XX                      | \*/\*                         |

## ScheduleUpdateBillingPeriod

Use when you need to trigger a billing-period update workflow (e.g. to recalculate or sync billing windows).

### Example Usage

<!-- UsageSnippet language="go" operationID="scheduleUpdateBillingPeriod" method="post" path="/tasks/scheduled/schedule-update-billing-period" -->
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

    res, err := s.ScheduledTasks.ScheduleUpdateBillingPeriod(ctx, operations.ScheduleUpdateBillingPeriodRequest{})
    if err != nil {
        log.Fatal(err)
    }
    if res.Object != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                                      | Type                                                                                                           | Required                                                                                                       | Description                                                                                                    |
| -------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------- |
| `ctx`                                                                                                          | [context.Context](https://pkg.go.dev/context#Context)                                                          | :heavy_check_mark:                                                                                             | The context to use for the request.                                                                            |
| `request`                                                                                                      | [operations.ScheduleUpdateBillingPeriodRequest](../../models/operations/scheduleupdatebillingperiodrequest.md) | :heavy_check_mark:                                                                                             | The request object to use for the request.                                                                     |
| `opts`                                                                                                         | [][operations.Option](../../models/operations/option.md)                                                       | :heavy_minus_sign:                                                                                             | The options for this request.                                                                                  |

### Response

**[*operations.ScheduleUpdateBillingPeriodResponse](../../models/operations/scheduleupdatebillingperiodresponse.md), error**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| apierrors.ErrorsErrorResponse | 400                           | application/json              |
| apierrors.ErrorsErrorResponse | 500                           | application/json              |
| apierrors.APIError            | 4XX, 5XX                      | \*/\*                         |

## GetScheduledTask

Use when you need to load a single scheduled task (e.g. to show details in a UI or check its configuration).

### Example Usage

<!-- UsageSnippet language="go" operationID="getScheduledTask" method="get" path="/tasks/scheduled/{id}" -->
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

    res, err := s.ScheduledTasks.GetScheduledTask(ctx, "<id>")
    if err != nil {
        log.Fatal(err)
    }
    if res.DtoScheduledTaskResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                | Type                                                     | Required                                                 | Description                                              |
| -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- |
| `ctx`                                                    | [context.Context](https://pkg.go.dev/context#Context)    | :heavy_check_mark:                                       | The context to use for the request.                      |
| `id`                                                     | *string*                                                 | :heavy_check_mark:                                       | Scheduled Task ID                                        |
| `opts`                                                   | [][operations.Option](../../models/operations/option.md) | :heavy_minus_sign:                                       | The options for this request.                            |

### Response

**[*operations.GetScheduledTaskResponse](../../models/operations/getscheduledtaskresponse.md), error**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| apierrors.ErrorsErrorResponse | 400, 404                      | application/json              |
| apierrors.ErrorsErrorResponse | 500                           | application/json              |
| apierrors.APIError            | 4XX, 5XX                      | \*/\*                         |

## UpdateScheduledTask

Use when pausing or resuming a scheduled task. Only the enabled field can be changed.

### Example Usage

<!-- UsageSnippet language="go" operationID="updateScheduledTask" method="put" path="/tasks/scheduled/{id}" -->
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

    res, err := s.ScheduledTasks.UpdateScheduledTask(ctx, "<id>", components.DtoUpdateScheduledTaskRequest{
        Enabled: false,
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.DtoScheduledTaskResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                            | Type                                                                                                 | Required                                                                                             | Description                                                                                          |
| ---------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------- |
| `ctx`                                                                                                | [context.Context](https://pkg.go.dev/context#Context)                                                | :heavy_check_mark:                                                                                   | The context to use for the request.                                                                  |
| `id`                                                                                                 | *string*                                                                                             | :heavy_check_mark:                                                                                   | Scheduled Task ID                                                                                    |
| `body`                                                                                               | [components.DtoUpdateScheduledTaskRequest](../../models/components/dtoupdatescheduledtaskrequest.md) | :heavy_check_mark:                                                                                   | Update request (enabled: true/false to pause/resume)                                                 |
| `opts`                                                                                               | [][operations.Option](../../models/operations/option.md)                                             | :heavy_minus_sign:                                                                                   | The options for this request.                                                                        |

### Response

**[*operations.UpdateScheduledTaskResponse](../../models/operations/updatescheduledtaskresponse.md), error**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| apierrors.ErrorsErrorResponse | 400, 404                      | application/json              |
| apierrors.ErrorsErrorResponse | 500                           | application/json              |
| apierrors.APIError            | 4XX, 5XX                      | \*/\*                         |

## DeleteScheduledTask

Use when removing a scheduled task from the active roster. Archives the task and removes it from the scheduler (soft delete).

### Example Usage

<!-- UsageSnippet language="go" operationID="deleteScheduledTask" method="delete" path="/tasks/scheduled/{id}" -->
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

    res, err := s.ScheduledTasks.DeleteScheduledTask(ctx, "<id>")
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
| `id`                                                     | *string*                                                 | :heavy_check_mark:                                       | Scheduled Task ID                                        |
| `opts`                                                   | [][operations.Option](../../models/operations/option.md) | :heavy_minus_sign:                                       | The options for this request.                            |

### Response

**[*operations.DeleteScheduledTaskResponse](../../models/operations/deletescheduledtaskresponse.md), error**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| apierrors.ErrorsErrorResponse | 400, 404                      | application/json              |
| apierrors.ErrorsErrorResponse | 500                           | application/json              |
| apierrors.APIError            | 4XX, 5XX                      | \*/\*                         |

## TriggerScheduledTaskRun

Use when you need to run a scheduled export immediately (e.g. on-demand report or catch-up). Supports optional custom time range.

### Example Usage

<!-- UsageSnippet language="go" operationID="triggerScheduledTaskRun" method="post" path="/tasks/scheduled/{id}/run" -->
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

    res, err := s.ScheduledTasks.TriggerScheduledTaskRun(ctx, "<id>", nil)
    if err != nil {
        log.Fatal(err)
    }
    if res.DtoTriggerForceRunResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                     | Type                                                                                          | Required                                                                                      | Description                                                                                   |
| --------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- |
| `ctx`                                                                                         | [context.Context](https://pkg.go.dev/context#Context)                                         | :heavy_check_mark:                                                                            | The context to use for the request.                                                           |
| `id`                                                                                          | *string*                                                                                      | :heavy_check_mark:                                                                            | Scheduled Task ID                                                                             |
| `body`                                                                                        | [*components.DtoTriggerForceRunRequest](../../models/components/dtotriggerforcerunrequest.md) | :heavy_minus_sign:                                                                            | Optional start and end time for custom range                                                  |
| `opts`                                                                                        | [][operations.Option](../../models/operations/option.md)                                      | :heavy_minus_sign:                                                                            | The options for this request.                                                                 |

### Response

**[*operations.TriggerScheduledTaskRunResponse](../../models/operations/triggerscheduledtaskrunresponse.md), error**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| apierrors.ErrorsErrorResponse | 400, 404                      | application/json              |
| apierrors.ErrorsErrorResponse | 500                           | application/json              |
| apierrors.APIError            | 4XX, 5XX                      | \*/\*                         |