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
		}
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
  "message": "Users info",
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

**Request Headers**

Property    | Value
----------- | -------
api-key | **API_KEY**
Content-Type | application/json

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

**Request Headers**

Property    | Value
----------- | -------
api-key | **API_KEY**
Content-Type | application/json

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
@TODO
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
@TODO
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
@TODO
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
	"userId": "q1w2e3r4-t5y6-u7i8-o9p0-q1e3t5u7i8o9",
	"name": "Cozy Townhome + Hotel Standard w/amenities",
	"url": "https://www.airbnb.ca/rooms/123623562",
	"address": "Jacksonville, Florida, United States",
	"countryCode": "USA",
	"postalCode": "32258"
}
```

> Response

```json
@TODO
```

Creates property associated to a user, normally a host.

**Request**

Property | Value
-------- | -------
Endpoint | /property
Method   | POST

**Request Headers**

Property    | Value
----------- | -------
api-key | **API_KEY**
Content-Type | application/json

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





### Update

> Request body

```json
{
	"userId": "q1w2e3r4-t5y6-u7i8-o9p0-q1e3t5u7i8o9",
	"name": "Cozy Townhome + Hotel Standard w/amenities",
	"url": "https://www.airbnb.ca/rooms/123623562",
	"address": "Jacksonville, Florida, United States",
	"countryCode": "USA",
	"postalCode": "32258"
}
```

> Response

```json
@TODO
```

Updates a property associated to a user, normally a host.

**Request**

Property | Value
-------- | -------
Endpoint | /property/propertyId/**PROPERTY_ID**
Method   | PUT

**Request Headers**

Property    | Value
----------- | -------
api-key | **API_KEY**
Content-Type | application/json

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





### Delete

> Response

```json
@TODO
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

