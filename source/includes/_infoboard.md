# Smart info board

Carebnb displays personalized messages straight through our smart info board.

Keep your guests up to date, communicating rules and procedures in a timely manner. Up-to-date guests are more likely to follow rules. Rules being followed equals less turnover work. 
This e-ink display, with no backlight, will never disturb guests.

This part of the API is pretty much like our "**Automatic check in check out**" API.
The main difference is the limits of the messages.

**Base URL**

<code>https://api.infoboard.carebnb.app/v1</code>

**Request / response properties**

Some properties expect a pre defined value.

Property | Description
-------- | -------
API_KEY | An exclusive API key generated for each partner
USER_ID | The user ID registered on Carebnb. Normally is a host
PROPERTY_ID | The property ID registered on Carebnb
EVENT_TYPE | "introduction", "scheduled", "checkin" or "checkout"
REMINDER_PERIOD | ... "-P2D", "-P1D", "P0D", "P1D", "P2D" ...
MESSAGE_ID | The message ID registered on Carebnb

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
  "statusCode":200,
  "data":{
    "messageId":"e7ac8705-a7c1-4f2c-8e32-036daaa30...",
    "message":"Hi {guestName},\n\nThanks for choosing us.\n\nI'm Carebnb...",
    "event":"introduction"
  }
}
```

Returns the introduction message for a given property.
This is the message sent to guests at the moment a new reservation is detected

**Request**

Property | Value
-------- | -------
Endpoint | /messages/event/introduction
Method   | GET

**Request Headers**

Property    | Value
----------- | -------
api-key | **API_KEY**
user-id | **USER_ID**
property-id | **PROPERTY_ID**





### Update

> Request body

```json
{
  "message":"Hi {guestName},\n\nI'm Carebnb, your automatic hosting.\n\nLet us know if there is anything else I can help you with.",
  "event":"introduction"
}
```

> Response

```json
{
  "statusCode":200,
  "data":{
    "messageId":"e7ac8705-a7c1-4f2c-8e32-036daaa30...",
    "message":"Updated message. Hi {guestName},\n\nThanks for choosing us.\n\nI'm Carebnb...",
    "event":"introduction"
  }
}
```

Updates the introduction message for a given property.
This is the message sent to guests at the moment a new reservation is detected

**Request**

Property | Value
-------- | -------
Endpoint | /message/messageId/**MESSAGE_ID**
Method   | PUT

**Request Headers**

Property    | Value
----------- | -------
api-key | **API_KEY**
user-id | **USER_ID**
property-id | **PROPERTY_ID**

This type of message can't be deleted.





## Scheduled messages

### Get all

> Response

```json
{
  "statusCode":200,
  "data":[
    {
      "messageId":"e7ac8705-a7c1-4f2c-8e32-036daaa30...",
      "message":"It's trash day.\n\nHi  {guestName}, please ...",
      "event":"scheduled",
      "reminderSchedule":[
        {
          "dayOfWeek":"monday",
          "hours":[
            "20:00"
          ]
        }
      ]
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
Endpoint | /messages/event/scheduled
Method   | GET

**Request Headers**

Property    | Value
----------- | -------
api-key | **API_KEY**
user-id | **USER_ID**
property-id | **PROPERTY_ID**





### Create

> Request body

```json
{
  "event":"scheduled",
  "message":"New message for {guestName}.\n\n\natt,\n {hostName} ...",
  "reminderSchedule":[
    {
      "dayOfWeek":"monday",
      "hours":[
        "20:00"
      ]
    }
  ]
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
Endpoint | /message
Method   | POST

**Request Headers**

Property    | Value
----------- | -------
api-key | **API_KEY**
user-id | **USER_ID**
property-id | **PROPERTY_ID**





### Update

> Request body

```json
{
  "message":"Updated message for {guestName}.\n\n\natt,\n {hostName} ...",
  "event":"scheduled",
  "reminderSchedule":[
    {
      "dayOfWeek":"friday",
      "hours":[
        "10:00"
      ]
    }
  ]
}
```

> Response

```json
{
  "statusCode":200,
  "data":{
    "messageId":"e7ac8705-a7c1-4f2c-8e32-036daaa30...",
    "message":"Updated message for {guestName}.\n\n\natt,\n {hostName} ...",
    "event":"scheduled",
      "reminderSchedule":[
      {
        "dayOfWeek":"monday",
        "hours":[
          "10:00"
        ]
      }
    ]
  }
}
```

Updates a scheduled message.
This type of message is sent to guests based on the day of the week.

**Request**

Property | Value
-------- | -------
Endpoint | /message/messageId/**MESSAGE_ID**
Method   | PUT

**Request Headers**

Property    | Value
----------- | -------
api-key | **API_KEY**
user-id | **USER_ID**
property-id | **PROPERTY_ID**





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
Endpoint | /message/messageId/**MESSAGE_ID**
Method   | DELETE

**Request Headers**

Property    | Value
----------- | -------
api-key | **API_KEY**
user-id | **USER_ID**
property-id | **PROPERTY_ID**





## Check in check out messages

### Get all

> Response

```json
{
  "statusCode":200,
  "data":[
    {
      "messageId":"e7ac8705-a7c1-4f2c-8e32-036daaa30...",
      "message":"It's trash day.\n\nHi  {guestName}, please ...",
      "event":"introduction",
      "reminderPeriod":"P1D"
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
Endpoint | /messages/event/checkin-checkout
Method   | GET

**Request Headers**

Property    | Value
----------- | -------
api-key | **API_KEY**
user-id | **USER_ID**
property-id | **PROPERTY_ID**





### Create

> Request body

```json
{
  "message":"New message for {guestName}.\n\n\natt,\n {hostName} ...",
  "event":EVENT_TYPE,
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
Endpoint | /message
Method   | POST

**Request Headers**

Property    | Value
----------- | -------
api-key | **API_KEY**
user-id | **USER_ID**
property-id | **PROPERTY_ID**





### Update

> Request body

```json
{
  "event":EVENT_TYPE,
  "message":"Hi {guestName},\n\nIt's Carebnb again.\nTomorrow is the big day!\n\nPrior to your arrival, our place was cleaned, sanitized and inspected. All seems to work fine, but let me know if you encounter any issue.\n\n{hostName} and I are looking forward to hosting you.",
  "reminderPeriod":"P1D"
}
```

> Response

```json
{
  "statusCode":200,
  "data":{
    "messageId":"e7ac8705-a7c1-4f2c-8e32-036daaa30...",
    "message":"Updated message for {guestName}.\n\n\natt,\n {hostName} ...",
    "event":"introduction",
    "reminderPeriod":"-P1D"
  }
}
```

Updates a check in check out based message.
This type of message is sent to guests based on check in check out date.

**Request**

Property | Value
-------- | -------
Endpoint | /message/messageId/**MESSAGE_ID**
Method   | PUT

**Request Headers**

Property    | Value
----------- | -------
api-key | **API_KEY**
user-id | **USER_ID**
property-id | **PROPERTY_ID**





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
Endpoint | /message/messageId/**MESSAGE_ID**
Method   | DELETE

**Request Headers**

Property    | Value
----------- | -------
api-key | **API_KEY**
user-id | **USER_ID**
property-id | **PROPERTY_ID**