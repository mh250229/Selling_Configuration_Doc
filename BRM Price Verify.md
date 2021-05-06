# BRM Price Verify

The Cart API supports the Price Verify BRM.

The BRM is triggered when the product price is verifed and the item price is different to the product price in the catalog. If the price is more or less than the catalog price the product cannot be sold.

The BRM is set up as follows:

* Rule Id -
* Rule Type -
* Applied on -
* Action Type

**HTTP Methods:**

* PUT
* GET
* DELETE

## Add a Price Verify Business Rule

Used to add a Price Verify business rule.

PUT

/emerald/selling-service/c1/selling-configuration/business-rules-settings/price-verifies/{ruleId}

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


Response 200 OK
{
   OK
}
```

## Get Price Verify Business Rules

Used to retrieve Price Verify business rule details.

GET

/emerald/selling-service/c1/selling-configuration/business-rules-settings/price-verifies

```json
Response 200 OK
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
