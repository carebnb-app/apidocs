# Automatic check in check out

Carebnb communicates with guests straight through Airbnb app!

Send automatic messages based on the day of check-ins and checkouts.

Keep your guests up to date, communicating rules and procedures in a timely manner. Up-to-date guests are more likely to follow rules. Rules being followed equals less turnover work. [know more](https://carebnb.app/services/automatic-check-in-check-out/)

**Base URL**

<code>https://api.messages.carebnb.app/api/v1</code>

**Request / response properties**

Some properties expect a pre defined value.

Property | Description
-------- | -------
EVENT_TYPE | "introduction", "scheduled", "checkin" or "checkout"
REMINDER_PERIOD | ... "-P2D", "-P1D", "P0D", "P1D", "P2D" ...
PROPERTY_ID | Carebnb property ID
MESSAGE_ID | Carebnb message ID

**Placeholders**

This service allows placeholders.
Values on the left column are replaced by values on the second one in any message sent by Carebnb.

Placeholder | Description
----------- | -------
{guestName} | Guest's first name
{hostName} | Host's full name





## Introduction message

### Get

> Response

```json
{
  "statusCode":201,
  "data":{
    "_id":"q1w2e3r4t5y6u7i8o9p0q1w2",
    "message":"Hi {guestName},\n\nThanks for choosing us.\n\nI'm Carebnb...",
    "event":"introduction",
    "reminderPeriod":null,
    "reminderSchedule":null,
    "createdAt":"2020-01-01T00:00:00.000Z",
    "updatedAt":"2020-01-01T00:00:00.000Z",
    "deletedAt":null
  }
}
```

Returns the introduction message for a given property.
This is the message sent to guests at the moment a new reservation is detected

**Request**

Property | Value
-------- | -------
Endpoint | /messages/carebnbPropertyId/**PROPERTY_ID**/event/introduction
Method   | GET





### Update

> Request body

```json
{
   "message":"Updated message. Hi {guestName},\n\nThanks for choosing us.\n\nI'm Carebnb...",
   "carebnbPropertyId":"76e122d8-3bb7-4e0e-843c-e26fc0931534",
   "event":"introduction"
}
```

> Response

```json
{
  "statusCode":201,
  "data":{
    "_id":"q1w2e3r4t5y6u7i8o9p0q1w2",
    "message":"Updated message. Hi {guestName},\n\nThanks for choosing us.\n\nI'm Carebnb...",
    "event":"introduction",
    "reminderPeriod":null,
    "reminderSchedule":null,
    "createdAt":"2020-01-01T00:00:00.000Z",
    "updatedAt":"2020-01-01T00:00:00.000Z",
    "deletedAt":null
  }
}
```

Updates the introduction message for a given property.
This is the message sent to guests at the moment a new reservation is detected

**Request**

Property | Value
-------- | -------
Endpoint | /messages/**MESSAGE_ID**
Method   | PUT

This message can't be deleted.





## Scheduled messages

### Get

> Response

```json
{
  "statusCode":201,
  "data":[
    {
      "_id":"q1w2e3r4t5y6u7i8o9p0q1w2",
      "message":"It's trash day.\n\nHi  {guestName}, please ...",
      "event":"scheduled",
      "reminderPeriod":null,
      "reminderSchedule":[
        {
            "dayOfWeek":"monday",
            "hours":[
              "20:00"
            ]
        },
        {
            "dayOfWeek":"wednesday",
            "hours":[
              "20:00"
            ]
        }
      ],
      "createdAt":"2020-01-01T00:00:00.000Z",
      "updatedAt":"2020-01-01T00:00:00.000Z",
      "deletedAt":null
    },
    ...
  ]
}
```

Returns all scheduled messages for a given property.
The returned messages are the ones sent to guests based on the day of the week.

**Request**

Property | Value
-------- | -------
Endpoint | /messages/carebnbPropertyId/**PROPERTY_ID**/event/scheduled
Method   | GET





### Update

> Request body

```json
{
  "message":"Updated message for {guestName}.\n\n\natt,\n {hostName} ...",
  "event":"scheduled",
  "carebnbPropertyId":PROPERTY_ID
}
```

> Response

```json
{
  "statusCode":201,
  "data":{
    "_id":"q1w2e3r4t5y6u7i8o9p0q1w2",
    "message":"Updated message for {guestName}.\n\n\natt,\n {hostName} ...",
    "event": "scheduled",
    "reminderPeriod":null,
    "reminderSchedule":[
      {
          "dayOfWeek":"monday",
          "hours":[
            "20:00"
          ]
      },
      {
          "dayOfWeek":"wednesday",
          "hours":[
            "20:00"
          ]
      }
    ],
    "createdAt":"2020-01-01T00:00:00.000Z",
    "updatedAt":"2020-01-01T00:00:00.000Z",
    "deletedAt":null
  }
}
```

Updates a scheduled message.
This type of message is sent to guests based on the day of the week.

**Request**

Property | Value
-------- | -------
Endpoint | /messages/**MESSAGE_ID**
Method   | PUT





### Create

> Request body

```json
{
  "message":"New message for {guestName}.\n\n\natt,\n {hostName} ...",
  "reminderSchedule":[
    {
        "dayOfWeek":"monday",
        "hours":[
          "20:00"
        ]
    },
    {
        "dayOfWeek":"wednesday",
        "hours":[
          "20:00"
        ]
    }
  ],
  "event":"scheduled",
  "carebnbPropertyId":PROPERTY_ID
}
```

> Response

```json
{
  "statusCode":201
}
```

Adds a new scheduled message.
This type of message is sent to guests based on the day of the week.

**Request**

Property | Value
-------- | -------
Endpoint | /messages
Method   | POST





### Delete

> Response

```json
{
  "statusCode":200
}
```

Removes a scheduled message.
This type of message is sent to guests based on the day of the week.

**Request**

Property | Value
-------- | -------
Endpoint | /messages/**MESSAGE_ID**
Method   | DELETE





## Check in check out messages

### Get

> Response

```json
{
  "statusCode":201,
  "data":[
    {
      "_id":"q1w2e3r4t5y6u7i8o9p0q1w2",
      "message":"It's trash day.\n\nHi  {guestName}, please ...",
      "event":"checkin-checkout",
      "reminderPeriod":"-P1D",
      "reminderSchedule":null,
      "createdAt":"2020-01-01T00:00:00.000Z",
      "updatedAt":"2020-01-01T00:00:00.000Z",
      "deletedAt":null
    },
    ...
  ]
}
```

Returns all check in check out messages for a given property.
The returned messages are the ones sent to guests based on check in check out dates.

**Request**

Property | Value
-------- | -------
Endpoint | /messages/carebnbPropertyId/**PROPERTY_ID**/event/checkin-checkout
Method   | GET





### Update

> Request body

```json
{
  "message":"Updated message for {guestName}.\n\n\natt,\n {hostName} ...",
  "event":EVENT_TYPE,
  "carebnbPropertyId":PROPERTY_ID,
  "reminderPeriod":REMINDER_PERIOD
}
```

> Response

```json
{
  "statusCode":201,
  "data":{
    "_id":"q1w2e3r4t5y6u7i8o9p0q1w2",
    "message":"Updated message for {guestName}.\n\n\natt,\n {hostName} ...",
    "event":"checkin",
    "reminderPeriod":"-P1D",
    "reminderSchedule":null,
    "createdAt":"2020-01-01T00:00:00.000Z",
    "updatedAt":"2020-01-01T00:00:00.000Z",
    "deletedAt":null
  }
}
```

Updates a check in check out based message.
This type of message is sent to guests based on check in check out date.

**Request**

Property | Value
-------- | -------
Endpoint | /messages/**MESSAGE_ID**
Method   | PUT





### Create

> Request body

```json
{
  "message":"New message for {guestName}.\n\n\natt,\n {hostName} ...",
  "event":EVENT_TYPE,
  "carebnbPropertyId":PROPERTY_ID,
  "reminderPeriod":REMINDER_PERIOD
}
```

> Response

```json
{
  "statusCode":201
}
```

Adds a new check in check out message.
This type of message is sent to guests based on check in check out date.

**Request**

Property | Value
-------- | -------
Endpoint | /messages
Method   | POST





### Delete

> Response

```json
{
  "statusCode":200
}
```

Removes a check in check out message.
This type of message is sent to guests based on check in check out date.

**Request**

Property | Value
-------- | -------
Endpoint | /messages/**MESSAGE_ID**
Method   | DELETE