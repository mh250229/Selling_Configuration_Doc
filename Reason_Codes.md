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

Used to add Reason Code groups.

PUT

/emerald/selling-service/c1/selling-configuration/reason-code-settings/reason-code-groups/{reasonCodeGroupId}

```json
Request
{
    "descriptions": [
        {
            "culture": "en-US",
            "value": "PriceOverrideReasons"
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

## Get Reason Code Groups

Used to get Reason Code groups.

GET

/emerald/selling-service/c1/selling-configuration/reason-code-settings/reason-code-groups

```json
Response Status OK
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

## Add Reason Codes

Used to add Reason Codes to a Reason Code Group.

PUT

/emerald/selling-service/c1/selling-configuration/reason-code-settings/reason-codes/{reasonCodeId}

```json
Request
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

```json
Response Status OK
{
   OK
}
```

## Get Reason Codes

Used to retrieve Reason Codes.

GET

/emerald/selling-service/c1/selling-configuration/reason-code-settings/reason-codes

```json
Response Status OK
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
