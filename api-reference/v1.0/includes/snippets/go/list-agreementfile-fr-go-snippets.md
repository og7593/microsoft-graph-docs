---
description: "Automatically generated file. DO NOT MODIFY"
---

```go


import (
	  "context"
	  abstractions "github.com/microsoft/kiota-abstractions-go"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphagreements "github.com/microsoftgraph/msgraph-sdk-go/agreements"
	  //other-imports
)

graphClient := msgraphsdk.NewGraphServiceClientWithCredentials(cred, scopes)


headers := abstractions.NewRequestHeaders()
headers.Add("Accept-Language", "fr-FR")

configuration := &graphagreements.AgreementItemFileRequestBuilderGetRequestConfiguration{
	Headers: headers,
}

result, err := graphClient.Agreements().ByAgreementId("agreement-id").File().Get(context.Background(), configuration)


```