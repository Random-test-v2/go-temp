<!-- Start SDK Example Usage [usage] -->
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