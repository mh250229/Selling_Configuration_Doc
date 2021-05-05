# BRM Price Override

The Cart API supports the Price Override BRM.

The BRM is triggered when the product price is overridden, and the new price exceeds the maximum percentage allowed to override an item price.

The BRM is set up as follows:

* Rule Id
* Rule Type – PriceOverride
* Applied on -Item
* Max Discount (percent)
* Action Type

The Price Override BRM supports the following Action Types:

* Prohibit
* Approval required
* Select reason
* Prompt for confirmation
* Input data required
* Notification

**HTTP Methods:**

* PUT
* GET
* DELETE

## Add a Price Override Business Rule

Used to add a Price Override business rule.

PUT
/emerald/selling-service/c1/selling-configuration/business-rules-settings/price-overrides/{ruleId}

```json

Request
{
"maxAllowedPercentChange": 10,
    "conditions": {
        "locationCondition": {
            "includedLocations": [{
                    "enterpriseUnitId": "{{nep-enterprise-unit}}"
                }
            ]
        },
        "productCondition": {
            "includedProducts": [{
                    "value": "Lettuce"
                }
            ]
        },
        "customerOrderCondition": {
            "{{customerOrderConditionKey}}": "{{customerOrderConditionValue}}"
        }
    },
    "tag": "selling"
}


Response 200 OK
{
   OK
}
```

## Get Price Override Business Rules

Used to retrieve Price Override business rule details.

GET

/emerald/selling-service/c1/selling-configuration/business-rules-settings/price-overrides

```json
Response 200 OK
{
    "lastPage": true,
    "pageNumber": 0,
    "totalPages": 1,
    "totalResults": 1,
    "pageContent": [
        {
            "maxAllowedPercentChange": 10,
            "ruleType": "PriceOverrideRestrictionData",
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
                            "value": "Lettuce"
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
