# BRM (Business Rules Management)

BRMs define rules and restrictions which are linked to messages that are triggered by various behaviors.
A big chunk of configurations fall under this title and are arranged according to different BRM types.
Each type is concerned with a different function or situation concerning the Cart.
While any configuration may be considered as a kind of business rule, the actual BRM types are mainly around limiting or adding steps to the "happy path" flow of selling.

Each BRM consists of a Behavior, optional Conditions, and an Action.
+ Behavior -  identifies the business situation or event in the Cart, like adding an item, existence of a Coupon, Cart total reaching a specific threshold etc.
+ Conditions - refine and restrict the Behavior scope, for example, on adding a specific item Id.
+ Action - what should be done when a situation and conditions are met. For example, require manager approval. See BRM Action Types.

BRM configuration is arranged in a way that allows listing all existing BRMs and their types (BRM Basic Data), and then provides specific endpoints for obtaining an manipulating a specific BRM type.

**Note:**
BRM and some other configurations reference a "messageId".
This messageId should reference an existing Message resource, containing the detailed multi-language message text. See Messages.


## BRM Price Override

The Cart API supports the Price Override BRM.

The BRM is triggered when the product price is overridden, and the new price exceeds the maximum percentage allowed to override an item price.

The BRM is set up as follows:

* Rule Id - The BRM name
* Rule Type – PriceOverrideRestrictionData
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

### Add a Price Override Business Rule

Used to add a Price Override business rule.
The {ruleId} is the name of the business rule.

PUT
/emerald/selling-service/c1/selling-configuration/business-rules-settings/price-overrides/{ruleId}

``` json
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

### Get Price Override Business Rules

Used to retrieve Price Override business rule details.

GET

/emerald/selling-service/c1/selling-configuration/business-rules-settings/price-overrides

``` json
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

## BRM Price Verify

The Cart API supports the Price Verify BRM.

The BRM is triggered when the product price is verifed and the item price is different to the product price in the catalog. If the price is more or less than the catalog price the product cannot be sold.

The BRM is set up as follows:

* Rule Id - The BRM name
* Rule Type - PriceVerifyRestrictionData
* Applied on -
* Action Type -

**HTTP Methods:**

* PUT
* GET
* DELETE

### Add a Price Verify Business Rule

Used to add a Price Verify business rule. The {ruleId} is the name of the business rule.

PUT

/emerald/selling-service/c1/selling-configuration/business-rules-settings/price-verifies/{ruleId}

``` json
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
          "enterpriseUnitId": "string"
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
          "value": "string"
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
      "minLineAmount": 0,
      "maxLineAmount": 0
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
  "tag": "string",
  "maxPercentageChange": 0,
  "maxFixedValueChange": 0,
  "direction": "Increase"
}
```

``` json
Response 200 OK
{
   OK
}
```

### Get Price Verify Business Rules

Used to retrieve Price Verify business rule details.

GET

/emerald/selling-service/c1/selling-configuration/business-rules-settings/price-verifies

``` json
Response 200 OK
{
    "lastPage": true,
    "pageNumber": 0,
    "totalPages": 1,
    "totalResults": 1,
    "pageContent": [
        {
            "maxPercentageChange": 0,
            "maxFixedValueChange": 0,
            "direction": "Increase",
            "ruleType": "PriceVerifyRestrictionData",
            "ruleId": "{ruleId}",
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
                            "enterpriseUnitId": "string"
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
                            "value": "string"
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
                    "minLineAmount": 0,
                    "maxLineAmount": 0
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
            "tag": "string"
        }
    ]
}
```

## BRM Void Limit Restrictions

The Cart API supports the Void Item BRM.
The BRM evaluates the items voided in a cart.
A 'Void item' restriction is created once one of the following criteria are met:

* Voided line amount > Max allowed amount per line
* Voided ticket amount >Max allowed amount per ticket

Both criteria can be configured together.
The maximum allowed limit can be any positive value including 0.
A Void item BRM includes:

* Rule Id - The BRM name
* Rule type- VoidLimitRestrictionData
* Applied on  - Voideditem
* Max allowed amount per line
* Max allowed amount per ticket
* Action type

  * Restricted audit line id
  * Original line id

If the client uses the 'Enforce' flag (instead of inform), the item is not removed from the cart until the restriction is resolved.
If the ‘Enforce’ flag is not used, the item is removed and captured in the audit line and the restriction is created.
The following Action type options are supported by the Void Item BRM:

* Approval required
* Select reason
* Prompt for confirmation
* Input data required
* Notification

**Note:**
Void Item restrictions cannot be prohibited.

**HTTP Methods:**

* PUT VoidLimitRules_PUT
* GET VoidLimitRules_GET

### Add Void Item Business Rule

Used to add a void item business rule. The {ruleId} is the name of the business rule.

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
```

```json
Response 200 OK
{
   OK
}
```

### Get Void Item Business Rules

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

## BRM Total Transaction

The Cart API supports the Total Transaction BRM. The {ruleId} is the name of the business rule.

The BRM is set up as follows:

* Rule Id - The BRM name
* Rule Type - TotalTransactionRestrictionData
* Applied on - Transaction
* Action Type

The transaction limit amount are configured in the CustomerOrderCondition element.

If the restriction is not solved when the Cart is moved to Finalize Status, an exception is returned.

**HTTP Methods:**

* PUT
* GET
* DELETE

### Add a Total Transaction Business Rule

Used to add a Total Transaction business rule.
The {ruleId} is the name of the business rule.

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
```

```json
Response 200 OK
{
   OK
}
```

### Get Total Transaction Business Rules

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
```

### GET BusinessRules_Delete

Used to delete a business rule set up in the system. The {ruleId} is the name of the BRM you are deleting.

/emerald/selling-service/c1/selling-configuration/business-rules-settings/rules/{ruleId}

```json

Request
{

}
```

```json
Response
{
   OK
}
```
