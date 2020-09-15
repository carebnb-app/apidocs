# Custom access codes

Fully automated Airbnb smartlock management

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

## Connect lock

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

Returns all logins for a given user.

**Request**

| Property | Value        |
| -------- | ------------ |
| Endpoint | /user/logins |
| Method   | GET          |

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
        "carebnbUserId": "79d76f9b-5a2e-4933-8741-ad7bb09bc85a",
        "deviceId": "10001001202039573056453031304758",
        "brand": "reagle",
        "name": "Front Door",
        "status": "locked",
        "batteryLevel": 87
      }
    ]
  }
}
```

Connects the user's lock account and return all locks for this login.
The expected value for the brand is "reagle".

**Request**

| Property | Value       |
| -------- | ----------- |
| Endpoint | /user/login |
| Method   | POST        |

**Request Headers**

| Property | Value       |
| -------- | ----------- |
| api-key  | **API_KEY** |
| user-id  | **USER_ID** |

### Disconect login

> Request body

```json
{
  "brand": "reagle"
}
```

> Response

```json
{
  "statusCode": 200
}
```

Disconect login for a given user and brand.

**Request**

| Property | Value       |
| -------- | ----------- |
| Endpoint | /user/login |
| Method   | DELETE      |

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
      "carebnbUserId": "79d76f9b-5a2e-4933-8741-ad7bb09bc25d",
      "deviceId": "10001001202039573056453031303433",
      "name": "Front Door",
      "batteryLevel": 87
    }
  ]
}
```

Returns all locks for a given user and brand.

**Request**

| Property | Value             |
| -------- | ----------------- |
| Endpoint | /user/login/locks |
| Method   | GET               |

**Request Headers**

| Property | Value       |
| -------- | ----------- |
| api-key  | **API_KEY** |
| user-id  | **USER_ID** |
