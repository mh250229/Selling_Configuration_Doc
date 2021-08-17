
## Tax Configuration

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

### Get Tax Authorities

Used to retrieve Tax Authorities details.

GET

/emerald/selling-service/c1/selling-configuration/tax-settings/authorities/effective-authorities

```json
Response Status OK
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




### Mapping a Tax Zone to a Store

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

```json
Response Status OK
{
   OK
}
```

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


## Get Tax Rates

### Get a Specific Tax Rate

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

## Tax Exemptions

Tax Exemptions are issued by Tax Authorities, and are performed at the transaction (Cart) level.

Tax Exemptions can be reversed.

**HTTP Methods:**

* PUT Tax Exemptions
* PUT Tax Parameters to capture Customer ID and Name of customers eligible for tax exemptions
* GET
* DELETE

### Add Tax Rates Exemption

Used to add Tax Exemptions.

PUT

/emerald/selling-service/c1/selling-configuration/tax-settings/exemptions/{exemptionId}

```json
Request
{
    "taxAuthority": "USA",
    "descriptions": [
        {
            "culture": "en-US",
            "value": "First Exemption"
        }
    ],
    "exemptionConditions": {
        "exemptByTender": [
            "null"
        ],
        "exemptByDiscountAuthority": false,
        "exemptByAuthority": true,
        "exemptByTaxRate": [
            "null"
        ]
    },
    "ExemptionMethod": {
        "exemptionMethodType": "FullExemption",
        "imposition": "null",
        "percentage": null
    }
}
```

```json
Response Status OK
{
   OK
}
```

## Get Tax Exemptions

### Get a Specific Tax Exemption

Used to retrieve Tax Exemption details.
The {exemptionId} is the Tax exemption name you are retrieving.

GET

/emerald/selling-service/c1/selling-configuration/tax-settings/exemptions/{exemptionId}

```json
Response Status OK
<TaxExemptionData xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">
    <TaxAuthority>USA</TaxAuthority>
    <Descriptions>
        <Description>
            <Culture>String</Culture>
            <Value>First Exemption</Value>
        </Description>
    </Descriptions>
    <ExemptionConditions>
        <ExemptByTender>
            <string>null</string>
        </ExemptByTender>
        <ExemptByDiscountAuthority>false</ExemptByDiscountAuthority>
        <ExemptByAuthority>true</ExemptByAuthority>
        <ExemptByTaxRate>
            <string>null</string>
        </ExemptByTaxRate>
    </ExemptionConditions>
    <ExemptionMethod>
        <ExemptionMethodType>Discount</ExemptionMethodType>
        <Imposition>null</Imposition>
        <Percentage>21.15</Percentage>
    </ExemptionMethod>
    <ExemptionId>{exemptionId}</ExemptionId>
</TaxExemptionData>
```

### Get All Tax Exemptions

Used to retrieve all the details of all Tax Exemptions.

GET

/emerald/selling-service/c1/selling-configuration/tax-settings/exemptions

```json
Response Status OK
<TaxExemptionResponse xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">
    <LastPage>true</LastPage>
    <PageNumber>0</PageNumber>
    <TotalPages>1</TotalPages>
    <TotalResults>3</TotalResults>
    <PageContent>
        <TaxExemptionData>
            <TaxAuthority>USA</TaxAuthority>
            <Descriptions>
                <Description>
                    <Culture>String</Culture>
                    <Value>First Exemption</Value>
                </Description>
            </Descriptions>
            <ExemptionConditions>
                <ExemptByTender>
                    <string>null</string>
                </ExemptByTender>
                <ExemptByDiscountAuthority>false</ExemptByDiscountAuthority>
                <ExemptByAuthority>true</ExemptByAuthority>
                <ExemptByTaxRate>
                    <string>null</string>
                </ExemptByTaxRate>
            </ExemptionConditions>
            <ExemptionMethod>
                <ExemptionMethodType>Discount</ExemptionMethodType>
                <Imposition>null</Imposition>
                <Percentage>21.0</Percentage>
            </ExemptionMethod>
            <ExemptionId>1</ExemptionId>
        </TaxExemptionData>
        <TaxExemptionData>
            <TaxAuthority>USA</TaxAuthority>
            <Descriptions>
                <Description>
                    <Culture>String</Culture>
                    <Value>First Exemption</Value>
                </Description>
            </Descriptions>
            <ExemptionConditions>
                <ExemptByTender>
                    <string>null</string>
                </ExemptByTender>
                <ExemptByDiscountAuthority>false</ExemptByDiscountAuthority>
                <ExemptByAuthority>true</ExemptByAuthority>
                <ExemptByTaxRate>
                    <string>null</string>
                </ExemptByTaxRate>
            </ExemptionConditions>
            <ExemptionMethod>
                <ExemptionMethodType>Discount</ExemptionMethodType>
                <Imposition>null</Imposition>
                <Percentage>21.15</Percentage>
            </ExemptionMethod>
            <ExemptionId>{exemptionId}</ExemptionId>
        </TaxExemptionData>
        <TaxExemptionData>
            <TaxAuthority>USA</TaxAuthority>
            <Descriptions>
                <Description>
                    <Culture>en-US</Culture>
                    <Value>First Exemption</Value>
                </Description>
            </Descriptions>
            <ExemptionConditions>
                <ExemptByTender>
                    <string>null</string>
                </ExemptByTender>
                <ExemptByDiscountAuthority>false</ExemptByDiscountAuthority>
                <ExemptByAuthority>true</ExemptByAuthority>
                <ExemptByTaxRate>
                    <string>null</string>
                </ExemptByTaxRate>
            </ExemptionConditions>
            <ExemptionMethod>
                <ExemptionMethodType>FullExemption</ExemptionMethodType>
                <Imposition>null</Imposition>
                <Percentage xsi:nil="true" />
            </ExemptionMethod>
            <ExemptionId>FullExemption</ExemptionId>
        </TaxExemptionData>
    </PageContent>
</TaxExemptionResponse>
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
}
```

```json
Response Status OK
{
   OK
}
```

## Get All Tax Parameters

Used to retrieve all the Tax Parameter details.

GET

/emerald/selling-service/c1/selling-configuration/tax-settings/tax-parameters

```json
Response Status OK
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
