# Custom access codes

Fully automated Airbnb smartlock management!

Carebnb detects your reservations and automatically creates temporary and secure access codes with your Reagle™ smartlock.

Automatically secured access codes
[know more](https://carebnb.app/services/custom-access-codes/)

**Base URL**

<code>https://api.smartlocks.carebnb.app/v1</code>

**Request / response properties**

Some properties expect a pre defined value.

| Property    | Description                                           |
| ----------- | ----------------------------------------------------- |
| API_KEY     | An exclusive API key generated for each partner       |
| PROPERTY_ID | The property ID registered on Carebnb                 |
| USER_ID     | The user ID registered on Carebnb. Normally is a host |
| BRAND_NAME  | The expected value for the brand is "reagle"          |

## User's smartock account

First step is to connect the user's smartlock account with Carebnb system.
To do it, the user must inform his smartlock login.

After loging in, a list of locks assiciated to the smartlock account can be retrieved.

### Get all logins

> Response

```json
{
  "statusCode": 200,
  "data": [
    {
      "brand": "reagle",
      "userLogin": "user.reagle@gmail.com"
    }
  ]
}
```

Returns all smartlock logins for a given user, associated or not to his properties.

**Request**

| Property | Value         |
| -------- | ------------- |
| Endpoint | /locks/logins |
| Method   | GET           |

**Request Headers**

| Property | Value       |
| -------- | ----------- |
| api-key  | **API_KEY** |
| user-id  | **USER_ID** |

### Connect login

> Request body

```json
{
  "brand": "reagle",
  "email": "user.reagle@gmail.com",
  "password": "b610958a4e630f753b62e"
}
```

> Response

```json
{
  "statusCode": 200,
  "data": {
    "locks": [
      {
        "carebnbUserId": "79d76f9b-5a2e-4933-3719-ad7bb09bc74a",
        "deviceId": "10001001202039573056451597534562",
        "brand": "reagle",
        "name": "Front Door",
        "status": "locked",
        "batteryLevel": 87
      }
    ]
  }
}
```

Connects an smartlock account to a Carebnb account.
Also returns all smartlocks associated with informed account.

**Request**

| Property | Value       |
| -------- | ----------- |
| Endpoint | /lock/login |
| Method   | POST        |

**Request object parameters**

| param    | type   | description                         | required? |
| -------- | ------ | ----------------------------------- | --------- |
| brand    | String | The value for the brand is "reagle" | yes       |
| email    | String | Account's e-mail                    | yes       |
| password | String | Account's password                  | yes       |

**Request Headers**

| Property | Value       |
| -------- | ----------- |
| api-key  | **API_KEY** |
| user-id  | **USER_ID** |

### Disconnect login

> Response

```json
{
  "statusCode": 200
}
```

Disconnects smartlock account from Carebnb account.

<aside class="warning">
  This action is final. After disconnecting, all data associated to a smartlock will be permanently deleted.
</aside>

**Request**

| Property | Value                            |
| -------- | -------------------------------- |
| Endpoint | /lock/login/brand/**BRAND_NAME** |
| Method   | DELETE                           |

**Request Headers**

| Property | Value       |
| -------- | ----------- |
| api-key  | **API_KEY** |
| user-id  | **USER_ID** |

### Get all locks

> Response

```json
{
  "statusCode": 200,
  "data": [
    {
      "brand": "reagle",
      "status": "locked",
      "carebnbUserId": "79d76f9b-5a2e-4933-3719-ad7bb09bc74a",
      "deviceId": "10001001202039573056451597534562",
      "name": "Front Door",
      "batteryLevel": 87
    }
  ]
}
```

Returns all smartlocks associated to a Carebnb user account.

**Request**

| Property | Value                       |
| -------- | --------------------------- |
| Endpoint | /locks/brand/**BRAND_NAME** |
| Method   | GET                         |

**Request Headers**

| Property | Value       |
| -------- | ----------- |
| api-key  | **API_KEY** |
| user-id  | **USER_ID** |

## Link with Carebnb

This section is related to the smartlocks retrieved after associating the user's smartlock account with his Carebnb account.

Now our API has the hability to link smartlocks with properties.

### Get all locks

> Response

```json
{
  "statusCode": 200,
  "data": [
    {
      "brand": "reagle",
      "status": "locked",
      "carebnbUserId": "79d76f9b-5a2e-4933-3719-ad7bb09bc74a",
      "deviceId": "10001001202039573056451597534562",
      "name": "Front Door",
      "batteryLevel": 87,
      "carebnbPropertyId": "735c17b9-w3l0-47b2-a478-52f1ead854ax"
    }
  ]
}
```

Returns all locks for a given property.

**Request**

| Property | Value           |
| -------- | --------------- |
| Endpoint | /property/locks |
| Method   | GET             |

**Request Headers**

| Property    | Value           |
| ----------- | --------------- |
| api-key     | **API_KEY**     |
| user-id     | **USER_ID**     |
| property-id | **PROPERTY_ID** |

### Link locks with property

> Request body

```json
{
  "locks": [
    {
      "deviceId": "10001001202039573056451597534562",
      "brand": "reagle"
    }
  ]
}
```

> Response

```json
{
  "statusCode": 200,
  "data": {
    "locks": [
      {
        "carebnbUserId": "79d76f9b-5a2e-4933-3719-ad7bb09bc74a",
        "deviceId": "10001001202039573056451597534562",
        "brand": "reagle",
        "name": "Front Door",
        "status": "locked",
        "batteryLevel": 87
      }
    ]
  }
}
```

Link locks (yes, can be many) with a property.

A list of locks can be passed to be linked.

**Request**

| Property | Value           |
| -------- | --------------- |
| Endpoint | /property/locks |
| Method   | POST            |

**Request Headers**

| Property    | Value           |
| ----------- | --------------- |
| api-key     | **API_KEY**     |
| user-id     | **USER_ID**     |
| property-id | **PROPERTY_ID** |

### Unlink lock from property

> Response

```json
{
  "statusCode": 200
}
```

Unlink a lock from a given property.

**Request**

| Property | Value                                 |
| -------- | ------------------------------------- |
| Endpoint | /property/lock/deviceId/**DEVICE_ID** |
| Method   | PUT                                   |

**Request Headers**

| Property    | Value           |
| ----------- | --------------- |
| api-key     | **API_KEY**     |
| user-id     | **USER_ID**     |
| property-id | **PROPERTY_ID** |

## Temp codes

These are the temporary access codes generated directly with real smartlocks.

### Get all

> Response

```json
{
  "statusCode": 200,
  "data": [
    {
      "codeId": "970",
      "code": "75011031",
      "name": "Airbnb - Brittany",
      "isActive": false,
      "reservationCode": null,
      "startDate": "2020-02-13 16:00:00",
      "endDate": "2020-02-16 11:00:00",
      "isAutoGenerated": false
    }
  ]
}
```

Returns all temp codes for a given lock.

**Request**

| Property | Value                                  |
| -------- | -------------------------------------- |
| Endpoint | /lock/tempCodes/deviceId/**DEVICE_ID** |
| Method   | GET                                    |

**Request Headers**

| Property | Value       |
| -------- | ----------- |
| api-key  | **API_KEY** |
| user-id  | **USER_ID** |

### Create

> Request body

```json
{
  "brand": "reagle",
  "deviceId": "10001001202039573056451597534562",
  "name": "My temp code",
  "startDate": "2020-09-25 08:00:00",
  "endDate": "2020-06-30 15:00:00"
}
```

> Response

```json
{
  "statusCode": 200,
  "data": {
    "codeId": 825,
    "code": 9157482,
    "name": "My temp code",
    "isActive": true,
    "startDate": "2020-09-25 08:00:00",
    "endDate": "2020-09-30 15:00:00",
    "isAutoGenerated": false
  }
}
```

Create a new temp code for a given lock.

The start date cannot be less than today and the end date cannot be less than the start date.

**Request**

| Property | Value          |
| -------- | -------------- |
| Endpoint | /lock/tempCode |
| Method   | POST           |

**Request object params**

| param     | type   | description                                                                                             | required? |
| --------- | ------ | ------------------------------------------------------------------------------------------------------- | --------- |
| brand     | String | The value for the brand is "reagle"                                                                     | yes       |
| deviceId  | String | Unique identifier for a lock                                                                            | yes       |
| name      | String | Temp code's name                                                                                        | yes       |
| startDate | Date   | [ISO 8601 format](https://www.iso.org/iso-8601-date-and-time-format.html). Example: yyyy-mm-dd HH:mm:ss | yes       |
| endDate   | Date   | [ISO 8601 format](https://www.iso.org/iso-8601-date-and-time-format.html). Example: yyyy-mm-dd HH:mm:ss | yes       |

**Request Headers**

| Property | Value       |
| -------- | ----------- |
| api-key  | **API_KEY** |
| user-id  | **USER_ID** |

### Update

> Request body

```json
{
  "brand": "reagle",
  "deviceId": "10001001202039573056451597534562",
  "name": "My temp code",
  "isActive": true,
  "isAutoGenerated": false,
  "reservationCode": null
}
```

> Response

```json
{
  "statusCode": 200,
  "data": {
    "codeId": 125,
    "code": 8566321,
    "name": "carebnb",
    "isActive": true,
    "startDate": "2000-01-01 02:00:00",
    "endDate": "2000-01-01 02:00:00",
    "isAutoGenerated": true,
    "reservationCode": null
  }
}
```

Update a temp code for a given lock.

**Request**

| Property | Value                                      |
| -------- | ------------------------------------------ |
| Endpoint | /lock/tempCode/tempCodeId/**TEMP_CODE_ID** |
| Method   | PUT                                        |

**Request Headers**

| Property | Value       |
| -------- | ----------- |
| api-key  | **API_KEY** |
| user-id  | **USER_ID** |

## Messages

These are the messages that will be sent to the user after generating the reservation code.

### Get all

> Response

```json
{
  "statusCode": 200,
  "data": [
    {
      "deletedAt": null,
      "_id": "5f6a9762e0adq4f93789145f",
      "carebnbUserId": "79d76f9b-5a2e-4933-3719-ad7bb09bc74a",
      "carebnbPropertyId": "735c17b9-w3l0-47b2-a478-52f1ead854ax",
      "event": "smartlocks",
      "message": "My message is here",
      "createdAt": "2020-09-23T00:31:30.460Z",
      "updatedAt": "2020-09-23T00:31:40.068Z",
      "__v": 0
    }
  ]
}
```

Returns all messages for a given property.

**Request**

| Property | Value     |
| -------- | --------- |
| Endpoint | /messages |
| Method   | GET       |

**Request Headers**

| Property    | Value           |
| ----------- | --------------- |
| api-key     | **API_KEY**     |
| user-id     | **USER_ID**     |
| property-id | **PROPERTY_ID** |

### Create

> Request body

```json
{
  "event": "smartlocks",
  "message": "My message is here"
}
```

> Response

```json
{
  "statusCode": 200,
  "data": {
    "_id": "5f6a9762e0dcb4f93787186f",
    "deletedAt": null,
    "carebnbUserId": "79d76f9b-5a2e-4933-3719-ad7bb09bc74a",
    "carebnbPropertyId": "735c17b9-w3l0-47b2-a478-52f1ead854ax",
    "event": "smartlocks",
    "message": "My message is here",
    "createdAt": "2020-09-23T00:31:30.460Z",
    "updatedAt": "2020-09-23T00:31:30.460Z",
    "__v": 0
  }
}
```

Create a new message for a given property.

**Request**

| Property | Value    |
| -------- | -------- |
| Endpoint | /message |
| Method   | POST     |

**Request object params**

| param   | type   | description                                               | required? |
| ------- | ------ | --------------------------------------------------------- | --------- |
| event   | String | Accepted values are "smartlocks" or "smartlocks-template" | yes       |
| message | String | Message to be sent                                        | yes       |

**Request Headers**

| Property    | Value           |
| ----------- | --------------- |
| api-key     | **API_KEY**     |
| user-id     | **USER_ID**     |
| property-id | **PROPERTY_ID** |

### Update

> Request body

```json
{
  "event": "smartlocks",
  "message": "My message updated"
}
```

> Response

```json
{
  "statusCode": 200,
  "data": {
    "_id": "5f6a9762e0dcb4f93787186f",
    "deletedAt": null,
    "carebnbUserId": "79d76f9b-5a2e-4933-3719-ad7bb09bc74a",
    "carebnbPropertyId": "735c17b9-w3l0-47b2-a478-52f1ead854ax",
    "event": "smartlocks",
    "message": "My message is here",
    "createdAt": "2020-09-23T00:31:30.460Z",
    "updatedAt": "2020-09-23T00:31:30.460Z",
    "__v": 0
  }
}
```

Update a message for givem property

**Request**

| Property | Value                             |
| -------- | --------------------------------- |
| Endpoint | /message/messageId/**MESSAGE_ID** |
| Method   | PUT                               |

**Request object params**

| param   | type   | description                                               | required? |
| ------- | ------ | --------------------------------------------------------- | --------- |
| event   | String | Accepted values are "smartlocks" or "smartlocks-template" | yes       |
| message | String | Message to be sent                                        | yes       |

**Request Headers**

| Property    | Value           |
| ----------- | --------------- |
| api-key     | **API_KEY**     |
| user-id     | **USER_ID**     |
| property-id | **PROPERTY_ID** |
