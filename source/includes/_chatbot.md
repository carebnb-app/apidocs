# Carebnb Chatbot

Carebnb Chatbot!

<!-- Send automatic messages based on the day of check-ins and checkouts. -->

<!-- Keep your guests up to date, communicating rules and procedures in a timely manner. Up-to-date guests are more likely to follow rules. Rules being followed equals less turnover work. [know more](https://carebnb.app/services/automatic-check-in-check-out/) -->

**Base URL**

<code>https://api.chatbot.carebnb.app/api/v1</code>

**Request / response properties**

Some properties expect a pre defined value.

| Property    | Description         |
| ----------- | ------------------- |
| PROPERTY_ID | Carebnb property ID |

**Modules**

This service has the following modules

| Module | Description            |
| ------ | ---------------------- |
| Faqs   | Description for faqs   |
| Rules  | Description for rules  |
| Places | Description for places |

## Faqs

### Get faqs

> Response

```json
[
  {
    "_id": "q1w2e3r4t5y6u7i8o9p0q1w2",
    "question": "How can I...",
    "answer": "Easy, you can...",
    "createdAt": "2020-01-01T00:00:00.000Z",
    "updatedAt": "2020-01-01T00:00:00.000Z",
    "deletedAt": null
  },
  ...
]
```

Returns all faqs for a given property.

**Request**

| Property | Value                                            |
| -------- | ------------------------------------------------ |
| Endpoint | /chatbot/faqs/carebnbPropertyId/**PROPERTY_ID**/ |
| Method   | GET                                              |

### Create faqs

> Request body

```json
{
  "question": "How can I...",
  "anwser": "Easy, you can...",
  "carebnbPropertyId": "76e122d8-3bb7-4e0e-843c-e26fc0931534"
}
```

> Response

```json
{
  "statusCode": 201,
  "data": {
    "_id": "q1w2e3r4t5y6u7i8o9p0q1w2",
    "question": "How can I...",
    "answer": "Easy, you can...",
    "createdAt": "2020-01-01T00:00:00.000Z"
  }
}
```

Adds a new faq for a given property.

**Request**

| Property | Value         |
| -------- | ------------- |
| Endpoint | /chatbot/faqs |
| Method   | POST          |

### Update faqs

> Request body

```json
{
  "question": "How can I...",
  "anwser": "Easy, you can...",
  "carebnbPropertyId": "76e122d8-3bb7-4e0e-843c-e26fc0931534"
}
```

> Response

```json
{
  "statusCode": 200
}
```

Updates a specific faq

**Request**

| Property | Value                    |
| -------- | ------------------------ |
| Endpoint | /chatbot/faqs/**FAQ_ID** |
| Method   | PUT                      |

### Delete faqs

> Response

```json
{
  "statusCode": 200
}
```

Removes a specific faq

**Request**

| Property | Value                   |
| -------- | ----------------------- |
| Endpoint | /chatbot/faq/**FAQ_ID** |
| Method   | DELETE                  |

## Rules

### Get rules

> Response

```json
[
  {
    "_id": "q1w2e3r4t5y6u7i8o9p0q1w2",
    "rule": "Pets",
    "answer": "Yes",
    "createdAt": "2020-01-01T00:00:00.000Z",
    "updatedAt": "2020-01-01T00:00:00.000Z",
    "deletedAt": null
  },
  {
    "_id": "q1w2e3r4t5y8d7i8o9p0q5s1",
    "rule": "Smoke",
    "answer": "No",
    "createdAt": "2020-01-01T00:00:00.000Z",
    "updatedAt": "2020-01-01T00:00:00.000Z",
    "deletedAt": null
  },
  ...
]
```

Returns all rules for a given property.

The answer for Rules can be Yes, Maybe or No

**Request**

| Property | Value                                             |
| -------- | ------------------------------------------------- |
| Endpoint | /chatbot/rules/carebnbPropertyId/**PROPERTY_ID**/ |
| Method   | GET                                               |

### Update rules

> Request body

```json
{
  "rule": "Pet",
  "anwser": "Maybe",
  "carebnbPropertyId": "76e122d8-3bb7-4e0e-843c-e26fc0931534"
}
```

> Response

```json
{
  "statusCode": 200
}
```

Update a specific of rule

The answer for Rules can be Yes, Maybe or No

**Request**

| Property | Value                      |
| -------- | -------------------------- |
| Endpoint | /chatbot/rules/**RULE_ID** |
| Method   | PUT                        |

## Places

### Get places

> Response

```json
[
  {
    "_id": "q1w2e3r4t5y6u7i8o9p0q1w2",
    "place": "Walmart",
    "distance": "5 miles",
    "time": "6 minutes",
    "createdAt": "2020-01-01T00:00:00.000Z",
    "updatedAt": "2020-01-01T00:00:00.000Z",
    "deletedAt": null
  },
  {
    "_id": "q1w2e3r4t5y6u7i9o9p0q9f4",
    "place": "Pool",
    "distance": "Walking distance",
    "time": "",
    "createdAt": "2020-01-01T00:00:00.000Z",
    "updatedAt": "2020-01-01T00:00:00.000Z",
    "deletedAt": null
  },
  ...
]
```

Returns all places for a given property.

**Request**

| Property | Value                                              |
| -------- | -------------------------------------------------- |
| Endpoint | /chatbot/places/carebnbPropertyId/**PROPERTY_ID**/ |
| Method   | GET                                                |

### Create places

> Request body

```json
{
  "place": "Pool",
  "distance": "Walking distance",
  "time": "",
  "carebnbPropertyId": "76e122d8-3bb7-4e0e-843c-e26fc0931534"
}
```

> Response

```json
{
  "statusCode": 201,
  "data": {
    "_id": "q1w2e3r4t5y6u7i9o9p0q9f4",
    "place": "Pool",
    "distance": "Walking distance",
    "time": "",
    "createdAt": "2020-01-01T00:00:00.000Z"
  }
}
```

Adds a new place for a given property.

Distance or time is required

**Request**

| Property | Value           |
| -------- | --------------- |
| Endpoint | /chatbot/places |
| Method   | POST            |

### Update places

> Request body

```json
{
  "place": "Walmart",
  "distance": "5 miles",
  "time": "6 minutes",
  "carebnbPropertyId": "76e122d8-3bb7-4e0e-843c-e26fc0931534"
}
```

> Response

```json
{
  "statusCode": 200
}
```

Update a specific of place

**Request**

| Property | Value                        |
| -------- | ---------------------------- |
| Endpoint | /chatbot/places/**PLACE_ID** |
| Method   | PUT                          |

### Delete places

> Response

```json
{
  "statusCode": 200
}
```

Remove a specific place

**Request**

| Property | Value                        |
| -------- | ---------------------------- |
| Endpoint | /chatbot/places/**PLACE_ID** |
| Method   | DELETE                       |
