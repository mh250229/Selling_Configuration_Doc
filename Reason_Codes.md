# Reason Codes

Reason codes indicate the reason an activity is performed. For example, when the cashier performs a Price Override, the system prompts the cashier to enter the reason the item price was overridden.

**HTTP Methods:**

* PUT Reason Code Group
* PUT Reason Code
* GET Reason Code Group
* GET Reason Code
* DELETE Reason Codes

The following examples show a request to add a Reason Code Groups to contain the reason codes when an item price is overridden.

## Add Reason Code Groups

PUT

/emerald/selling-service/c1/selling-configuration/reason-code-settings/reason-code-groups/{reasonCodeGroupId}

Request

```json
{
    "descriptions": [
        {
            "culture": "en-US",
            "value": "PriceOverrideReasons"
        }
    ]
}
```

Response 200 OK

## Get Reason Code Groups

GET

/emerald/selling-service/c1/selling-configuration/reason-code-settings/reason-code-groups

Response

```json
{
    "lastPage": true,
    "pageNumber": 0,
    "totalPages": 1,
    "totalResults": 1,
    "pageContent": [
        {
            "ReasonCodeGroupId": "{reasonCodeGroupId}",
            "descriptions": [
                {
                    "culture": "en-US",
                    "value": "PriceOverrideReasons"
                }
            ]
        }
    ]
}
```

## Add Reason Codes to a Reason Code group

PUT

/emerald/selling-service/c1/selling-configuration/reason-code-settings/reason-codes/{reasonCodeId}

Request

```json
{
    "descriptions": [
        {
            "culture": "en-US",
            "value": "Damaged"
        }
    ],
    "reasonCodeGroupId": "PriceOverrideReasons"
}
```

Response 200 OK

## Retrieve Reason Codes

GET

/emerald/selling-service/c1/selling-configuration/reason-code-settings/reason-codes

Response

```json
{
    "ReasonCodeId": "{reasonCodeId}",
    "descriptions": [
        {
            "culture": "en-US",
            "value": "Damaged"
        }
    ],
    "reasonCodeGroupId": "PriceOverrideReasons"
}
```
