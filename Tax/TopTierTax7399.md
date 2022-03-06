# Top Tier Tax

Top Tier taxes enable Tax Authorities to apply taxes in which one tax rate determined by the item price is applied on the full item price.

The rate is taken from the Tax Tier table based on the item’s price. For example, Tier 1 with a 4.5% tax rate is applied to all items between $0.00 - $100.00. Tier 2 with a 8 % tax rate is applied to all items between $100.01 - $200.00

## Configuring a Top Tier Tax

Used to configure Top Tier Taxes imposed by the Tax Authority.

Top Tier tax configuration is not part of the Base Configuration.

The following are examples of Top Tier Tax Configuration required for the flows in the Selling Services.

### Tax Rate 1

**HTTP Method:**

PUT

/emerald/selling-service/selling-configuration/v1/tax-settings/rates/Rate1

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

### Tax Rate 2

**HTTP Method:**

PUT

/emerald/selling-service/selling-configuration/v1/tax-settings/rates/Rate2

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
