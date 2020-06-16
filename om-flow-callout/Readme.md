# Use Lightning Flow to Make REST Callout in Vlocity OM
## Overview

**Business Requirements for the OM**  
You resell "V-Suite" cloud service to your customers. To activiate the service purchased by the customer, you need make two REST API calls to the end-points exposed by the "V-Suite" service provider.
1. Create Customer record in the system of "V-Suite" service provider.
2. Create service entitlement under the customer record created above.


```
/Customers/*
Customer JSON
{
  "name": string,
  "orgDisplayName": string,
  "orgPostalAddress": {
    "revision": number,
    "regionCode": string,
    "languageCode": string,
    "postalCode": string,
    "sortingCode": string,
    "administrativeArea": string,
    "locality": string,
    "sublocality": string,
    "addressLines": [
      string
    ],
    "recipients": [
      string
    ],
    "organization": string
  },
  "primaryContactInfo": {
    "firstName": string,
    "lastName": string,
    "displayName": string,
    "email": string,
    "title": string,
    "phone": string
  },
  "alternateEmail": string,
  "domain": string,
  "createTime": string,
  "updateTime": string,
  "cloudIdentityId": string,
  "languageCode": string
}
```
```
/Customers/*/Entitlements
Entitlement JSON
{
  "name": string,
  "createTime": string,
  "updateTime": string,
  "channelPartnerId": string,
  "offer": string,
  "numUnits": number,
  "maxUnits": number,
  "assignedUnits": number,
  "commitmentSettings": {
    object (CommitmentSettings)
  },
  "provisioningState": enum (ProvisioningState),
  "provisionedService": {
    object (ProvisionedService)
  },
  "suspensionReasons": [
    enum (SuspensionReason)
  ],
  "purchaseOrderId": string
}

```
