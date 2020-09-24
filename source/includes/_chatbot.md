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
USER_ID | The user (host) ID registered on Carebnb
PROPERTY_ID | The property ID registered on Carebnb
RULE | A rule per se. A complete list of rules is retrieved by "Get all" in "House rules" sub-section
RULE_ANSWER | "no", "yes" or "maybe"





## Frequently answered questions

### Get all

> Response

```json
{
  "statusCode": 200,
  "message": "FAQs list",
  "data": [
    {
      "faqId": "7b02c6af-aff6-4f61-9508-b0259908d...",
      "question": "How can I...?",
      "answer": "Easy, you can just..."
    },
    ...
  ]
}
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
user-id     | **USER**
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
  "message": "FAQ created",
  "data": {
    "faqId": "7b02c6af-aff6-4f61-9508-b0259908d...",
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

**Request object parameters**

| param | type | description | required? |
| ------ | ------ | ------ | ------ |
| question | String(4000) | The most apropriated question title | yes
| answer | String(4000) | Resumed answer for the FAQ item | yes

**Request Headers**

Property    | Value
----------- | -------
api-key     | **API_KEY**
user-id     | **USER**
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
  "statusCode": 200,
  "message": "FAQ updated",
  "data": {
    "faqId": "7b02c6af-aff6-4f61-9508-b0259908d...",
    "question": "How can I...?",
    "answer": "Easy, you can just..."
  }
}
```

Updates a frequently asked question for a given property.

**Request**

Property | Value
-------- | -------
Endpoint | /faq/faqId/**FAQ_ID**
Method   | PUT

**Request object parameters**

| param | type | description | required? |
| ------ | ------ | ------ | ------ |
| question | String(4000) | The most apropriated question title | yes
| answer | String(4000) | Resumed answer for the FAQ item | yes

**Request Headers**

Property    | Value
----------- | -------
api-key     | **API_KEY**
user-id     | **USER**
property-id | **PROPERTY_ID**




### Delete

> Response

```json
{
  "statusCode": 200,
  "message": "FAQ deleted"
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
user-id     | **USER**
property-id | **PROPERTY_ID**





## House rules

### Get all

> Response

```json
{
  "statusCode": 200,
  "message": "Rules list",
  "data": [
    {
      "ruleId": "pets",
      "title": "Pets",
      "answer": "maybe",
      "questions": [
        "Are pets allowed?",
        ...
      ],
      "answers": {
        "positive": "Absolutelly, pets are welcome.",
        "negative": "Sorry, pets are not allowed.",
        "maybe": "Pets are welcome in certain cases."
      },
      "subRules": [
        {
          "ruleId": "serviceDogs",
          "title": "Service dogs",
          "answer": null,
          "questions": [
            "Can I take my assistance dog with me?",
            ...
          ],
          "positive": "Yes, we are okay with service / assitance dogs.",
          "negative": "Sorry, service / assistance dogs are not allowed.",
          "maybe": "Service / assitance dogs are welcome in certain cases."
        },
        ...
      ]
    },
    ...
  ]
}
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
user-id     | **USER**
property-id | **PROPERTY_ID**





### Update

> Request body

```json
{
  "statusCode": 200,
  "message": "Rule updated",
  "data": {
    "ruleId": "pets",
    "title": "Pets",
    "questions": [
      "Are pets allowed?",
      ...
    ],
    "answers": {
      "positive": "Absolutelly, pets are welcome.",
      "negative": "Sorry, pets are not allowed.",
      "maybe": "Pets are welcome in certain cases. {hostName} will touch base with you on this."
    },
    "answer": "maybe"
  }
}
```

> Response

```json
{
  "answer": "yes"
}	
```

Updates a house rule for a given property.

<aside class="notice">
  Sub rules are not returned by this update end point.
</aside>

**Request**

Property | Value
-------- | -------
Endpoint | /rule/ruleId/**RULE_ID**
Method   | PUT

**Request object parameters**

| param | type | description | required? |
| ------ | ------ | ------ | ------ |
| answer | String(5) | Resumed answer for the FAQ item | yes

**Request Headers**

Property    | Value
----------- | -------
api-key     | **API_KEY**
user-id     | **USER**
property-id | **PROPERTY_ID**





## Nearby places

### Get all

> Response

```json
{
  "statusCode": 200,
  "message": "Places list",
  "data": [
    {
      "place": "Pool",
      "distance": "Walking distance",
      "time": "2 minutes"
    },
    ...
  ]
}
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
user-id     | **USER**
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
  "statusCode": 201,
  "message": "Place created",
  "data": {
    "placeId": "e541ea21-60d5-43e0-b41d-9ad002255...",
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

**Request object parameters**

| param | type | description | required? |
| ------ | ------ | ------ | ------ |
| place | String(400) | The name of the place nearby property | yes
| distance | String(255) | How far for the place in miles, kilometers or even steps | yes
| time | String(255) | How long to reach the place in hours, minutes, etc | yes

Observation: The **distance** or **time** parameters must be in the request. But offcourse, booth parameters should be passed to.

**Request Headers**

Property    | Value
----------- | -------
api-key     | **API_KEY**
user-id     | **USER**
property-id | **PROPERTY_ID**



### Update

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
  "message": "Place updated",
  "data": {
    "placeId": "e541ea21-60d5-43e0-b41d-9ad002255...",
    "place": "Pool",
    "distance": "Walking distance",
    "time": "2 minutes"
  }
}
```

Updates a nearby place for a given property.

**Request**

Property | Value
-------- | -------
Endpoint | /place/placeId/**PLACE_ID**
Method   | PUT

**Request object parameters**

| param | type | description | required? |
| ------ | ------ | ------ | ------ |
| place | String(400) | The name of the place nearby property | yes
| distance | String(255) | How far for the place in miles, kilometers or even steps | yes
| time | String(255) | How long to reach the place in hours, minutes, etc | yes

Observation: The **distance** or **time** parameters must be in the request. But offcourse, booth parameters should be passed to.

**Request Headers**

Property    | Value
----------- | -------
api-key     | **API_KEY**
user-id     | **USER**
property-id | **PROPERTY_ID**



### Delete

> Response

```json
{
  "statusCode": 200,
  "message": "Place deleted"
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
user-id     | **USER**
property-id | **PROPERTY_ID**
