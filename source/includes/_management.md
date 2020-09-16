# Basic Management

As a partner, you need manners to manage hosts and properties (listings) under your umbrella.
In this section, We describe all endpoints for this mean.

**Base URL**

<code>https://api.carebnb.app/v1</code>





## Manage users (hosts)

### Get all

> Response

```json
{
  "statusCode": 200,
  "message": "Users list",
  "data": [
		{
			"userId": "79d76f9b-5a2e-4933-8741-...",
			"name": "John Doe",
			"email": "john.doe@mail.co",
			"birthDate": "1990-01-01",
			"gender": "male",
			"cellphone": "+55(61)12375-4345",
			"address": "Happy street at 5th avenue",
			"countryCode": "USA",
			"zipCode": "71.672-188"
		},
		...
  ]
}
```

Returns all users. Normally are hosts.
These users will be the "owners" of properties.

**Request**

Property | Value
-------- | -------
Endpoint | /users
Method   | GET

**Request Headers**

Property    | Value
----------- | -------
api-key | **API_KEY**





### Get

> Response

```json
{
  "statusCode": 200,
  "message": "User info",
  "data": {
		"userId": "79d76f9b-5a2e-4933-8741-9123812...",
		"name": "John Doe",
		"email": "john.doe@mail.co",
		"birthDate": "1990-01-01",
		"gender": "male",
		"cellphone": "+55(61)12375-4345",
		"address": "Happy street at 5th avenue",
		"countryCode": "USA",
		"zipCode": "71.672-188"
	}
}
```

Returns a user. Normally is a host.
These users will be the "owners" of properties.

**Request**

Property | Value
-------- | -------
Endpoint | /user/userId/**USER_ID**
Method   | GET

**Request Headers**

Property    | Value
----------- | -------
api-key | **API_KEY**





### Create

> Request body

```json
{
	"name": "John Doe",
	"email": "john.doe@mail.co",
	"birthDate": "1990-01-01",
	"gender": "male",
	"cellphone": "+55(61)12375-4345",
	"address": "Happy street at 5th avenue",
	"countryCode": "USA",
	"zipCode": "71.672-188"
}
```

> Response

```json
{
  "statusCode": 201,
  "message": "User created",
  "data": {
		"userId": "79d76f9b-5a2e-4933-8741-...",
		"name": "John Doe",
		"email": "john.doe@mail.co",
		"birthDate": "1990-01-01",
		"gender": "male",
		"cellphone": "+55(61)12375-4345",
		"address": "Happy street at 5th avenue",
		"countryCode": "USA",
		"zipCode": "71.672-188"
	}
}
```

Creates a new user. Normally is a host.
This user will be the "owner" of properties.

**Request**

Property | Value
-------- | -------
Endpoint | /user
Method   | POST

**Request object params**

| param | type | description | required? |
| ------ | ------ | ------ | ------ |
| name | String(255) | Fullname in native alphabet | yes
| email | String(64) | To communicate with the host | yes
| birthDate | Date | [ISO 8601 format](https://www.iso.org/iso-8601-date-and-time-format.html). Example: yyyy-mm-dd  | -
| gender | String(8) | Valid values: "male", "female", "other" | -
| cellphone | String(32) | Full phone number with country and area codes. | -
| address | String(64) | Real full street address, no country and no zip code. | -
| countryCode | String(3) | [ISO 3 format](https://unstats.un.org/unsd/tradekb/knowledgebase/country-code) | -
| zipCode | String(32) | Obeying each country specification. | -

**Request Headers**

Property    | Value
----------- | -------
api-key | **API_KEY**





### Update

> Request body

```json
{
	"name": "John Doe",
	"email": "john.doe@mail.co",
	"birthDate": "1990-01-01",
	"gender": "male",
	"cellphone": "+55(61)12375-4345",
	"address": "Happy street at 5th avenue",
	"countryCode": "USA",
	"zipCode": "71.672-188"
}
```

> Response

```json
{
  "statusCode": 200,
  "message": "User updated",
  "data": {
		"userId": "79d76f9b-5a2e-4933-8741-...",
		"name": "John Doe",
		"email": "john.doe@mail.co",
		"birthDate": "1990-01-01",
		"gender": "male",
		"cellphone": "+55(61)12375-4345",
		"address": "Happy street at 5th avenue",
		"countryCode": "USA",
		"zipCode": "71.672-188"
  }
}
```

Updates a user. Normally is a host.
This user will be the "owner" of properties.

**Request**

Property | Value
-------- | -------
Endpoint | /user/userId/**USER_ID**
Method   | PUT

**Request object params**

| param | type | description | required? |
| ------ | ------ | ------ | ------ |
| name | String(255) | Fullname in native alphabet | yes
| email | String(64) | To communicate with the host | yes
| birthDate | Date | [ISO 8601 format](https://www.iso.org/iso-8601-date-and-time-format.html). Example: yyyy-mm-dd  | -
| gender | String(8) | Valid values: "male", "female", "other" | -
| cellphone | String(32) | Full phone number with country and area codes. | -
| address | String(64) | Real full street address, no country and no zip code. | -
| countryCode | String(3) | [ISO 3 format](https://unstats.un.org/unsd/tradekb/knowledgebase/country-code) | -
| zipCode | String(32) | Obeying each country specification. | -

**Request Headers**

Property    | Value
----------- | -------
api-key | **API_KEY**





### Delete

> Response

```json
{
  "statusCode": 200,
  "message": "User deleted"
}
```

Deletes a user. Normally is a host.
A user cannot be deleted if it owns a property.

**Request**

Property | Value
-------- | -------
Endpoint | /user/userId/**USER_ID**
Method   | PUT

**Request Headers**

Property    | Value
----------- | -------
api-key | **API_KEY**





## Manage properties (listings)

### Get all

> Response

```json
{
  "statusCode": 200,
  "message": "Properties list",
  "data": [
    {
      "propertyId": "ce155e19-66f1-4f64-9aa2-...",
      "description": "Cozy three bedrooms apartment",
      "coverImage": "https://a0.muscache.com/im/pictures/3ff8e57d-59c9-4193-a6c1-c89f2be79ea2.jpg?aki_policy=medium",
      "address": "4 Rue Marie France, Canton-Tremblay, QC G7G 4N4, Canada",
      "countryCode": "CA",
      "timeZoneName": "America/New_York",
      "zipCode": "G7G 4N4"
    },
    ...
  ]
}
```

Returns all properties (listings).

**Request**

Property | Value
-------- | -------
Endpoint | /properties
Method   | GET

**Request Headers**

Property    | Value
----------- | -------
api-key | **API_KEY**





### Get all by user (host)

> Response

```json
{
  "statusCode": 200,
  "message": "Users list",
  "data": [
    {
      "userId": "79d76f9b-5a2e-4933-8741-ad7bb09bc...",
      "name": "John Doe",
      "email": "john.doe@mail.co",
      "birthDate": null,
      "gender": "male",
      "cellphone": "991321321",
			"countryCode": "CA",
			"timeZoneName": "America/New_York",
			"zipCode": "G7G 4N4"
		},
		...
  ]
}
```

Returns all properties associated to a user, normally a host.

**Request**

Property | Value
-------- | -------
Endpoint | /properties/userId/**USER_ID**
Method   | GET

**Request Headers**

Property    | Value
----------- | -------
api-key | **API_KEY**





### Get

> Response

```json
{
  "statusCode": 200,
  "message": "Property info",
  "data": {
    "propertyId": "76e122d8-3bb7-4e0e-843c-...",
    "description": "Cozy three bedrooms apartment",
    "coverImage": "https://a0.muscache.com/im/pictures/3ff8e57d-59c9-4193-a6c1-c89f2be79ea2.jpg?aki_policy=medium",
    "address": "4 Rue Marie France, Canton-Tremblay, QC G7G 4N4, Canada",
    "countryCode": "CA",
    "timeZoneName": "America/New_York",
    "zipCode": "G7G 4N4"
  }
}
```

Returns a property associated to a user, normally a host.

**Request**

Property | Value
-------- | -------
Endpoint | /property/propertyId/**PROPERTY_ID**
Method   | GET

**Request Headers**

Property    | Value
----------- | -------
api-key | **API_KEY**





### Create

> Request body

```json
{
	"userId": "q1w2e3r4-t5y6-u7i8-o9p0-q1e3t5u7i...",
	"name": "Cozy Townhome + Hotel Standard w/amenities",
	"url": "https://www.airbnb.ca/rooms/123623562",
	"address": "Jacksonville, Florida, United States",
	"countryCode": "USA",
	"postalCode": "32258"
}
```

> Response

```json
{
	"userId": "76e122d8-3bb7-4e0e-843c-e26fc0932...",
	"description": "Cozy Townhome + Hotel Standard w/amenities",
	"coverImage": "https://a0.muscache.com/im/pictures/3ff8e57d-59c9-4193-a6c1-c89f2be79ea2.jpg?aki_policy=medium",
	"timeZoneName": "America/California",
	"address": "Jacksonville, Florida, United States",
	"countryCode": "USA",
	"zipCode": "9035"
}
```

Creates property associated to a user, normally a host.

**Request**

Property | Value
-------- | -------
Endpoint | /property
Method   | POST

**Request object params**

| param | type | description | required? |
| ------ | ------ | ------ | ------ |
| userId | String(32) | The user ID registered on Carebnb. Normally is a host. | yes
| name | String(255) | A short description. | yes
| timezone | String(255) | [TZ Database name format](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones). | yes
| url | String(255) | A public url. | -
| address | String(64) | Real full street address, no country and no zip code. | -
| countryCode | String(3) | [ISO 3 format](https://unstats.un.org/unsd/tradekb/knowledgebase/country-code) | -
| zipCode | String(32) | Obeying each country specification. | -

**Request Headers**

Property    | Value
----------- | -------
api-key | **API_KEY**





### Update

> Request body

```json
{
	"userId": "q1w2e3r4-t5y6-u7i8-o9p0-q1e3t5u7i...",
	"name": "Cozy Townhome + Hotel Standard w/amenities",
	"url": "https://www.airbnb.ca/rooms/123623562",
	"address": "Jacksonville, Florida, United States",
	"countryCode": "USA",
	"postalCode": "32258"
}
```

> Response

```json
{
	"userId": "76e122d8-3bb7-4e0e-843c-e26fc0931...",
	"description": "Cozy Townhome + Hotel Standard w/amenities",
	"coverImage": "https://a0.muscache.com/im/pictures/3ff8e57d-59c9-4193-a6c1-c89f2be79ea2.jpg?aki_policy=medium",
	"timeZoneName": "America/California",
	"address": "Jacksonville, Florida, United States",
	"countryCode": "USA",
	"zipCode": "9035"
}
```

Updates a property associated to a user, normally a host.

**Request**

Property | Value
-------- | -------
Endpoint | /property/propertyId/**PROPERTY_ID**
Method   | PUT

**Request object params**

| param | type | description | required? |
| ------ | ------ | ------ | ------ |
| userId | String(32) | The user ID registered on Carebnb. Normally is a host. | yes
| name | String(255) | A short description. | yes
| timezone | String(255) | [TZ Database name format](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones). | yes
| url | String(255) | A public url. | -
| address | String(64) | Real full street address, no country and no zip code. | -
| countryCode | String(3) | [ISO 3 format](https://unstats.un.org/unsd/tradekb/knowledgebase/country-code) | -
| zipCode | String(32) | Obeying each country specification. | -

**Request Headers**

Property    | Value
----------- | -------
api-key | **API_KEY**





### Delete

> Response

```json
{
  "statusCode": 200,
  "message": "Property deleted"
}
```

Deletes a property associated to a user, normally a host.

**Request**

Property | Value
-------- | -------
Endpoint | /property/propertyId/**PROPERTY_ID**
Method   | DELETE

**Request Headers**

Property    | Value
----------- | -------
api-key | **API_KEY**





## Manage services

These are the actions related to checking, enabling or disabling services for a given property.

<aside class="notice">
  All operations here are "by property". Which means, the PROPERTY_ID value must be passed to every call.
</aside>

### Get all

> Response

```json
{
  "statusCode": 200,
  "message": "Services list",
  "data": [
    {
      "serviceId": "a3921911-2192-4279-99a8-f67c97652...",
      "description": "Automatic check in check out",
      "url": "https://api.messages.carebnb.app",
      "active": true
		},
		...
  ]
}
```

Returns all services associated to a property.

**Request**

Property | Value
-------- | -------
Endpoint | /services
Method   | GET

**Request Headers**

Property    | Value
----------- | -------
api-key | **API_KEY**
property-id | **PROPERTY_ID**




### Get

> Response

```json
{
  "statusCode": 200,
  "message": "Service info",
  "data": {
		"serviceId": "a3921911-2192-4279-99a8-f67c97652...",
		"description": "Automatic check in check out",
		"url": "https://api.messages.carebnb.app",
		"active": true
	}
}
```

Returns info and status of a specific service associated to a property.

**Request**

Property | Value
-------- | -------
Endpoint | /service/serviceId/**SERVICE_ID**
Method   | GET

**Request Headers**

Property    | Value
----------- | -------
api-key | **API_KEY**
property-id | **PROPERTY_ID**





### Enable

> Response

```json
{
  "statusCode": 200,
  "message": "Service enabled",
  "data": [
    {
      "serviceId": "a3921911-2192-4279-99a8-f67c97652...",
      "description": "Automatic check in check out",
      "url": "https://api.messages.carebnb.app",
      "active": true
    }
  ]
}
```

Enable a service associated to a property.

**Request**

Property | Value
-------- | -------
Endpoint | /service/enable/serviceId/**SERVICE_ID**
Method   | POST

**Request Headers**

Property    | Value
----------- | -------
api-key | **API_KEY**
property-id | **PROPERTY_ID**





### Disable

> Response

```json
{
  "statusCode": 200,
  "message": "Service disabled",
  "data": [
    {
      "serviceId": "a3921911-2192-4279-99a8-f67c97652...",
      "description": "Automatic check in check out",
      "url": "https://api.messages.carebnb.app",
      "active": false
    }
  ]
}
```

Disable a service associated to a property.

**Request**

Property | Value
-------- | -------
Endpoint | /service/disable/serviceId/**SERVICE_ID**
Method   | POST

**Request Headers**

Property    | Value
----------- | -------
api-key | **API_KEY**
property-id | **PROPERTY_ID**