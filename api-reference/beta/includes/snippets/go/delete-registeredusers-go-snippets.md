---
description: "Automatically generated file. DO NOT MODIFY"
---

```go


import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  //other-imports
)

graphClient := msgraphsdk.NewGraphServiceClientWithCredentials(cred, scopes)



graphClient.Devices().ByDeviceId("device-id").RegisteredUsers().ByRegisteredUserId("directoryObject-id").Ref().Delete(context.Background(), nil)


```