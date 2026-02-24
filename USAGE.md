<!-- Start SDK Example Usage [usage] -->
```go
package main

import (
	"context"
	"log"
	"undefined"
	"undefined/models/components"
)

func main() {
	ctx := context.Background()

	s := undefined.New(
		"https://api.example.com",
		undefined.WithSecurity("<YOUR_API_KEY_HERE>"),
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