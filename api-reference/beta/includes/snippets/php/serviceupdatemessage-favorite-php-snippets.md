---
description: "Automatically generated file. DO NOT MODIFY"
---

```php

<?php

// THIS SNIPPET IS A PREVIEW FOR THE KIOTA BASED SDK. NON-PRODUCTION USE ONLY
$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new FavoritePostRequestBody();
$requestBody->setMessageIds(['MC172851', 'MC167983', 	]);



$result = $graphServiceClient->admin()->serviceAnnouncement()->messages()->favorite()->post($requestBody);


```