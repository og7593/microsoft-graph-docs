---
description: "Automatically generated file. DO NOT MODIFY"
---

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

var graphClient = new GraphServiceClient(requestAdapter);

var requestBody = new Microsoft.Graph.ServicePrincipals.Item.Synchronization.Jobs.Item.ProvisionOnDemand.ProvisionOnDemandPostRequestBody
{
	Parameters = new List<SynchronizationJobApplicationParameters>
	{
		new SynchronizationJobApplicationParameters
		{
			RuleId = "6c409270-f78a-4bc6-af23-7cf3ab6482fe",
			Subjects = new List<SynchronizationJobSubject>
			{
				new SynchronizationJobSubject
				{
					ObjectId = "CN=AdeleV,CN=Users,DC=corp,DC=chicago,DC=com",
					ObjectTypeName = "user",
				},
			},
		},
	},
};
var result = await graphClient.ServicePrincipals["{servicePrincipal-id}"].Synchronization.Jobs["{synchronizationJob-id}"].ProvisionOnDemand.PostAsync(requestBody);


```