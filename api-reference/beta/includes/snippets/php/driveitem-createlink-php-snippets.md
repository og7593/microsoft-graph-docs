---
description: "Automatically generated file. DO NOT MODIFY"
---

```php

<?php

// THIS SNIPPET IS A PREVIEW FOR THE KIOTA BASED SDK. NON-PRODUCTION USE ONLY
$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new CreateLinkPostRequestBody();
$requestBody->setType('view');

$requestBody->setScope('anonymous');

$requestBody->setPassword('String');

$recipientsDriveRecipient1 = new DriveRecipient();
$recipientsDriveRecipient1->setOdataType('microsoft.graph.driveRecipient');


$recipientsArray []= $recipientsDriveRecipient1;
$requestBody->setRecipients($recipientsArray);


$requestBody->setSendNotification(true);

$requestBody->setRetainInheritedPermissions(false);



$result = $graphServiceClient->drives()->byDriveId('drive-id')->items()->byDriveItemId('driveItem-id')->createLink()->post($requestBody);


```