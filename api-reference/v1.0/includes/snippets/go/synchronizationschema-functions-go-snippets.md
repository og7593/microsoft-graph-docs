---
description: "Automatically generated file. DO NOT MODIFY"
---

```go


import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  //other-imports
)

graphClient := msgraphsdk.NewGraphServiceClientWithCredentials(cred, scopes)



result, err := graphClient.ServicePrincipals().ByServicePrincipalId("servicePrincipal-id").Synchronization().Jobs().ByJobId("synchronizationJob-id").Schema().Functions().Get(context.Background(), nil)


```