# BRM Total Transaction

The Cart API supports the Total Transaction BRM.

The BRM is set up as follows:

* Rule Id - Total Transaction
* Rule Type -TransactionTotal
* Applied on - Transaction
* Action Type

If the restriction is not solved when the Cart is moved to Finalize Status, an exception is returned.

**HTTP Methods:**

* PUT
* GET
* DELETE

## Add a Total Transaction Business Rule

Used to add a Total Transaction business rule.

PUT

/emerald/selling-service/c1/selling-configuration/business-rules-settings/total-transactions/{ruleId}

```json

Request
{
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
             "maxAmount": 500,
             "maxQuantity": 0,
             "containsLoyalty": false
        }
    },
    "tag": "selling"
}


Response 200 OK
{
   OK
}
```

## Get Total Transaction Business Rules

Used to retrieve Total Transaction business rule details.

GET

/emerald/selling-service/c1/selling-configuration/business-rules-settings/total-transactions/{ruleId}

```json
Response 200 OK
{
    "ruleType": "TotalTransactionRestrictionData",
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
        "customerOrderCondition": {
            "maxAmount": 500,
            "maxQuantity": 0,
            "containsLoyalty": false
        }
    },
    "tag": "selling"
}

