# Users

## Overview

### Available Operations

* [CreateUser](#createuser) - Create service account
* [GetUserInfo](#getuserinfo) - Get current user
* [QueryUser](#queryuser) - Query users

## CreateUser

Use when provisioning API access for automation, CI/CD pipelines, or headless integrations that need scoped API keys.

### Example Usage

<!-- UsageSnippet language="go" operationID="createUser" method="post" path="/users" -->
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

    res, err := s.Users.CreateUser(ctx, components.DtoCreateUserRequest{
        Roles: []string{},
        Type: components.TypesUserTypeUser,
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.DtoUserResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                          | Type                                                                               | Required                                                                           | Description                                                                        |
| ---------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- |
| `ctx`                                                                              | [context.Context](https://pkg.go.dev/context#Context)                              | :heavy_check_mark:                                                                 | The context to use for the request.                                                |
| `request`                                                                          | [components.DtoCreateUserRequest](../../models/components/dtocreateuserrequest.md) | :heavy_check_mark:                                                                 | The request object to use for the request.                                         |
| `opts`                                                                             | [][operations.Option](../../models/operations/option.md)                           | :heavy_minus_sign:                                                                 | The options for this request.                                                      |

### Response

**[*operations.CreateUserResponse](../../models/operations/createuserresponse.md), error**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| apierrors.ErrorsErrorResponse | 400                           | application/json              |
| apierrors.ErrorsErrorResponse | 500                           | application/json              |
| apierrors.APIError            | 4XX, 5XX                      | \*/\*                         |

## GetUserInfo

Use to show the logged-in user's profile in the UI or to check permissions and roles for the current session.

### Example Usage

<!-- UsageSnippet language="go" operationID="getUserInfo" method="get" path="/users/me" -->
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

    res, err := s.Users.GetUserInfo(ctx)
    if err != nil {
        log.Fatal(err)
    }
    if res.DtoUserResponse != nil {
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

**[*operations.GetUserInfoResponse](../../models/operations/getuserinforesponse.md), error**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| apierrors.ErrorsErrorResponse | 401                           | application/json              |
| apierrors.ErrorsErrorResponse | 500                           | application/json              |
| apierrors.APIError            | 4XX, 5XX                      | \*/\*                         |

## QueryUser

Use when listing or searching service accounts in an admin UI, or when auditing who has API access and which roles they have.

### Example Usage

<!-- UsageSnippet language="go" operationID="queryUser" method="post" path="/users/search" -->
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

    res, err := s.Users.QueryUser(ctx, components.TypesUserFilter{})
    if err != nil {
        log.Fatal(err)
    }
    if res.DtoListUsersResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                | Type                                                                     | Required                                                                 | Description                                                              |
| ------------------------------------------------------------------------ | ------------------------------------------------------------------------ | ------------------------------------------------------------------------ | ------------------------------------------------------------------------ |
| `ctx`                                                                    | [context.Context](https://pkg.go.dev/context#Context)                    | :heavy_check_mark:                                                       | The context to use for the request.                                      |
| `request`                                                                | [components.TypesUserFilter](../../models/components/typesuserfilter.md) | :heavy_check_mark:                                                       | The request object to use for the request.                               |
| `opts`                                                                   | [][operations.Option](../../models/operations/option.md)                 | :heavy_minus_sign:                                                       | The options for this request.                                            |

### Response

**[*operations.QueryUserResponse](../../models/operations/queryuserresponse.md), error**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| apierrors.ErrorsErrorResponse | 400                           | application/json              |
| apierrors.ErrorsErrorResponse | 500                           | application/json              |
| apierrors.APIError            | 4XX, 5XX                      | \*/\*                         |