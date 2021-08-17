
# Messages

Messages are configured for Business Rules and Age Restrictions.
A message is an auxiliary resource used for offload handling of multi-language message text from other configurations.
In case a configuration needs to return a human readable text to the client, then instead of returning the full text, it can return a reference to a Message.
Messages are composed of a Title and Body and may contain predefined embedded parameterized values.


**HTTP Methods:**

- PUT Message_PUT
- DELETE Message_DELETE
- GET Message_GET

## Add Message

Used to add a message in the system.

PUT

/emerald/selling-service/c1/selling-configuration/message-settings/messages/{messageId}

The following example shows a request to add a message for a Business Rule.

The context type is BRM. The request includes the default culture, message header and body.

```json
Request
{
    "contextType": "BRM",
    "description": "null",
    "name": "AlcoholSaleRestrictedMessage",
    "parts": [
        {
            "type": "Header",
            "culture": "{{culture_str}}",
            "text": "Alcohol Sale Restricted"
        },
        {
            "type": "Body",
            "culture": "{{culture_str}}",
            "text": "Manager Approval Required at this Time"
        }
    ]
}
```

```json
Response Status OK
{
   OK
}
```

## Get Messages

Used to retrieve the messages in the system.

GET

/emerald/selling-service/c1/selling-configuration/message-settings/messages

The following example shows a response when a request is sent to retrieve the messages defined in the system.

```json
Response
{
    "lastPage": true,
    "pageNumber": 0,
    "totalPages": 1,
    "totalResults": 1,
    "pageContent": [
        {
            "messageId": "{messageId}",
            "contextType": "BRM",
            "description": "{{messageId_str}}",
            "name": "{messageId}",
            "parts": [
                {
                    "type": "Header",
                    "culture": "{{culture_str}}",
                    "text": "Void Item"
                },
                {
                    "type": "Body",
                    "culture": "{{culture_str}}",
                    "text": "Please Select Void Reason"
                }
            ]
        }
    ]
}
```
