# General

**Base URL**

<code>https://api.carebnb.app/api/v1</code>





## Get property info

> Response

```json
{
   "data":[
      {
         "gid":"q1w2e3r4-q1w2-e3r4-t5y6-u7i8o9p0q1w2",
         "coverImage":"https://a0.muscache.com/im/pictures/3ff8e57d-59c9-4193-a6c1-c89f2be79ea2.jpg?aki_policy=medium",
         "description":"Cozy three bedrooms apartment",
         "language":"en",
         "country":"Canada",
         "countryCode":"CA",
         "state":"QC",
         "city":"Canton-Tremblay",
         "address":"4 Rue Marie France, Canton-Tremblay, QC G7G 4N4, Canada",
         "street":"4 Rue Marie France",
         "zipcode":"G7G 4N4",
         "checkOutWindow":"11",
         "checkinWindowStartAt":"16",
         "checkinWindowEndAt":"16",
         "isPushNotificationSended":false,
         "location":{
            "x":30.130421,
            "y":-81.536018
         },
         "timeZoneName":"America/New_York",
         "createdAt":"2020-07-19T01:24:19.190Z",
         "updatedAt":"2020-07-19T01:24:19.190Z",
         "deletedAt":null,
         "ownerUserGid":"e3r4t5y6-i8o9-w2e3-r4t5-y6u7i8o9w2e3",
         "services":[
            {
               "gid":"9b5e910c-9c03-4696-9eac-d0b9dbe5c110",
               "name":"stories",
               "description":"Smart guestbook",
               "type":"listing",
               "protocols":[
                  "reservations"
               ],
               "url":null,
               "createdAt":"2020-07-06T18:41:54.107Z",
               "updatedAt":"2020-07-06T18:41:54.107Z",
               "deletedAt":null,
               "propertyService":{
                  "createdAt":"2020-08-16T13:16:30.601Z",
                  "updatedAt":"2020-08-16T13:16:30.601Z",
                  "propertyGid":"q1w2e3r4-q1w2-e3r4-t5y6-u7i8o9p0q1w2",
                  "serviceGid":"t5y6u7i8-p0q1-w2e3-r4t5-y6u7i8o9p0q1"
               }
            },
            ...
         ],
         "user":{
            "name":"Demétrio Guilardi"
         }
      }
   ]
}
```

Returns all info for a given property.
It contains the address, as well as all services full info.

Property | Value
-------- | -------
Endpoint | /helpers/getPropertyByUserProperty/carebnbUserId/**USER_ID**/carebnbPropertyId/**PROPERTY_ID**
Method   | GET

An authentication token must be passed to this endpoint in its request **header**.

<code>{
   "token":89f5u3q4p5uq43gq5uh34p895uhw34p5u34hp9guj905...
}
</code>





## Get service info

> Response

```json
{
   "statusCode":200,
   "message":"Services by property.",
   "data":{
      "gid":"q1w2e3r4-r4t5-y6u7-i8o9-p0q1w2e3r4t5y6",
      "name":SERVICE_NAME,
      "url":SERVICE_SETUP_URL,
      "description":SERVICE_DESCRIPTION,
      "active":SERVICE_STATUS
   }
}
```

Returns status along with basic info for a given service.

Property | Value
-------- | -------
Endpoint | /owner/services/property/**PROPERTY_ID**/serviceName/**SERVICE_NAME**
Method   | GET





## Enable / disable service

> Request

```json
{
  "carebnbPropertyId":"q1w2e3r4-q1w2-e3r4-t5y6-u7i8o9p0q1w2",
  "serviceName":SERVICE_NAME,
  "active":FALSE_OR_TRUE
}
```

> Response

```json
{
  "statusCode":200,
  "message":"Service saved."
}
```

Enables or disables a service for a given property.

Property | Value
-------- | -------
Endpoint | /v1/owner/services/property
Method   | POST

An authentication token must be passed to this endpoint in its request **header**.

<code>{
   "token":89f5u3q4p5uq43gq5uh34p895uhw34p5u34hp9guj905...
}
</code>