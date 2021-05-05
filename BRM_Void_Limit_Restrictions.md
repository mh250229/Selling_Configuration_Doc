# BRM Void Limit Restrictions

The Cart API supports the Void Item BRM.
The BRM evaluates the items voided in a cart.
A 'Void item' restriction is created once one of the following criteria are met:

* Voided line amount > Max allowed amount per line
* Voided ticket amount >Max allowed amount per ticket

Both criteria can be configured together.
The maximum allowed limit can be any positive value including 0.
A Void item BRM includes:

* Rule Id
* Rule type- "VoidLimitBehavior"
* Applied on :Voideditem
* Max allowed amount per line
* Max allowed amount per ticket
* Action type:

  * Restricted audit line id
  * Original line id

If the client uses the 'Enforce' flag (instead of inform), the item is not removed from the cart until the restriction is resolved.
If the ‘Enforce’ flag is not used, the item is removed and captured in the audit line and the restriction is created.
The following Action type options are supported by the Void Item BRM:

* Prohibit
* Approval required
* Select reason
* Prompt for confirmation
* Input data required
* Notification

**HTTP Methods:**

* PUT VoidLimitRules_PUT
* GET VoidLimitRules_GET

## Add Void Item Business Rule

Used to add a void item business rule.

PUT

/emerald/selling-service/c1/selling-configuration/business-rules-settings/void-limits/{ruleId}

```json
Request
{
"maxAllowedAmountperLine": 50.0,
    "conditions": {
        "locationCondition": {
            "includedLocations": [{
                    "enterpriseUnitId": "{{nep-enterprise-unit}}"
                }
            ]
        },
        "productCondition": {
            "includedProducts": [{
                    "value": "{{includedItemId}}"
                }
            ]
        },
        "customerOrderCondition": {
            "{{customerOrderConditionKey}}": "{{customerOrderConditionValue}}"
        }
    },
    "tag": "{{contextType}}"
}


Response 200 OK
{
   OK
}
```

## Get Void Item Business Rules

Used to retrieve a void item business rule details.

GET

/emerald/selling-service/c1/selling-configuration/business-rules-settings/void-limits/{ruleId}

```json
Response 200 OK
{
    "lastPage": true,
    "pageNumber": 0,
    "totalPages": 1,
    "totalResults": 1,
    "pageContent": [
        {
            "ruleType": "VoidLimitRestrictionData",
            "ruleId": "{ruleId}",
            "actionType": null,
            "conditions": {
                "locationCondition": {
                    "includedLocations": [
                        {
                            "enterpriseUnitId": "00000000000000000000000000035295"
                        }
                    ]
                },
                "productCondition": {
                    "includedProducts": [
                        {
                            "value": "{{includedItemId}}"
                        }
                    ]
                },
                "customerOrderCondition": {}
            },
            "tag": "selling"
        }
    ]
}
```
