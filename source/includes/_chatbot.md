# Smart chatbot agent

Our artificially intelligent chatbot answers common questions, as well as learns as it goes.

Don't let your guests wait, be always polite and communicate with efficiency.
[know more](https://carebnb.app/services/smart-chatbot-agent/)

**Base URL**

<code>https://api.chatbot.carebnb.app/v1</code>

**Request / response properties**

Some properties expect a pre defined value.

Property | Description
-------- | -------
API_KEY | An exclusive API key generated for each partner
PROPERTY_ID | The property ID registered on Carebnb
RULE | A list of all rules is retrieved by "Get all" in "Rouse rules" section
RULE_ANSWER | "no", "yes" or "maybe"





## Frequently answered questions

### Get all

> Response

```json
[
  {
    "_id": "q1w2e3r4t5y6u7i8o9p0q1w2",
    "question": "How can I...?",
    "answer": "Easy, you can just..."
  }
]
```

Returns all frequently asked questions for a given property.

**Request**

Property | Value
-------- | -------
Endpoint | /faqs
Method   | GET

**Request Headers**

Property    | Value
----------- | -------
api-key     | **API_KEY**
property-id | **PROPERTY_ID**





### Create

> Request body

```json
{
  "question": "How can I...?",
  "answer": "Easy, you can just..."
}
```

> Response

```json
{
  "statusCode": 201,
  "data": {
    "_id": "q1w2e3r4t5y6u7i8o9p0q1w2",
    "question": "How can I...?",
    "answer": "Easy, you can just..."
  }
}
```

Adds a new frequently asked question for a given property.

**Request**

Property | Value
-------- | -------
Endpoint | /faq
Method   | POST

**Request Headers**

Property    | Value
----------- | -------
api-key     | **API_KEY**
property-id | **PROPERTY_ID**





### Update

> Request body

```json
{
  "question": "How can I...?",
  "answer": "Easy, you can just..."
}
```

> Response

```json
{
  "statusCode":200,
  "data":{
    "_id": "q1w2e3r4t5y6u7i8o9p0q1w2",
    "question": "How can I...?",
    "answer": "Easy, you can just...",
    "createdAt":"2020-01-01T00:00:00.000Z",
    "updatedAt":"2020-01-01T00:00:00.000Z"
  }
}
```

Updates a frequently asked question for a given property.

**Request**

Property | Value
-------- | -------
Endpoint | /faq/faqId/**FAQ_ID**
Method   | PUT

**Request Headers**

Property    | Value
----------- | -------
api-key     | **API_KEY**
property-id | **PROPERTY_ID**





### Delete

> Response

```json
{
  "statusCode": 200
}
```

Removes a frequently asked question for a given property.

**Request**

Property | Value
-------- | -------
Endpoint | /faq/faqId/**FAQ_ID**
Method   | DELETE

**Request Headers**

Property    | Value
----------- | -------
api-key     | **API_KEY**
property-id | **PROPERTY_ID**





## House rules

### Get all

> Response

```json
[
  {
    "_id": "q1w2e3r4t5y6u7i8o9p0q1w2",
    "rule": RULE,
    "answer": RULE_ANSWER
  }
]
```

Returns all house rules for a given property.

**Request**

Property | Value
-------- | -------
Endpoint | /rules
Method   | GET

**Request Headers**

Property    | Value
----------- | -------
api-key     | **API_KEY**
property-id | **PROPERTY_ID**





### Update

> Request body

```json
{
  "rule": RULE,
  "answer": RULE_ANSWER
}
```

> Response

```json
{
  "statusCode": 200
}
```

Updates a house rule for a given property.

**Request**

Property | Value
-------- | -------
Endpoint | /rule/ruleId/**RULE_ID**
Method   | PUT

**Request Headers**

Property    | Value
----------- | -------
api-key     | **API_KEY**
property-id | **PROPERTY_ID**





## Nearby places

### Get all

> Response

```json
[
  {
    "_id": "q1w2e3r4t5y6u7i8o9p0q1w2",
    "place": "Walmart",
    "distance": "5 miles",
    "time": "6 minutes"
  }
]
```

Returns all nearby places for a given property.

**Request**

Property | Value
-------- | -------
Endpoint | /places
Method   | GET

**Request Headers**

Property    | Value
----------- | -------
api-key     | **API_KEY**
property-id | **PROPERTY_ID**





### Create

> Request body

```json
{
  "place": "Pool",
  "distance": "Walking distance",
  "time": "2 minutes"
}
```

> Response

```json
{
  "statusCode": 200,
  "data": {
    "_id": "q1w2e3r4t5y6u7i9o9p0q9f4",
    "place": "Pool",
    "distance": "Walking distance",
    "time": "2 minutes"
  }
}
```

Adds a new nearby place for a given property.

**Request**

Property | Value
-------- | -------
Endpoint | /place
Method   | POST

**Request Headers**

Property    | Value
----------- | -------
api-key     | **API_KEY**
property-id | **PROPERTY_ID**





### Update

> Request body

```json
{
  "place": "Walmart",
  "distance": "5 miles",
  "time": "6 minutes"
}
```

> Response

```json
{
  "statusCode": 200
}
```

Updates a nearby palce for a given property.

**Request**

Property | Value
-------- | -------
Endpoint | /place/placeId/**PLACE_ID**
Method   | PUT

**Request Headers**

Property    | Value
----------- | -------
api-key     | **API_KEY**
property-id | **PROPERTY_ID**





### Delete

> Response

```json
{
  "statusCode": 200
}
```

Removes a nearby place for a given property.

**Request**

Property | Value
-------- | -------
Endpoint | /place/placeId/**PLACE_ID**
Method   | DELETE

**Request Headers**

Property    | Value
----------- | -------
api-key     | **API_KEY**
property-id | **PROPERTY_ID**
