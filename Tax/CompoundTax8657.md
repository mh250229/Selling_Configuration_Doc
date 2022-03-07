# Compound Tax

Compound Tax is tax calculated on top of other taxes (stacked tax).

For example, if an item is defined with two taxes, the first tax is calculated, and then the second tax rate. The total tax amount is the sum of both taxes. Both percentage and fixed tax rates are supported.

## Configuring a Compound Tax

Used to configure Compound Taxes imposed by the Tax Authority.

Compound tax configuration is not part of the Base Configuration.

The following are examples of Compound Tax Configuration required for the flows in the Selling Services.

### Tax Rate 222 ($3.00 Fixed)

**HTTP Method:**

PUT

/emerald/selling-service/selling-configuration/v1/tax-settings/rates/222

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

### Tax Rate 333 (10% Percent)

**HTTP Method:**

PUT

/emerald/selling-service/selling-configuration/v1/tax-settings/rates/333

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

### Tax Rate 444 (5% Percent)

**HTTP Method:**

PUT

/emerald/selling-service/selling-configuration/v1/tax-settings/rates/444

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
