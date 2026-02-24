# flexprice

Developer-friendly & type-safe Go SDK specifically catered to leverage *flexprice* API.

[![Built by Speakeasy](https://img.shields.io/badge/Built_by-SPEAKEASY-374151?style=for-the-badge&labelColor=f3f4f6)](https://www.speakeasy.com/?utm_source=flexprice&utm_campaign=go)
[![License: MIT](https://img.shields.io/badge/LICENSE_//_MIT-3b5bdb?style=for-the-badge&labelColor=eff6ff)](https://opensource.org/licenses/MIT)


<br /><br />
> [!IMPORTANT]
> This SDK is not yet ready for production use. To complete setup please follow the steps outlined in your [workspace](https://app.speakeasy.com/org/flexprice/prod). Delete this section before > publishing to a package manager.

<!-- Start Summary [summary] -->
## Summary

Flexprice API: Flexprice API provides billing, metering, and subscription management for SaaS and usage-based products. Use it to manage customers, plans, invoices, payments, usage events, and entitlements. Authenticate with an API key in the x-api-key header.
<!-- End Summary [summary] -->

<!-- Start Table of Contents [toc] -->
## Table of Contents
<!-- $toc-max-depth=2 -->
* [flexprice](#flexprice)
  * [SDK Installation](#sdk-installation)
  * [SDK Example Usage](#sdk-example-usage)
  * [Authentication](#authentication)
  * [Available Resources and Operations](#available-resources-and-operations)
  * [Retries](#retries)
  * [Error Handling](#error-handling)
  * [Custom HTTP Client](#custom-http-client)
* [Development](#development)
  * [Maturity](#maturity)
  * [Contributions](#contributions)

<!-- End Table of Contents [toc] -->

<!-- Start SDK Installation [installation] -->
## SDK Installation

To add the SDK as a dependency to your project:
```bash
go get github.com/flexprice/flexprice-go
```
<!-- End SDK Installation [installation] -->

<!-- Start SDK Example Usage [usage] -->
## SDK Example Usage

### Example

```go
package main

import (
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
		Name:      "<value>",
		Type:      components.TypesAddonTypeMultipleInstance,
	})
	if err != nil {
		log.Fatal(err)
	}
	if res.DtoCreateAddonResponse != nil {
		// handle response
	}
}

```
<!-- End SDK Example Usage [usage] -->

<!-- Start Authentication [security] -->
## Authentication

### Per-Client Security Schemes

This SDK supports the following security scheme globally:

| Name         | Type   | Scheme  |
| ------------ | ------ | ------- |
| `APIKeyAuth` | apiKey | API key |

You can configure it using the `WithSecurity` option when initializing the SDK client instance. For example:
```go
package main

import (
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
		Name:      "<value>",
		Type:      components.TypesAddonTypeMultipleInstance,
	})
	if err != nil {
		log.Fatal(err)
	}
	if res.DtoCreateAddonResponse != nil {
		// handle response
	}
}

```
<!-- End Authentication [security] -->

<!-- Start Available Resources and Operations [operations] -->
## Available Resources and Operations

<details open>
<summary>Available methods</summary>

### [Addons](docs/sdks/addons/README.md)

* [CreateAddon](docs/sdks/addons/README.md#createaddon) - Create addon
* [GetAddonByLookupKey](docs/sdks/addons/README.md#getaddonbylookupkey) - Get addon by lookup key
* [QueryAddon](docs/sdks/addons/README.md#queryaddon) - Query addons
* [GetAddon](docs/sdks/addons/README.md#getaddon) - Get addon
* [UpdateAddon](docs/sdks/addons/README.md#updateaddon) - Update addon
* [DeleteAddon](docs/sdks/addons/README.md#deleteaddon) - Delete addon

### [Alerts](docs/sdks/alerts/README.md)

* [QueryAlertLog](docs/sdks/alerts/README.md#queryalertlog) - Query alert logs

### [Costs](docs/sdks/costs/README.md)

* [CreateCostsheet](docs/sdks/costs/README.md#createcostsheet) - Create costsheet
* [GetActiveCostsheet](docs/sdks/costs/README.md#getactivecostsheet) - Get active costsheet
* [GetDetailedCostAnalytics](docs/sdks/costs/README.md#getdetailedcostanalytics) - Get combined revenue and cost analytics
* [GetDetailedCostAnalyticsV2](docs/sdks/costs/README.md#getdetailedcostanalyticsv2) - Get combined revenue and cost analytics (V2)
* [QueryCostsheet](docs/sdks/costs/README.md#querycostsheet) - Query costsheets
* [GetCostsheet](docs/sdks/costs/README.md#getcostsheet) - Get costsheet
* [UpdateCostsheet](docs/sdks/costs/README.md#updatecostsheet) - Update costsheet
* [DeleteCostsheet](docs/sdks/costs/README.md#deletecostsheet) - Delete costsheet

### [Coupons](docs/sdks/coupons/README.md)

* [CreateCoupon](docs/sdks/coupons/README.md#createcoupon) - Create coupon
* [QueryCoupon](docs/sdks/coupons/README.md#querycoupon) - Query coupons
* [GetCoupon](docs/sdks/coupons/README.md#getcoupon) - Get coupon
* [UpdateCoupon](docs/sdks/coupons/README.md#updatecoupon) - Update coupon
* [DeleteCoupon](docs/sdks/coupons/README.md#deletecoupon) - Delete coupon

### [CreditGrants](docs/sdks/creditgrants/README.md)

* [CreateCreditGrant](docs/sdks/creditgrants/README.md#createcreditgrant) - Create credit grant
* [GetCreditGrant](docs/sdks/creditgrants/README.md#getcreditgrant) - Get credit grant
* [UpdateCreditGrant](docs/sdks/creditgrants/README.md#updatecreditgrant) - Update credit grant
* [DeleteCreditGrant](docs/sdks/creditgrants/README.md#deletecreditgrant) - Delete credit grant
* [GetPlanCreditGrants](docs/sdks/creditgrants/README.md#getplancreditgrants) - Get plan credit grants

### [CreditNotes](docs/sdks/creditnotes/README.md)

* [CreateCreditNote](docs/sdks/creditnotes/README.md#createcreditnote) - Create credit note
* [GetCreditNote](docs/sdks/creditnotes/README.md#getcreditnote) - Get credit note
* [ProcessCreditNote](docs/sdks/creditnotes/README.md#processcreditnote) - Finalize credit note
* [VoidCreditNote](docs/sdks/creditnotes/README.md#voidcreditnote) - Void credit note

### [Customers](docs/sdks/customers/README.md)

* [UpdateCustomer](docs/sdks/customers/README.md#updatecustomer) - Update customer
* [CreateCustomer](docs/sdks/customers/README.md#createcustomer) - Create customer
* [GetCustomerByExternalID](docs/sdks/customers/README.md#getcustomerbyexternalid) - Get customer by external ID
* [QueryCustomer](docs/sdks/customers/README.md#querycustomer) - Query customers
* [GetCustomerUsageSummary](docs/sdks/customers/README.md#getcustomerusagesummary) - Get customer usage summary
* [GetCustomer](docs/sdks/customers/README.md#getcustomer) - Get customer
* [DeleteCustomer](docs/sdks/customers/README.md#deletecustomer) - Delete customer
* [GetCustomerEntitlements](docs/sdks/customers/README.md#getcustomerentitlements) - Get customer entitlements
* [GetCustomerUpcomingGrants](docs/sdks/customers/README.md#getcustomerupcominggrants) - Get upcoming credit grant applications

### [Entitlements](docs/sdks/entitlements/README.md)

* [GetAddonEntitlements](docs/sdks/entitlements/README.md#getaddonentitlements) - Get addon entitlements
* [CreateEntitlement](docs/sdks/entitlements/README.md#createentitlement) - Create entitlement
* [CreateEntitlementsBulk](docs/sdks/entitlements/README.md#createentitlementsbulk) - Create entitlements in bulk
* [QueryEntitlement](docs/sdks/entitlements/README.md#queryentitlement) - Query entitlements
* [GetEntitlement](docs/sdks/entitlements/README.md#getentitlement) - Get entitlement
* [UpdateEntitlement](docs/sdks/entitlements/README.md#updateentitlement) - Update entitlement
* [DeleteEntitlement](docs/sdks/entitlements/README.md#deleteentitlement) - Delete entitlement
* [GetPlanEntitlements](docs/sdks/entitlements/README.md#getplanentitlements) - Get plan entitlements

### [EntityIntegrationMappings](docs/sdks/entityintegrationmappings/README.md)

* [CreateEntityIntegrationMapping](docs/sdks/entityintegrationmappings/README.md#createentityintegrationmapping) - Create entity integration mapping
* [DeleteEntityIntegrationMapping](docs/sdks/entityintegrationmappings/README.md#deleteentityintegrationmapping) - Delete entity integration mapping

### [Environments](docs/sdks/environments/README.md)

* [CreateEnvironment](docs/sdks/environments/README.md#createenvironment) - Create environment
* [UpdateEnvironment](docs/sdks/environments/README.md#updateenvironment) - Update environment

### [Events](docs/sdks/events/README.md)

* [IngestEvent](docs/sdks/events/README.md#ingestevent) - Ingest event
* [GetUsageAnalytics](docs/sdks/events/README.md#getusageanalytics) - Get usage analytics
* [IngestEventsBulk](docs/sdks/events/README.md#ingesteventsbulk) - Bulk ingest events
* [GetHuggingfaceInferenceData](docs/sdks/events/README.md#gethuggingfaceinferencedata) - Get Hugging Face inference data
* [ListRawEvents](docs/sdks/events/README.md#listrawevents) - List raw events
* [GetUsageStatistics](docs/sdks/events/README.md#getusagestatistics) - Get usage statistics
* [GetUsageByMeter](docs/sdks/events/README.md#getusagebymeter) - Get usage by meter
* [GetEvent](docs/sdks/events/README.md#getevent) - Get event

### [Features](docs/sdks/features/README.md)

* [CreateFeature](docs/sdks/features/README.md#createfeature) - Create feature
* [QueryFeature](docs/sdks/features/README.md#queryfeature) - Query features
* [UpdateFeature](docs/sdks/features/README.md#updatefeature) - Update feature
* [DeleteFeature](docs/sdks/features/README.md#deletefeature) - Delete feature

### [Groups](docs/sdks/groups/README.md)

* [CreateGroup](docs/sdks/groups/README.md#creategroup) - Create group
* [QueryGroup](docs/sdks/groups/README.md#querygroup) - Query groups
* [GetGroup](docs/sdks/groups/README.md#getgroup) - Get group
* [DeleteGroup](docs/sdks/groups/README.md#deletegroup) - Delete group

### [Integrations](docs/sdks/integrations/README.md)

* [GetIntegration](docs/sdks/integrations/README.md#getintegration) - Get integration details
* [CreateOrUpdateIntegration](docs/sdks/integrations/README.md#createorupdateintegration) - Create or update an integration
* [ListLinkedIntegrations](docs/sdks/integrations/README.md#listlinkedintegrations) - List linked integrations
* [DeleteIntegration](docs/sdks/integrations/README.md#deleteintegration) - Delete an integration

### [Invoices](docs/sdks/invoices/README.md)

* [GetCustomerInvoiceSummary](docs/sdks/invoices/README.md#getcustomerinvoicesummary) - Get customer invoice summary
* [CreateInvoice](docs/sdks/invoices/README.md#createinvoice) - Create one-off invoice
* [GetInvoicePreview](docs/sdks/invoices/README.md#getinvoicepreview) - Get invoice preview
* [QueryInvoice](docs/sdks/invoices/README.md#queryinvoice) - Query invoices
* [GetInvoice](docs/sdks/invoices/README.md#getinvoice) - Get invoice
* [UpdateInvoice](docs/sdks/invoices/README.md#updateinvoice) - Update invoice
* [TriggerInvoiceCommsWebhook](docs/sdks/invoices/README.md#triggerinvoicecommswebhook) - Trigger invoice communication webhook
* [FinalizeInvoice](docs/sdks/invoices/README.md#finalizeinvoice) - Finalize invoice
* [UpdateInvoicePaymentStatus](docs/sdks/invoices/README.md#updateinvoicepaymentstatus) - Update invoice payment status
* [AttemptInvoicePayment](docs/sdks/invoices/README.md#attemptinvoicepayment) - Attempt invoice payment
* [GetInvoicePdf](docs/sdks/invoices/README.md#getinvoicepdf) - Get invoice PDF
* [RecalculateInvoice](docs/sdks/invoices/README.md#recalculateinvoice) - Recalculate invoice
* [VoidInvoice](docs/sdks/invoices/README.md#voidinvoice) - Void invoice

### [Payments](docs/sdks/payments/README.md)

* [ListPayments](docs/sdks/payments/README.md#listpayments) - List payments
* [CreatePayment](docs/sdks/payments/README.md#createpayment) - Create payment
* [GetPayment](docs/sdks/payments/README.md#getpayment) - Get payment
* [UpdatePayment](docs/sdks/payments/README.md#updatepayment) - Update payment
* [DeletePayment](docs/sdks/payments/README.md#deletepayment) - Delete payment
* [ProcessPayment](docs/sdks/payments/README.md#processpayment) - Process payment

### [Plans](docs/sdks/plans/README.md)

* [CreatePlan](docs/sdks/plans/README.md#createplan) - Create plan
* [QueryPlan](docs/sdks/plans/README.md#queryplan) - Query plans
* [GetPlan](docs/sdks/plans/README.md#getplan) - Get plan
* [UpdatePlan](docs/sdks/plans/README.md#updateplan) - Update plan
* [DeletePlan](docs/sdks/plans/README.md#deleteplan) - Delete plan
* [SyncPlanPrices](docs/sdks/plans/README.md#syncplanprices) - Synchronize plan prices

### [PriceUnits](docs/sdks/priceunits/README.md)

* [ListPriceUnits](docs/sdks/priceunits/README.md#listpriceunits) - List price units
* [CreatePriceUnit](docs/sdks/priceunits/README.md#createpriceunit) - Create price unit
* [GetPriceUnitByCode](docs/sdks/priceunits/README.md#getpriceunitbycode) - Get price unit by code
* [QueryPriceUnit](docs/sdks/priceunits/README.md#querypriceunit) - Query price units
* [GetPriceUnit](docs/sdks/priceunits/README.md#getpriceunit) - Get price unit
* [UpdatePriceUnit](docs/sdks/priceunits/README.md#updatepriceunit) - Update price unit
* [DeletePriceUnit](docs/sdks/priceunits/README.md#deletepriceunit) - Delete price unit

### [Prices](docs/sdks/prices/README.md)

* [CreatePrice](docs/sdks/prices/README.md#createprice) - Create price
* [CreatePricesBulk](docs/sdks/prices/README.md#createpricesbulk) - Create prices in bulk
* [GetPriceByLookupKey](docs/sdks/prices/README.md#getpricebylookupkey) - Get price by lookup key
* [QueryPrice](docs/sdks/prices/README.md#queryprice) - Query prices
* [GetPrice](docs/sdks/prices/README.md#getprice) - Get price
* [UpdatePrice](docs/sdks/prices/README.md#updateprice) - Update price
* [DeletePrice](docs/sdks/prices/README.md#deleteprice) - Delete price

### [Rbac](docs/sdks/rbac/README.md)

* [ListRbacRoles](docs/sdks/rbac/README.md#listrbacroles) - List all RBAC roles
* [GetRbacRole](docs/sdks/rbac/README.md#getrbacrole) - Get a specific RBAC role

### [ScheduledTasks](docs/sdks/scheduledtasks/README.md)

* [ListScheduledTasks](docs/sdks/scheduledtasks/README.md#listscheduledtasks) - List scheduled tasks
* [CreateScheduledTask](docs/sdks/scheduledtasks/README.md#createscheduledtask) - Create scheduled task
* [ScheduleUpdateBillingPeriod](docs/sdks/scheduledtasks/README.md#scheduleupdatebillingperiod) - Schedule update billing period
* [GetScheduledTask](docs/sdks/scheduledtasks/README.md#getscheduledtask) - Get scheduled task
* [UpdateScheduledTask](docs/sdks/scheduledtasks/README.md#updatescheduledtask) - Update a scheduled task
* [DeleteScheduledTask](docs/sdks/scheduledtasks/README.md#deletescheduledtask) - Delete a scheduled task
* [TriggerScheduledTaskRun](docs/sdks/scheduledtasks/README.md#triggerscheduledtaskrun) - Trigger force run

### [Secrets](docs/sdks/secrets/README.md)

* [ListAPIKeys](docs/sdks/secrets/README.md#listapikeys) - List API keys
* [CreateAPIKey](docs/sdks/secrets/README.md#createapikey) - Create a new API key
* [DeleteAPIKey](docs/sdks/secrets/README.md#deleteapikey) - Delete an API key

### [Subscriptions](docs/sdks/subscriptions/README.md)

* [CreateSubscription](docs/sdks/subscriptions/README.md#createsubscription) - Create subscription
* [AddSubscriptionAddon](docs/sdks/subscriptions/README.md#addsubscriptionaddon) - Add addon to subscription
* [RemoveSubscriptionAddon](docs/sdks/subscriptions/README.md#removesubscriptionaddon) - Remove addon from subscription
* [UpdateSubscriptionLineItem](docs/sdks/subscriptions/README.md#updatesubscriptionlineitem) - Update subscription line item
* [DeleteSubscriptionLineItem](docs/sdks/subscriptions/README.md#deletesubscriptionlineitem) - Delete subscription line item
* [QuerySubscription](docs/sdks/subscriptions/README.md#querysubscription) - Query subscriptions
* [GetSubscriptionUsage](docs/sdks/subscriptions/README.md#getsubscriptionusage) - Get usage by subscription
* [GetSubscription](docs/sdks/subscriptions/README.md#getsubscription) - Get subscription
* [UpdateSubscription](docs/sdks/subscriptions/README.md#updatesubscription) - Update subscription
* [ActivateSubscription](docs/sdks/subscriptions/README.md#activatesubscription) - Activate draft subscription
* [GetSubscriptionAddonAssociations](docs/sdks/subscriptions/README.md#getsubscriptionaddonassociations) - Get active addon associations
* [CancelSubscription](docs/sdks/subscriptions/README.md#cancelsubscription) - Cancel subscription
* [ExecuteSubscriptionChange](docs/sdks/subscriptions/README.md#executesubscriptionchange) - Execute subscription plan change
* [PreviewSubscriptionChange](docs/sdks/subscriptions/README.md#previewsubscriptionchange) - Preview subscription plan change
* [GetSubscriptionEntitlements](docs/sdks/subscriptions/README.md#getsubscriptionentitlements) - Get subscription entitlements
* [GetSubscriptionUpcomingGrants](docs/sdks/subscriptions/README.md#getsubscriptionupcominggrants) - Get upcoming credit grant applications
* [CreateSubscriptionLineItem](docs/sdks/subscriptions/README.md#createsubscriptionlineitem) - Create subscription line item
* [PauseSubscription](docs/sdks/subscriptions/README.md#pausesubscription) - Pause a subscription
* [ListSubscriptionPauses](docs/sdks/subscriptions/README.md#listsubscriptionpauses) - List all pauses for a subscription
* [ResumeSubscription](docs/sdks/subscriptions/README.md#resumesubscription) - Resume a paused subscription
* [GetSubscriptionV2](docs/sdks/subscriptions/README.md#getsubscriptionv2) - Get subscription (V2)
* [ListAllSubscriptionSchedules](docs/sdks/subscriptions/README.md#listallsubscriptionschedules) - List all subscription schedules
* [GetSubscriptionSchedule](docs/sdks/subscriptions/README.md#getsubscriptionschedule) - Get subscription schedule
* [CancelSubscriptionSchedule](docs/sdks/subscriptions/README.md#cancelsubscriptionschedule) - Cancel subscription schedule
* [ListSubscriptionSchedules](docs/sdks/subscriptions/README.md#listsubscriptionschedules) - List subscription schedules

### [Tasks](docs/sdks/tasks/README.md)

* [ListTasks](docs/sdks/tasks/README.md#listtasks) - List tasks
* [CreateTask](docs/sdks/tasks/README.md#createtask) - Create a new task
* [GetTaskResult](docs/sdks/tasks/README.md#gettaskresult) - Get task processing result
* [GetTask](docs/sdks/tasks/README.md#gettask) - Get a task
* [DownloadTaskExport](docs/sdks/tasks/README.md#downloadtaskexport) - Download task export file
* [UpdateTaskStatus](docs/sdks/tasks/README.md#updatetaskstatus) - Update task status

### [TaxAssociations](docs/sdks/taxassociations/README.md)

* [ListTaxAssociations](docs/sdks/taxassociations/README.md#listtaxassociations) - List tax associations
* [CreateTaxAssociation](docs/sdks/taxassociations/README.md#createtaxassociation) - Create Tax Association
* [GetTaxAssociation](docs/sdks/taxassociations/README.md#gettaxassociation) - Get Tax Association
* [UpdateTaxAssociation](docs/sdks/taxassociations/README.md#updatetaxassociation) - Update tax association
* [DeleteTaxAssociation](docs/sdks/taxassociations/README.md#deletetaxassociation) - Delete tax association

### [TaxRates](docs/sdks/taxrates/README.md)

* [GetTaxRates](docs/sdks/taxrates/README.md#gettaxrates) - Get tax rates
* [CreateTaxRate](docs/sdks/taxrates/README.md#createtaxrate) - Create a tax rate
* [GetTaxRate](docs/sdks/taxrates/README.md#gettaxrate) - Get a tax rate
* [UpdateTaxRate](docs/sdks/taxrates/README.md#updatetaxrate) - Update a tax rate
* [DeleteTaxRate](docs/sdks/taxrates/README.md#deletetaxrate) - Delete a tax rate

### [Tenants](docs/sdks/tenants/README.md)

* [GetTenantBillingUsage](docs/sdks/tenants/README.md#gettenantbillingusage) - Get billing usage for the current tenant
* [CreateTenant](docs/sdks/tenants/README.md#createtenant) - Create a new tenant
* [UpdateTenant](docs/sdks/tenants/README.md#updatetenant) - Update a tenant
* [GetTenant](docs/sdks/tenants/README.md#gettenant) - Get tenant

### [Users](docs/sdks/users/README.md)

* [CreateUser](docs/sdks/users/README.md#createuser) - Create service account
* [GetUserInfo](docs/sdks/users/README.md#getuserinfo) - Get current user
* [QueryUser](docs/sdks/users/README.md#queryuser) - Query users

### [Wallets](docs/sdks/wallets/README.md)

* [GetCustomerWallets](docs/sdks/wallets/README.md#getcustomerwallets) - Get Customer Wallets
* [GetWalletsByCustomerID](docs/sdks/wallets/README.md#getwalletsbycustomerid) - Get wallets by customer ID
* [CreateWallet](docs/sdks/wallets/README.md#createwallet) - Create a new wallet
* [QueryWallet](docs/sdks/wallets/README.md#querywallet) - Query wallets
* [QueryWalletTransaction](docs/sdks/wallets/README.md#querywallettransaction) - Query wallet transactions
* [GetWallet](docs/sdks/wallets/README.md#getwallet) - Get wallet
* [UpdateWallet](docs/sdks/wallets/README.md#updatewallet) - Update a wallet
* [GetWalletBalance](docs/sdks/wallets/README.md#getwalletbalance) - Get wallet balance
* [TerminateWallet](docs/sdks/wallets/README.md#terminatewallet) - Terminate a wallet
* [TopUpWallet](docs/sdks/wallets/README.md#topupwallet) - Top up wallet
* [GetWalletTransactions](docs/sdks/wallets/README.md#getwallettransactions) - Get wallet transactions

### [Webhooks](docs/sdks/webhooks/README.md)

* [HandleChargebeeWebhook](docs/sdks/webhooks/README.md#handlechargebeewebhook) - Handle Chargebee webhook events
* [HandleHubspotWebhook](docs/sdks/webhooks/README.md#handlehubspotwebhook) - Handle HubSpot webhook events
* [HandleMoyasarWebhook](docs/sdks/webhooks/README.md#handlemoyasarwebhook) - Handle Moyasar webhook events
* [HandleNomodWebhook](docs/sdks/webhooks/README.md#handlenomodwebhook) - Handle Nomod webhook events
* [HandleQuickbooksWebhook](docs/sdks/webhooks/README.md#handlequickbookswebhook) - Handle QuickBooks webhook events
* [HandleRazorpayWebhook](docs/sdks/webhooks/README.md#handlerazorpaywebhook) - Handle Razorpay webhook events
* [HandleStripeWebhook](docs/sdks/webhooks/README.md#handlestripewebhook) - Handle Stripe webhook events

### [Workflows](docs/sdks/workflows/README.md)

* [QueryWorkflow](docs/sdks/workflows/README.md#queryworkflow) - Query workflows

</details>
<!-- End Available Resources and Operations [operations] -->

<!-- Start Retries [retries] -->
## Retries

Some of the endpoints in this SDK support retries. If you use the SDK without any configuration, it will fall back to the default retry strategy provided by the API. However, the default retry strategy can be overridden on a per-operation basis, or across the entire SDK.

To change the default retry strategy for a single API call, simply provide a `retry.Config` object to the call by using the `WithRetries` option:
```go
package main

import (
	"context"
	flexprice "github.com/flexprice/flexprice-go"
	"github.com/flexprice/flexprice-go/models/components"
	"github.com/flexprice/flexprice-go/retry"
	"log"
	"models/operations"
)

func main() {
	ctx := context.Background()

	s := flexprice.New(
		"https://api.example.com",
		flexprice.WithSecurity("<YOUR_API_KEY_HERE>"),
	)

	res, err := s.Addons.CreateAddon(ctx, components.DtoCreateAddonRequest{
		LookupKey: "<value>",
		Name:      "<value>",
		Type:      components.TypesAddonTypeMultipleInstance,
	}, operations.WithRetries(
		retry.Config{
			Strategy: "backoff",
			Backoff: &retry.BackoffStrategy{
				InitialInterval: 1,
				MaxInterval:     50,
				Exponent:        1.1,
				MaxElapsedTime:  100,
			},
			RetryConnectionErrors: false,
		}))
	if err != nil {
		log.Fatal(err)
	}
	if res.DtoCreateAddonResponse != nil {
		// handle response
	}
}

```

If you'd like to override the default retry strategy for all operations that support retries, you can use the `WithRetryConfig` option at SDK initialization:
```go
package main

import (
	"context"
	flexprice "github.com/flexprice/flexprice-go"
	"github.com/flexprice/flexprice-go/models/components"
	"github.com/flexprice/flexprice-go/retry"
	"log"
)

func main() {
	ctx := context.Background()

	s := flexprice.New(
		"https://api.example.com",
		flexprice.WithRetryConfig(
			retry.Config{
				Strategy: "backoff",
				Backoff: &retry.BackoffStrategy{
					InitialInterval: 1,
					MaxInterval:     50,
					Exponent:        1.1,
					MaxElapsedTime:  100,
				},
				RetryConnectionErrors: false,
			}),
		flexprice.WithSecurity("<YOUR_API_KEY_HERE>"),
	)

	res, err := s.Addons.CreateAddon(ctx, components.DtoCreateAddonRequest{
		LookupKey: "<value>",
		Name:      "<value>",
		Type:      components.TypesAddonTypeMultipleInstance,
	})
	if err != nil {
		log.Fatal(err)
	}
	if res.DtoCreateAddonResponse != nil {
		// handle response
	}
}

```
<!-- End Retries [retries] -->

<!-- Start Error Handling [errors] -->
## Error Handling

Handling errors in this SDK should largely match your expectations. All operations return a response object or an error, they will never return both.

By Default, an API error will return `apierrors.APIError`. When custom error responses are specified for an operation, the SDK may also return their associated error. You can refer to respective *Errors* tables in SDK docs for more details on possible error types for each operation.

For example, the `CreateAddon` function may return the following errors:

| Error Type                    | Status Code | Content Type     |
| ----------------------------- | ----------- | ---------------- |
| apierrors.ErrorsErrorResponse | 400         | application/json |
| apierrors.ErrorsErrorResponse | 500         | application/json |
| apierrors.APIError            | 4XX, 5XX    | \*/\*            |

### Example

```go
package main

import (
	"context"
	"errors"
	flexprice "github.com/flexprice/flexprice-go"
	"github.com/flexprice/flexprice-go/models/apierrors"
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
		Name:      "<value>",
		Type:      components.TypesAddonTypeMultipleInstance,
	})
	if err != nil {

		var e *apierrors.ErrorsErrorResponse
		if errors.As(err, &e) {
			// handle error
			log.Fatal(e.Error())
		}

		var e *apierrors.ErrorsErrorResponse
		if errors.As(err, &e) {
			// handle error
			log.Fatal(e.Error())
		}

		var e *apierrors.APIError
		if errors.As(err, &e) {
			// handle error
			log.Fatal(e.Error())
		}
	}
}

```
<!-- End Error Handling [errors] -->

<!-- Start Custom HTTP Client [http-client] -->
## Custom HTTP Client

The Go SDK makes API calls that wrap an internal HTTP client. The requirements for the HTTP client are very simple. It must match this interface:

```go
type HTTPClient interface {
	Do(req *http.Request) (*http.Response, error)
}
```

The built-in `net/http` client satisfies this interface and a default client based on the built-in is provided by default. To replace this default with a client of your own, you can implement this interface yourself or provide your own client configured as desired. Here's a simple example, which adds a client with a 30 second timeout.

```go
import (
	"net/http"
	"time"

	"github.com/flexprice/flexprice-go"
)

var (
	httpClient = &http.Client{Timeout: 30 * time.Second}
	sdkClient  = flexprice.New(flexprice.WithClient(httpClient))
)
```

This can be a convenient way to configure timeouts, cookies, proxies, custom headers, and other low-level configuration.
<!-- End Custom HTTP Client [http-client] -->

<!-- Placeholder for Future Speakeasy SDK Sections -->

# Development

## Maturity

This SDK is in beta, and there may be breaking changes between versions without a major version update. Therefore, we recommend pinning usage
to a specific package version. This way, you can install the same version each time without breaking changes unless you are intentionally
looking for the latest version.

## Contributions

While we value open-source contributions to this SDK, this library is generated programmatically. Any manual changes added to internal files will be overwritten on the next generation. 
We look forward to hearing your feedback. Feel free to open a PR or an issue with a proof of concept and we'll do our best to include it in a future release. 

### SDK Created by [Speakeasy](https://www.speakeasy.com/?utm_source=flexprice&utm_campaign=go)
