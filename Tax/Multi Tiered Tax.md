# Multi Tiered Tax

Multi-tiered taxes enable Tax Authorities to apply different tax rates according to the item price.

Multi-tiered taxes are composed of several tax tiers, the tax is calculated by adding the taxable amount for all the items lines required for a specific tax rate and utilizing the tiers in ascending order.

Thresholds are defined to specify the maximum amount each tax level is applied to. For example, the first tier rate is applied to the first item added into the cart. If the item price is more than the first tier threshold, the remaining price amount is calculated according to the second tier rate. Taxes are calculated according to each tier until tax is applied to the full item price.

## Configuring a Multi Tiered Tax

Used to configure Multi Tiered Taxes imposed by the Tax Authority.

Multi Tiered tax configuration is not part of the Base Configuration.

The following are examples of Multi Tiered Tax Configuration required for the flows in the Selling Services.

### Tax Rate 1

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

### Tax Rate 5

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
