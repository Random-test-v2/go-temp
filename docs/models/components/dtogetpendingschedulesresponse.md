# DtoGetPendingSchedulesResponse

List of pending schedules for a subscription


## Fields

| Field                                                                                                      | Type                                                                                                       | Required                                                                                                   | Description                                                                                                |
| ---------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- |
| `Count`                                                                                                    | **int64*                                                                                                   | :heavy_minus_sign:                                                                                         | count is the number of pending schedules                                                                   |
| `Schedules`                                                                                                | [][components.DtoSubscriptionScheduleResponse](../../models/components/dtosubscriptionscheduleresponse.md) | :heavy_minus_sign:                                                                                         | schedules is the list of pending schedules                                                                 |