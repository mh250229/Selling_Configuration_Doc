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

PUT

/emerald/selling-service/c1/selling-configurationtax-settings/authorities/{authorityId}

Request

```json
{
    "descriptions": [{
            "culture": "en-US",
            "value": "First Authority"
        }
    ]
}
```

Response 200 OK

### Get Tax Authorities

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

## Tax Zones

### Map a tax zone to a store

PUT

 /selling-configuration/tax-settings/zones/{zoneId}

Request

```json
{
    "locations": [{
            "zoneType": "EnterpriseBusinessUnit",
            "locationId": "00000000000000000000000000035295"
        }
    ]
}
```

Response 200 OK

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

PUT

/emerald/selling-service/c1/selling-configuration/tax-settings/rates/{rateId}

Request

```json
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

Response 200 OK

### Add a 5 % tax rate

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

Response 200 OK

### Add a Tax Rate to the Authority and Zone

PUT

/selling-configuration/tax-settings/rates/{rateId}

Request

```json
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
        "zoneId":  "Zone1",
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

### Add a Tax Exemption

PUT

/emerald/selling-service/c1/selling-configuration/tax-settings/exemptions/{exemptionId}

Request

```json
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

Response 200 OK

### Get the Tax Exemptions

GET

/emerald/selling-service/c1/selling-configuration/tax-settings/exemptions

Request

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

Request

```json
{
  "enterpriseUnit": "00000000000000000000000000035295",
  "customerExemptionIdRequired": true,
  "exemptionCustomerNameRequired": true
}
```

Response 200 OK

### Get All Tax Parameters

GET

/emerald/selling-service/c1/selling-configuration/tax-settings/tax-parameters

Response

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

## Compound Tax

Compound Tax is tax calculated on top of other taxes (stacked tax).

For example, if an item is defined with two taxes, the first tax is calculated, and then the second tax rate. The total tax amount is the sum of both taxes. Both percentage and fixed tax rates are supported.

## Configuring a Compound Tax

Used to configure Compound Taxes imposed by the Tax Authority.

Compound tax configuration is not part of the Base Configuration.

The following are examples of Compound Tax Configuration required for the flows in the Selling Services.

### Add a Tax Rate 222 ($3.00 Fixed)

**HTTP Method:**

PUT

/emerald/selling-service/selling-configuration/v1/tax-settings/rates/222

Request

```json
{
    "taxAuthority": "USA",
    "taxType": "Tax",
    "descriptions": [
        {
            "culture": "en-US",
            "value": "Fixed 3 Dollars"
        }
    ],
    "isIncluded": false,
    "startDateTime": "2022-02-02T10:12:42.578039",
    "endDateTime": null,
    "rateCondition": {
        "zoneId": null,
        "products": null,
        "categories": [
            {
                "categoryId": "1-1-2C-002-001-003",
                "categoryLabel": "Merchandise",
                "isExclude": false
            }
        ],
        "groups": null,
        "minimumTaxableAmount": null,
        "containEatInProducts": null,
        "includeAccessorialFee": null
    },
    "calculationMethod": {
        "calculationMethodType": "FixedAmount",
        "leveles": [
            {
                "from": 0.0,
                "to": null,
                "value": 3,
                "supportedImposition": {
                    "impositionId": "1",
                    "indicator": "A"
                },
                "BracketId": null
            }
        ]
    },
    "dependenceRates": [
        ""
    ],
    "roundingMethod": "Standard",
    "isCouponReduceTaxationAmount": false,
    "taxableAmountRoundingStrategyKey": null
}
```

Response 200 OK

### Add Tax Rate 333 (10% Percent)

**HTTP Method:**

PUT

/emerald/selling-service/selling-configuration/v1/tax-settings/rates/333

Request

```json
{
    "taxAuthority": "USA",
    "taxType": "Tax",
    "descriptions": [
        {
            "culture": "en-US",
            "value": "10% precent"
        }
    ],
    "isIncluded": false,
    "startDateTime": "2022-02-02T10:12:42.5856133",
    "endDateTime": null,
    "rateCondition": {
        "zoneId": null,
        "products": null,
        "categories": [
            {
                "categoryId": "1-1-2C-002-001-003",
                "categoryLabel": "Merchandise",
                "isExclude": false
            }
        ],
        "groups": null,
        "minimumTaxableAmount": null,
        "containEatInProducts": null,
        "includeAccessorialFee": null
    },
    "calculationMethod": {
        "calculationMethodType": "Percent",
        "leveles": [
            {
                "from": 0.0,
                "to": null,
                "value": 10,
                "supportedImposition": {
                    "impositionId": "2",
                    "indicator": "C"
                },
                "BracketId": null
            }
        ]
    },
    "dependenceRates": [
        "222"
    ],
    "roundingMethod": "Standard",
    "isCouponReduceTaxationAmount": false,
    "taxableAmountRoundingStrategyKey": null
}
```

Response 200 OK

### Add Tax Rate 444 (5% Percent)

**HTTP Method:**

PUT

/emerald/selling-service/selling-configuration/v1/tax-settings/rates/444

Request

```json
{
    "taxAuthority": "USA",
    "taxType": "Tax",
    "descriptions": [
        {
            "culture": "en-US",
            "value": "5% precent"
        }
    ],
    "isIncluded": false,
    "startDateTime": "2022-02-02T10:12:42.5856133",
    "endDateTime": null,
    "rateCondition": {
        "zoneId": null,
        "products": null,
        "categories": [
            {
                "categoryId": "1-1-2C-002-001-003",
                "categoryLabel": "Merchandise",
                "isExclude": false
            }
        ],
        "groups": null,
        "minimumTaxableAmount": null,
        "containEatInProducts": null,
        "includeAccessorialFee": null
    },
    "calculationMethod": {
        "calculationMethodType": "Percent",
        "leveles": [
            {
                "from": 0.0,
                "to": null,
                "value": 5,
                "supportedImposition": {
                    "impositionId": "3",
                    "indicator": "C"
                },
                "BracketId": null
            }
        ]
    },
    "dependenceRates": [
        "333"
    ],
    "roundingMethod": "Standard",
    "isCouponReduceTaxationAmount": false,
    "taxableAmountRoundingStrategyKey": null
}
```

Response 200 OK

### Add Tax Rate 555 - Multi Tier Compound Tax

**HTTP Method:**

PUT

/emerald/selling-service/selling-configuration/v1/tax-settings/rates/Rate555

Request

```json
{
    "taxAuthority": "USA_r",
    "taxType": "Tax",
    "descriptions": [
        {
            "culture": "en-US",
            "value": "Multi tier tax1"
        }
    ],
    "isIncluded": false,
    "startDateTime": "2022-01-23T11:15:21.0368168",
    "endDateTime": null,
    "rateCondition": {
        "zoneId": null,
        "products": null,
        "categories": [
            {
                "categoryId": "20-1",
                "categoryLabel": "Tax",
                "isExclude": false
            }
        ],
        "groups": null,
        "minimumTaxableAmount": null,
        "containEatInProducts": null,
        "includeAccessorialFee": null
    },
    "calculationMethod": {
        "calculationMethodType": "MultiLevelTiered",
        "leveles": [
            {
                "from": 0.0,
                "to": 5.0,
                "value": 8.0,
                "supportedImposition": {
                    "impositionId": "11",
                    "indicator": "G"
                },
                "BracketId": null
            },
            {
                "from": 5.0,
                "to": 10.0,
                "value": 16.0,
                "supportedImposition": {
                    "impositionId": "12",
                    "indicator": "H"
                },
                "BracketId": null
            },
            {
                "from": 10.0,
                "to": null,
                "value": 20.0,
                "supportedImposition": {
                    "impositionId": "13",
                    "indicator": "I"
                },
                "BracketId": null
            }
        ]
    },
    "dependenceRates": [
        
    ],
    "roundingMethod": "Standard",
    "isCouponReduceTaxationAmount": false,
    "taxableAmountRoundingStrategyKey": null
}

```

Response  200  OK

## Multi Tiered Tax

Used to configure Multi Tiered Taxes imposed by the Tax Authority.

Multi Tiered tax configuration is not part of the Base Configuration.

The following are examples of Multi Tiered Tax Configuration required for the flows in the Selling Services.

## Add Tax Rate 1

**HTTP Method:**

PUT

/emerald/selling-service/selling-configuration/v1/tax-settings/rates/Rate1

Request

```json
{
  "taxAuthority": "USA",
  "taxType": "Tax",
  "descriptions": [
    {
      "culture": "en-US",
      "value": "Multi tier tax1"
    }
  ],
  "isIncluded": false,
  "startDateTime": "2022-01-03T07:56:30.509776",
  "endDateTime": null,
  "rateCondition": {
    "zoneId": null,
    "products": null,
    "categories": [
      {
        "categoryId": "Food TH",
        "categoryLabel": "Merchandise",
        "isExclude": false
      }
    ],
    "groups": null,
    "minimumTaxableAmount": null,
    "containEatInProducts": null,
    "includeAccessorialFee": null
  },
  "calculationMethod": {
    "calculationMethodType": "MultiLevelTiered",
    "leveles": [
      {
        "from": 0,
        "to": 2,
        "value": 8,
        "supportedImposition": {
          "impositionId": "R1",
          "indicator": "R1"
        },
        "BracketId": null
      },
      {
        "from": 2,
        "to": 4,
        "value": 16,
        "supportedImposition": {
          "impositionId": "R1",
          "indicator": "R1"
        },
        "BracketId": null
      },
      {
        "from": 4,
        "to": 6,
        "value": 18,
        "supportedImposition": {
          "impositionId": "R1",
          "indicator": "R1"
        },
        "BracketId": null
      },
      {
        "from": 6,
        "to": null,
        "value": 20,
        "supportedImposition": {
          "impositionId": "R1",
          "indicator": "R1"
        },
        "BracketId": null
      }
    ]
  },
  "dependenceRates": [],
  "roundingMethod": "Standard",
  "isCouponReduceTaxationAmount": false,
  "taxableAmountRoundingStrategyKey": null
}
```

Response  200 OK

## Add Tax Rate 5

**HTTP Method:**

PUT

/emerald/selling-service/selling-configuration/v1/tax-settings/rates/Rate5

Request

```json
{
  "taxAuthority": "USA",
  "taxType": "Tax",
  "descriptions": [
    {
      "culture": "en-US",
      "value": "Multi tier tax2"
    }
  ],
  "isIncluded": false,
  "startDateTime": "2022-01-03T07:56:30.5149324",
  "endDateTime": null,
  "rateCondition": {
    "zoneId": null,
    "products": null,
    "categories": [
      {
        "categoryId": "Candy",
        "categoryLabel": "Merchandise",
        "isExclude": false
      }
    ],
    "groups": null,
    "minimumTaxableAmount": null,
    "containEatInProducts": null,
    "includeAccessorialFee": null
  },
  "calculationMethod": {
    "calculationMethodType": "MultiLevelTiered",
    "leveles": [
      {
        "from": 0,
        "to": 10,
        "value": 5,
        "supportedImposition": {
          "impositionId": "R5",
          "indicator": "R5"
        },
        "BracketId": null
      },
      {
        "from": 10,
        "to": 50,
        "value": 10,
        "supportedImposition": {
          "impositionId": "R5",
          "indicator": "R5"
        },
        "BracketId": null
      },
      {
        "from": 50,
        "to": null,
        "value": 20,
        "supportedImposition": {
          "impositionId": "R5",
          "indicator": "R5"
        },
        "BracketId": null
      }
    ]
  },
  "dependenceRates": [],
  "roundingMethod": "Standard",
  "isCouponReduceTaxationAmount": false,
  "taxableAmountRoundingStrategyKey": null
}
```

Response  200  OK

## Top Tier Tax

Top Tier taxes enable Tax Authorities to apply taxes in which one tax rate determined by the item price is applied on the full item price.

The rate is taken from the Tax Tier table based on the item’s price. For example, Tier 1 with a 4.5% tax rate is applied to all items between $0.00 - $100.00. Tier 2 with a 8 % tax rate is applied to all items between $100.01 - $200.00

## Add Top Tier Tax Rate 1

**HTTP Method:**

PUT

/emerald/selling-service/selling-configuration/v1/tax-settings/rates/Rate1

Request

```json
{
    "taxAuthority": "USA",
    "taxType": "Tax",
    "descriptions": [
        {
            "culture": "en-US",
            "value": "Top Tier 1"
        }
    ],
    "isIncluded": false,
    "startDateTime": "2022-02-02T12:54:47.8518522",
    "endDateTime": null,
    "rateCondition": {
        "zoneId": null,
        "products": null,
        "categories": null,
        "groups": [
            {
            "groupid": "100",
            "isExclude": false
            }
            ],
        "minimumTaxableAmount": null,
        "containEatInProducts": null,
        "includeAccessorialFee": null
    },
    "calculationMethod": {
        "calculationMethodType": "TopLevelTiered",
        "leveles": [
            {
                "from": 0.0,
                "to": 30.0,
                "value": 5.0,
                "supportedImposition": {
                    "impositionId": "L",
                    "indicator": "L"
                },
                "BracketId": null
            },
            {
                "from": 30.0,
                "to": 100.0,
                "value": 10.0,
                "supportedImposition": {
                    "impositionId": "M",
                    "indicator": "M"
                },
                "BracketId": null
            },
            {
                "from": 100.0,
                "to": null,
                "value": 20.0,
                "supportedImposition": {
                    "impositionId": "N",
                    "indicator": "N"
                },
                "BracketId": null
            }
        ]
    },
    "dependenceRates": [],
    "roundingMethod": "Standard",
    "isCouponReduceTaxationAmount": false,
    "taxableAmountRoundingStrategyKey": null
}
```

### Add Top Tier Tax Rate 2

**HTTP Method:**

PUT

/emerald/selling-service/selling-configuration/v1/tax-settings/rates/Rate2

Request

```json
{
    "taxAuthority": "USA",
    "taxType": "Tax",
    "descriptions": [
        {
            "culture": "en-US",
            "value": "Top Tier 2"
        }
    ],
    "isIncluded": false,
    "startDateTime": "2022-02-02T12:54:47.8662354",
    "endDateTime": null,
    "rateCondition": {
        "zoneId": null,
        "products": null,
                "groups": [
                    {
                        "groupid": "GroupForTax2",
            "isExclude": false
            }],
        "minimumTaxableAmount": null,
        "containEatInProducts": null,
        "includeAccessorialFee": null
    },
    "calculationMethod": {
        "calculationMethodType": "TopLevelTiered",
        "leveles": [
            {
                "from": 0.0,
                "to": 20.0,
                "value": 3.0,
                "supportedImposition": {
                    "impositionId": "C",
                    "indicator": "C"
                },
                "BracketId": null
            },
            {
                "from": 20.0,
                "to": null,
                "value": 7.0,
                "supportedImposition": {
                    "impositionId": "D",
                    "indicator": "D"
                },
                "BracketId": null
            }
        ]
    },
    "dependenceRates": [],
    "roundingMethod": "Standard",
    "isCouponReduceTaxationAmount": false,
    "taxableAmountRoundingStrategyKey": null
}
```

### Add Tax Rate 111

**HTTP Method:**

PUT

/emerald/selling-service/selling-configuration/v1/tax-settings/rates/Rate1

Request

```json
{
    "taxAuthority": "USA",
    "taxType": "Tax",
    "descriptions": [
        {
            "culture": "en-US",
            "value": "BracketsTopTiered"
        }
    ],
    "isIncluded": false,
    "startDateTime": "2022-02-14T07:30:16.9170013",
    "endDateTime": null,
    "rateCondition": {
        "zoneId": null,
        "products": null,
        "categories": null,
        "groups": [
            {
                "groupId": "GroupCheese",
                "isExclude": false
            }
        ],
        "minimumTaxableAmount": null,
        "containEatInProducts": null,
        "includeAccessorialFee": null
    },
    "calculationMethod": {
        "calculationMethodType": "BracketsTopTiered",
        "leveles": [
            {
                "from": 0.0,
                "to": 5.0,
                "value": 8.0,
                "supportedImposition": {
                    "impositionId": "A",
                    "indicator": "A"
                },
                "BracketId": "Brackets8"
            },
            {
                "from": 5.0,
                "to": 20.0,
                "value": 6.0,
                "supportedImposition": {
                    "impositionId": "C",
                    "indicator": "C"
                },
                "BracketId": "Brackets6"
            },
            {
                "from": 20.0,
                "to": null,
                "value": 8.0,
                "supportedImposition": {
                    "impositionId": "E",
                    "indicator": "E"
                },
                "BracketId": "Brackets8"
            }
        ]
    },
    "dependenceRates": [],
    "roundingMethod": "Standard",
    "isCouponReduceTaxationAmount": false,
    "taxableAmountRoundingStrategyKey": null
}
```