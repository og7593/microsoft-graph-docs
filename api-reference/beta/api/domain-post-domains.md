---
title: "Create domain"
description: "Adds a domain to the tenant."
author: "adimitui"
localization_priority: Normal
ms.prod: "microsoft-identity-platform"
doc_type: apiPageType
---

# Create domain

Namespace: microsoft.graph

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Adds a domain to the tenant.

**Important**: You cannot use an associated domain with your Azure AD tenant until ownership is verified. See [List verificationDnsRecords](domain-list-verificationdnsrecords.md) for details. Root domains require verification. For example, contoso.com requires verification. If a root domain is verified, subdomains of the root domain are automatically verified. For example, subdomain.contoso.com is automatically be verified if contoso.com has been verified.

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](/graph/permissions-reference).


|Permission type      | Permissions (from least to most privileged)              |
|:--------------------|:---------------------------------------------------------|
|Delegated (work or school account) | Directory.AccessAsUser.All    |
|Delegated (personal Microsoft account) | Not supported.    |
|Application | Domain.ReadWrite.All |

## HTTP request

<!-- { "blockType": "ignored" } -->
```http
POST /domains
```

## Request headers

| Name       | Description|
|:---------------|:----------|
| Authorization  | Bearer {token}. Required.|
| Content-Type  | application/json |

## Request body

In the request body, supply a JSON representation of [domain](../resources/domain.md) object.

> The request body contains the id property for the new domain. Id is the only property that can be specified and it is required, with the exception of onMicrosoft domains and branding domains, which are special purpose domains that have extra required properties. The id property value is the fully qualified domain name to create.

### OnMicrosoft Domain

This is a microsoft provisioned domain also known as MOERA (Microsoft Online Email Routable Address) domain owned by the organization that has the following characteristics:

- The domain name extends the `onmicrosoft.com` domain suffix.
- It has `MoeraDomain` as a `supportedService`.
- It has the `isInitial` property set to:
  - `true` if it is a primary `OnMicrosoft` domain
  - `false` if it is a secondary `OnMicrosoft` domain
- There can only be one primary domain per organization.

`OnMicrosoft` domains are initial domains that enable organizations to perform full organization(tenant) wide rename which transalates to renaming of Microsoft 355, Azure and other Microsoft services. Services such as Sharepoint Online rely on `OnMicrosoft` domains to reserve namespaces for sharepoint urls. For example: a organization with Office 365 domain of contoso.onmicrosoft.com, will get a root URL of contoso.sharepoint.com.

> The request body of `OnMicrosoft` domains must contain the `id` property, `isVerified` property which must be set to true and `supportedServices` collection which contains `MoeraDomain` value.

### Branding Domain

This is a microsoft provisioned domain that helps to improve product branding e.g. @contoso.microsoft365.com, @contoso.microsoftazure.com, etc. New customers can sign up with new branding domains and existing customer can add additional branding domains. They have the following characteristics:

- The domain suffix is a microsoft online domain e.g. `contoso.`**`onmicrosoft.com`**.
- The domain prefix is a verified third level domain name belonging to the organization. It is also globally unique.

A number of constraints apply when working with branding domains. New organization(tenants) will be created with only one initial branding domain, but organization admins may add other branding domains later. For example, a customer may sign up with `@contoso.microsoft365.com` but then go to the Admin portal to also add the branding domain `@contoso.microsoftazure.com`.

The default selected initial branding domain name on the drop-down list will be derived from the customer's first purchase. For example, if the customer is signing-up to purchase a Microsoft365 product then the default user choice will be @contoso.microsoft365.com. Likewise, if the customer is signing up in the Windows Azure portal then the default choice will be @microsoftazure.com.

Microsoft services teams will be responsible for determining the actual branding domain name suffixes.

## Response

If successful, this method returns `201 Created` response code and [domain](../resources/domain.md) object in the response body.

## Example

##### Request

In the request body, supply a JSON representation of [domain](../resources/domain.md) object. This is the case when adding a domain whose ownership is not verified.

<!-- {
  "blockType": "request",
  "id": "create_domain_from_domains"
}-->
```http
POST https://graph.microsoft.com/beta/domains
Content-type: application/json
Content-length: 192

{
  "id": "contoso.com"
}
```

In the case of adding an `OnMicrosoft`(MOERA) domain the `isVerified` property with value of `true` and `supportedServices` collection property with value of `MoeraDomain` must be supplied in addition to the required `id` property.

```http
POST https://graph.microsoft.com/beta/domains
Content-type: application/json

{
    "id": "contoso.onmicrosoft.com",
    "isVerified": true,
    "supportedServices": [
        "MoeraDomain"
    ]
}
```

In the case of adding a branding domain, the `isVerified` property with a value of `true` must be supplied in addition to the required `id` property.

##### Response
Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.domain"
} -->
```http
HTTP/1.1 201 Created
Content-type: application/json
Content-length: 192

{
  "authenticationType": "authenticationType-value",
  "availabilityStatus": "availabilityStatus-value",
  "id": "contoso.com",
  "isAdminManaged": true,
  "isDefault": true,
  "isInitial": true,
  "isRoot": true
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!--
{
  "type": "#page.annotation",
  "description": "Create domain",
  "keywords": "",
  "section": "documentation",
  "tocPath": "",
  "suppressions": []
}
-->
