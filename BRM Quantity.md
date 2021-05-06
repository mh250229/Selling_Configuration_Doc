# BRM Quantity

The Cart API supports the Quantity restriction.

The rule evaluates the total quantity/weight/amount of an item scanned in a transaction in order to control the maximum or minimum quantity, weight, or amount allowed for an item.

The BRM supports the following configuration:

* Location Conditions
  * Include business unit
  * Exclude business unit
* Touchpoints Groups Condition
  * Included Touchpoint Group, for example, main lane, self-scanner etc.
* Product Condition
  * Apply on (item and department sale or only item sale or only department sale
  * Apply on (sale  item only) ,return will be handled in future Us)
  * Products/category
  * Items group
  * Department
* Customer Order Condition
  * Max Transaction Amount
  * Max Transaction Quantity
* Reason Condition
* Action Type
  * Prohibit
  * Approval required
  * Select reason
  * Enter loyalty card
  * Prompt for confirmation
  * Input data required
  * Notification
* Action Message:
  * Requires attendant
* Quantitative Limit is aggregated on:
  * Max Quantity
  * Min Quantity
  * Max Weight
  * Min Weight
  * Max Amount
  
The Quantitative Limit BRM is setup as follows:

* Rule Id
* Rule type - "Quantity"
* Applied on :item/cart
* Action type
* Message header
* Message body
* Restricted lines

When the restriction is applied, "Ready to tender" = False for every item line that has met the restriction conditions.
When restriction is not applied - "Ready to tender" = True for every item line that has NOT met the restriction conditions

**HTTP Methods:**

* PUT
* GET
* DELETE

## Add a Quantity Business Rule

Used to add a Quantity business rule.

PUT

/emerald/selling-service/c1/selling-configuration/business-rules-settings/quantities/{ruleId}

```json

Request
{
  "conditions": {
    "locationCondition": {
      "includedLocations": [
        {
          "enterpriseUnitId": "{{nep-enterprise-unit}}"
        }
      ],
      "excludedLocations": [
        {
          "enterpriseUnitId": "{{nep-enterprise-unit}}"
        }
      ]
    },
    "retailSegmentCondition": {
      "includedRetailSegmentsId": [
        "string"
      ],
      "excludedRetailSegmentsId": [
        "string"
      ]
    },
    "productCondition": {
      "transactionType ": "SaleOnly",
      "includedProducts": [
        {
          "type": "string",
          "value": "4210000526"
        }
      ],
      "excludedProducts": [
        {
          "type": "string",
          "value": "string"
        }
      ],
      "includedGroups": [
        "string"
      ],
      "excludedGroups": [
        "string"
      ],
      "includedDepartments": [
        "string"
      ],
      "excludedDepartments": [
        "string"
      ],
      "includedCategories": [
        "string"
      ],
      "excludedCategories": [
        "string"
      ]
    },
    "customerOrderCondition": {
      "maxAmount": 0,
      "maxQuantity": 0,
      "containsLoyalty": true
    },
    "lineCondition": {
      "isReturnLine": true,
      "isDepartmentSaleLine": true,
      "minLineAmount": 2,
      "maxLineAmount": 5
    },
    "expressionCondition": {
      "expression": "string"
    },
    "accountProfileCondition": {
      "targetAccountProfileId": "string"
    },
    "paymentCondition": {
      "entryMethod": "string",
      "tenderTypeIds": [
        "string"
      ]
    },
    "couponRuleCondition": {
      "seriesIds": [
        "string"
      ],
      "couponTypes": [
        "string"
      ]
    }
  },
  "tag": "{{contextType}}"
}

Response 200 OK
{
   OK
}
```

## Get Quantity Business Rules

Used to retrieve Quantity business rule details.

GET

/emerald/selling-service/c1/selling-configuration/business-rules-settings/quantities

```json
Response 200 OK
{
    "lastPage": true,
    "pageNumber": 0,
    "totalPages": 1,
    "totalResults": 2,
    "pageContent": [
        {
            "maxAmount": 50,
            "ruleType": "QuantityRestrictionData",
            "ruleId": "DepartmentSale_SupervisorApproval",
            "actionType": "ApprovalAction",
            "conditions": {
                "locationCondition": {},
                "retailSegmentCondition": {
                    "includedRetailSegmentsId": [
                        "1",
                        "3",
                        "4",
                        "7"
                    ],
                    "excludedRetailSegmentsId": []
                },
                "productCondition": {
                    "includedProducts": [],
                    "includedGroups": [],
                    "includedDepartments": [],
                    "includedCategories": []
                },
                "customerOrderCondition": {},
                "lineCondition": {
                    "isDepartmentSaleLine": true
                },
                "expressionCondition": {},
                "accountProfileCondition": {},
                "paymentCondition": {},
                "couponRuleCondition": {}
            },
            "tag": "Selling"
        },
        {
            "ruleType": "QuantityRestrictionData",
            "ruleId": "Min 2 Max 5 Pasta allowed",
            "actionType": null,
            "conditions": {
                "locationCondition": {
                    "includedLocations": [
                        {
                            "enterpriseUnitId": "00000000000000000000000000035295"
                        }
                    ],
                    "excludedLocations": [
                        {
                            "enterpriseUnitId": "00000000000000000000000000035295"
                        }
                    ]
                },
                "retailSegmentCondition": {
                    "includedRetailSegmentsId": [
                        "string"
                    ],
                    "excludedRetailSegmentsId": [
                        "string"
                    ]
                },
                "productCondition": {
                    "transactionType ": "SaleOnly",
                    "includedProducts": [
                        {
                            "type": "string",
                            "value": "4210000526"
                        }
                    ],
                    "excludedProducts": [
                        {
                            "type": "string",
                            "value": "string"
                        }
                    ],
                    "includedGroups": [
                        "string"
                    ],
                    "excludedGroups": [
                        "string"
                    ],
                    "includedDepartments": [
                        "string"
                    ],
                    "excludedDepartments": [
                        "string"
                    ],
                    "includedCategories": [
                        "string"
                    ],
                    "excludedCategories": [
                        "string"
                    ]
                },
                "customerOrderCondition": {
                    "maxAmount": 0,
                    "maxQuantity": 0,
                    "containsLoyalty": true
                },
                "lineCondition": {
                    "isReturnLine": true,
                    "isDepartmentSaleLine": true,
                    "minLineAmount": 2,
                    "maxLineAmount": 5
                },
                "expressionCondition": {
                    "expression": "string"
                },
                "accountProfileCondition": {
                    "targetAccountProfileId": "string"
                },
                "paymentCondition": {
                    "entryMethod": "string",
                    "tenderTypeIds": [
                        "string"
                    ]
                },
                "couponRuleCondition": {
                    "seriesIds": [
                        "string"
                    ],
                    "couponTypes": [
                        "string"
                    ]
                }
            },
            "tag": "{{contextType}}"
        }
    ]
}