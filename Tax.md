
# Taxes

Taxes are applied to items when the item is added to the cart. More than one tax can be applied.
When a tax is applied the item tax, transaction tax, and transaction totals are calculated correctly and returned in the response from the Cart API.

Both Inclusive and Exclusive taxes can be added to items in a cart:

* Inclusive tax - the tax is included in the item price
* Exclusive tax – the tax is excluded from the item price and added to the transaction after the item is added to the cart.

Item and Transaction Fees are also supported by the Cart API.
On applying an Item Fee or Transaction Fee to an time in a cart, the Item and Transaction tax details as well as the transaction totals are calculated correctly and are included in the response.

Rounding rules can be applied to tax rates applied to items in a cart.
Tax amounts are rounded to the 3rd decimal point, and the remainder is allocated to the most expensive product in the transaction. Rounding shortages are allocated to the least expensive product in the transaction.

The rounding options are:

* Standard - mathematical rounding. Indicates that if the third decimal value in the tax value is more than 0.005 the tax value is rounded up. If the third decimal value in the tax value is equal to or less than 0.005 the tax value is rounded down. This is the default value.
* Up – the tax value is always rounded up (3rd decimal is truncated), no matter what the third decimal value is.
* Down – the tax value is always rounded down, no matter what the third decimal value is.

**HTTP Methods:**

* PUT
* GET
* DELETE

## Add Tax Rates

Used to add Tax Rates.

PUT

/emerald/selling-service/c1/selling-configuration/tax-settings/rates/{rateId}

The following example shows a request to add a 10 % tax rate.

```json
Request
{
  "taxAuthority": "USA",
  "taxType": "Tax",
  "descriptions": [
    {
      "culture": "en-US",
      "value": "10% tax"
    }
  ],
  "isIncluded": false,
  "startDateTime": "2021-05-06T15:02:30.508Z",
  "endDateTime": "2022-05-06T15:02:30.508Z",
  "rateCondition": {
    "zoneId": "string",
    "products": [
      {
        "isExclude": true,
        "itemCode": "string"
      }
    ],
    "categories": [
      {
        "categoryId": "Food TH",
        "categoryLabel": "Merchandise",
        "isExclude": false
      }
    ],
    "groups": [
      {
        "groupId": "string",
        "isExclude": true
      }
    ],
    "minimumTaxableAmount": 0,
    "containEatInProducts": true,
    "includeAccessorialFee": true
  },
  "calculationMethod": {
    "calculationMethodType": "Percent",
    "leveles": [
      {
        "from": 0,
        "to": 0,
        "value": 0,
        "supportedImposition": {
          "impositionId": "R1",
          "indicator": "null"
        },
        "BracketId": "null"
      }
    ]
  },
  "dependenceRates": [
    "string"
  ],
  "roundingMethod": "Standard",
  "isCouponReduceTaxationAmount": false,
  "taxableAmountRoundingStrategyKey": "null"
}
```

```json
Response Status OK
{
   OK
}
```

The following example shows a request to add a 5 % tax rate.

```json
Request

{
  "taxAuthority": "USA",
  "taxType": "Tax",
  "descriptions": [
    {
      "culture": "en-US",
      "value": "5% tax"
    }
  ],
  "isIncluded": false,
  "startDateTime": "2021-05-06T15:02:30.508Z",
  "endDateTime": "2022-05-06T15:02:30.508Z",
  "rateCondition": {
    "zoneId": "string",
    "products": [
      {
        "isExclude": true,
        "itemCode": "string"
      }
    ],
    "categories": [
      {
        "categoryId": "Food TH",
        "categoryLabel": "Merchandise",
        "isExclude": false
      }
    ],
    "groups": [
      {
        "groupId": "string",
        "isExclude": true
      }
    ],
    "minimumTaxableAmount": 0,
    "containEatInProducts": true,
    "includeAccessorialFee": true
  },
  "calculationMethod": {
    "calculationMethodType": "Percent",
    "leveles": [
      {
        "from": 0,
        "to": 0,
        "value": 0,
        "supportedImposition": {
          "impositionId": "R1",
          "indicator": "null"
        },
        "BracketId": "null"
      }
    ]
  },
  "dependenceRates": [
    "string"
  ],
  "roundingMethod": "Standard",
  "isCouponReduceTaxationAmount": false,
  "taxableAmountRoundingStrategyKey": "null"
}
```

```json
Response Status OK
{
   OK
}
```

## Get a Specific Tax Rate

Used to retrieve Tax Rate details for a specific tax.

GET

/emerald/selling-service/c1/selling-configuration/tax-settings/rates/{rateId}

```json
Response Status OK
{
    "rateId": "Rate1",
    "taxAuthority": "USA",
    "taxType": "Tax",
    "descriptions": [
        {
            "culture": "en-US",
            "value": "10% tax"
        }
    ],
    "isIncluded": false,
    "startDateTime": "2021-05-06T15:02:30.508Z",
    "endDateTime": "2022-05-06T15:02:30.508Z",
    "rateCondition": {
        "zoneId": "string",
        "products": [
            {
                "isExclude": true,
                "itemCode": "string"
            }
        ],
        "categories": [
            {
                "categoryId": "Food TH",
                "categoryLabel": "Merchandise",
                "isExclude": false
            }
        ],
        "groups": [
            {
                "groupId": "string",
                "isExclude": true
            }
        ],
        "minimumTaxableAmount": 0,
        "containEatInProducts": true,
        "includeAccessorialFee": true
    },
    "calculationMethod": {
        "calculationMethodType": "Percent",
        "leveles": [
            {
                "from": 0,
                "to": 0,
                "value": 0,
                "supportedImposition": {
                    "impositionId": "R1",
                    "indicator": "null"
                },
                "BracketId": "null"
            }
        ]
    },
    "dependenceRates": [
        "string"
    ],
    "roundingMethod": "Standard",
    "isCouponReduceTaxationAmount": false,
    "taxableAmountRoundingStrategyKey": "null"
}
```

## Get All Tax Rates

Used to retrieve Tax Rate details of all tax rates.

GET

/emerald/selling-service/c1/selling-configuration/tax-settings/rates

```json
Response Status OK
{
    "lastPage": true,
    "pageNumber": 0,
    "totalPages": 1,
    "totalResults": 3,
    "pageContent": [
        {
            "rateId": "{rateId}",
            "taxAuthority": "USA",
            "taxType": "Tax",
            "descriptions": [
                {
                    "culture": "en-US",
                    "value": "10% tax"
                }
            ],
            "isIncluded": false,
            "startDateTime": "2021-05-06T15:02:30.508Z",
            "endDateTime": "2022-05-06T15:02:30.508Z",
            "rateCondition": {
                "zoneId": "string",
                "products": [
                    {
                        "isExclude": true,
                        "itemCode": "string"
                    }
                ],
                "categories": [
                    {
                        "categoryId": "Food TH",
                        "categoryLabel": "Merchandise",
                        "isExclude": false
                    }
                ],
                "groups": [
                    {
                        "groupId": "string",
                        "isExclude": true
                    }
                ],
                "minimumTaxableAmount": 0,
                "containEatInProducts": true,
                "includeAccessorialFee": true
            },
            "calculationMethod": {
                "calculationMethodType": "Percent",
                "leveles": [
                    {
                        "from": 0,
                        "to": 0,
                        "value": 0,
                        "supportedImposition": {
                            "impositionId": "R1",
                            "indicator": "null"
                        },
                        "BracketId": "null"
                    }
                ]
            },
            "dependenceRates": [
                "string"
            ],
            "roundingMethod": "Standard",
            "isCouponReduceTaxationAmount": false,
            "taxableAmountRoundingStrategyKey": "null"
        },
        {
            "rateId": "Rate1",
            "taxAuthority": "USA",
            "taxType": "Tax",
            "descriptions": [
                {
                    "culture": "en-US",
                    "value": "10% tax"
                }
            ],
            "isIncluded": false,
            "startDateTime": "2021-05-06T15:02:30.508Z",
            "endDateTime": "2022-05-06T15:02:30.508Z",
            "rateCondition": {
                "zoneId": "string",
                "products": [
                    {
                        "isExclude": true,
                        "itemCode": "string"
                    }
                ],
                "categories": [
                    {
                        "categoryId": "Food TH",
                        "categoryLabel": "Merchandise",
                        "isExclude": false
                    }
                ],
                "groups": [
                    {
                        "groupId": "string",
                        "isExclude": true
                    }
                ],
                "minimumTaxableAmount": 0,
                "containEatInProducts": true,
                "includeAccessorialFee": true
            },
            "calculationMethod": {
                "calculationMethodType": "Percent",
                "leveles": [
                    {
                        "from": 0,
                        "to": 0,
                        "value": 0,
                        "supportedImposition": {
                            "impositionId": "R1",
                            "indicator": "null"
                        },
                        "BracketId": "null"
                    }
                ]
            },
            "dependenceRates": [
                "string"
            ],
            "roundingMethod": "Standard",
            "isCouponReduceTaxationAmount": false,
            "taxableAmountRoundingStrategyKey": "null"
        },
        {
            "rateId": "Rate2",
            "taxAuthority": "USA",
            "taxType": "Tax",
            "descriptions": [
                {
                    "culture": "en-US",
                    "value": "5% tax"
                }
            ],
            "isIncluded": false,
            "startDateTime": "2021-05-06T15:02:30.508Z",
            "endDateTime": "2022-05-06T15:02:30.508Z",
            "rateCondition": {
                "zoneId": "string",
                "products": [
                    {
                        "isExclude": true,
                        "itemCode": "string"
                    }
                ],
                "categories": [
                    {
                        "categoryId": "Food TH",
                        "categoryLabel": "Merchandise",
                        "isExclude": false
                    }
                ],
                "groups": [
                    {
                        "groupId": "string",
                        "isExclude": true
                    }
                ],
                "minimumTaxableAmount": 0,
                "containEatInProducts": true,
                "includeAccessorialFee": true
            },
            "calculationMethod": {
                "calculationMethodType": "Percent",
                "leveles": [
                    {
                        "from": 0,
                        "to": 0,
                        "value": 0,
                        "supportedImposition": {
                            "impositionId": "R1",
                            "indicator": "null"
                        },
                        "BracketId": "null"
                    }
                ]
            },
            "dependenceRates": [
                "string"
            ],
            "roundingMethod": "Standard",
            "isCouponReduceTaxationAmount": false,
            "taxableAmountRoundingStrategyKey": "null"
        }
    ]
}
```
