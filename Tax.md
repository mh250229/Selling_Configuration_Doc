
# Taxes

Taxes are applied to items when the item is added to the cart. More than one tax can be applied.
When a tax is applied, the item tax, transaction tax, and transaction totals are calculated correctly and returned in the response from the Cart API.
In the current version of the Selling Cart Service, the Cart is also calculating the Tax with its own internal engine.
Hence, Tax definitions are currently part of the Selling configuration.

## Tax Authorities

Tax Authorities are government entities authorized by law to assess, levy, and collect taxes.

The Tax Authority determines the tax rates that need to be imposed.

**HTTP Methods:**

* PUT
* GET
* DELETE

### Add Tax Authorities

Used to add Tax Authorities.

PUT

/emerald/selling-service/c1/selling-configurationtax-settings/authorities/{authorityId}

```json
Request
{
    "descriptions": [{
            "culture": "en-US",
            "value": "First Authority"
        }
    ]
}
```

Response OK.

### Get Tax Authorities

Used to retrieve Tax Authorities details.

GET

/emerald/selling-service/c1/selling-configuration/tax-settings/authorities/effective-authorities

Response

```json
{
    "authorityId": "1",
    "descriptions": [
        {
            "culture": "en-US",
            "value": "First Authority"
        }
    ]
}
```

### Tax Zones

This example shows how to map a tax zone to a store.

PUT /selling-configuration/tax-settings/zones/{zoneId}

```json
{
    "locations": [{
            "zoneType": "EnterpriseBusinessUnit",
            "locationId": "00000000000000000000000000035295"
        }
    ]
}
```

Response Status OK

## Tax Rates

Both Inclusive and Exclusive tax rates can be applied to items in a cart:

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

### Add Tax Rates

Used to add Tax Rates.

PUT

/emerald/selling-service/c1/selling-configuration/tax-settings/rates/{rateId}

**The following example shows a request to add a 10 % tax rate.**

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
  "startDateTime": "2021-11-10T14:29:23.8509277",
  "endDateTime": "null",
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

Response Status OK

**The following example shows a request to add a 5 % tax rate.**

Request

```json

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
  "startDateTime": "2021-11-10T14:29:23.8509277",
  "endDateTime": "null",
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

Response Status OK

### Adding a Tax Rate to the Authority and Zone

PUT
/selling-configuration/tax-settings/rates/{rateId}

```json
Request
{
    "taxType": "Tax",
    "taxAuthority": "TaxAuthority1",
    "descriptions": [{
            "culture": "en-US",
            "value": "MyRate"
        }
    ],
    "isIncluded": false,
    "startDateTime": "2000-01-01T00:00:00",
    "endDateTime": "0001-01-01T00:00:00",
    "rateCondition": {
        "zoneId": {zone-id},
        "products": [],
        "categories": [],
        "groups": [{
                "groupId": "GroupForTax7",
                "isExclude": false
            }
        ],
        "minimumTaxableAmount": 0.01,
        "containEatInProducts": null,
        "includeAccessorialFee": null
    },
    "calculationMethod": {
        "calculationMethodType": "Percent",
        "levels": [{
                "from": 0.0,
                "to": null,
                "value": 10.0,
                "supportedImposition": {
                    "impositionId": "E",
                    "indicator": null
                }
            }
        ]
    },
    "dependenceRates": [],
    "roundingMethod": 0,
    "isCouponReduceTaxationAmount": false,
    "taxableAmountRoundingStrategyKey": null
}
```

### Get a Specific Tax Rate

Used to retrieve Tax Rate details for a specific tax.

GET

/emerald/selling-service/c1/selling-configuration/tax-settings/rates/{rateId}

Response

```json

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
    "startDateTime": "2021-11-10T14:29:23.8509277",
    "endDateTime": "null",
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

### Get All Tax Rates

Used to retrieve Tax Rate details of all tax rates.

GET

/emerald/selling-service/c1/selling-configuration/tax-settings/rates

Response

```json
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
            "startDateTime": "2021-11-10T14:29:23.8509277",
            "endDateTime": "null",
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
            "startDateTime": "2021-11-10T14:29:23.8509277",
            "endDateTime": "null",
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
            "startDateTime": "2021-11-10T14:29:23.8509277",
            "endDateTime": "null",
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

## Tax Exemptions

Tax Exemptions are issued by Tax Authorities and are performed at the transaction (Cart) level.

Tax Exemptions can be reversed.

**HTTP Methods:**

* PUT Tax Exemptions
* PUT Tax Parameters to capture Customer ID and Name of customers eligible for tax exemptions
* GET
* DELETE

### Add Tax Exemption

Used to add Tax Exemptions.
The following example shows how to add a tax exemption for eWIC Tender exemption.

PUT

/emerald/selling-service/c1/selling-configuration/tax-settings/exemptions/{exemptionId}

{exemptionId} = the exemption name.

PUT
/emerald/selling-service/selling-configuration/v1/tax-settings/exemptions/eWic_TaxExemptionUSA%20

```Json
{
  "taxAuthority": "USA1",
  "descriptions": [
    {
      "culture": "en-US",
      "value": "eWic Tender Exemption"
    }
  ],
  "exemptionConditions": {
    "exemptByTender": [
      "42"
    ],
    "exemptByDiscountAuthority": false,
    "exemptByAuthority": false,
    "exemptByTaxRate": null
  },
  "exemptionMethod": {
    "exemptionMethodType": "Tender",
    "imposition": null,
    "percentage": null
  }
}
```

Response: OK

### Get Tax Exemptions

Used to retrieve all the details of all Tax Exemptions.

GET

/emerald/selling-service/c1/selling-configuration/tax-settings/exemptions

```json
{
    "lastPage": true,
    "pageNumber": 0,
    "totalPages": 1,
    "totalResults": 1,
    "pageContent": [
        {
            "exemptionId": "{exemptionId}",
            "taxAuthority": "USA1",
            "descriptions": [
                {
                    "culture": "en-US",
                    "value": "eWic Tender Exemption"
                }
            ],
            "exemptionConditions": {
                "exemptByTender": [
                    "42"
                ],
                "exemptByDiscountAuthority": false,
                "exemptByAuthority": false,
                "exemptByTaxRate": null
            },
            "ExemptionMethod": {
                "exemptionMethodType": "Tender",
                "imposition": null,
                "percentage": null
            }
        }
    ]
}
```

## Tax Parameters

Used to add the Customer ID and Name of customers eligible for Tax Exemptions.

The Customer details are recorded for Tax Exemptions at both the item and transaction level.

When configured to capture on or both of the customer details, and a Tax Exemption is added without customer details, an exception is thrown and the Tax Exemption is not added to the cart.

### Add Tax Parameters

The {enterpriseUnit} is the Enterprise Unit for which you are adding tax parameters.

PUT

/emerald/selling-service/c1/selling-configuration/tax-settings/tax-parameters/{enterpriseUnit}

```json
Request
{
  "enterpriseUnit": "00000000000000000000000000035295",
  "customerExemptionIdRequired": true,
  "exemptionCustomerNameRequired": true
}
```

Response Status OK

### Get All Tax Parameters

Used to retrieve all the Tax Parameter details.

GET

/emerald/selling-service/c1/selling-configuration/tax-settings/tax-parameters

Response Status OK

```json
{
    "lastPage": true,
    "pageNumber": 0,
    "totalPages": 1,
    "totalResults": 1,
    "pageContent": [
        {
            "enterpriseUnit": "{enterpriseUnit}",
            "configuration": {
                "enterpriseUnit": "00000000000000000000000000035295",
                "customerExemptionIdRequired": true,
                "exemptionCustomerNameRequired": true
            }
        }
    ]
}
```
