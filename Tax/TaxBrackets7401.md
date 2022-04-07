# Tax Brackets

The Tax Bracket tax calculation method is used to apply a complex calculation comprised of a tax rate on part of the taxable amount and a Tax Brackets table for the remaining amount.
Tax Brackets serve as cutoff levels for sales tax rates, and are required by regulation in certain US States, such as Maryland, Florida.
Tax Bracket tables are defined according to Tax Authority regulations, and contain the price increments between each cent increase in tax.

## Configuring Tax Brackets

Used to configure Tax Brackets.

Tax Bracket configuration is not part of the Base Configuration.

The following shows an example of Tax Bracket Configuration required for the flows in the Selling Services.

### Tax Bracket - Brackets Definition Data Brackets625

**HTTP Method:**

PUT

/emerald/selling-service/selling-configuration/v1/tax-settings/brackets/Bracket625

Request

```json
{
  "descriptions": [
    {
      "culture": "en-US",
      "value": "USA"
    }
  ]
}
```{
    "bracketsData": [
        {
            "from": {
                "value": 0.00,
                "currency": {
                    "isoCurrencySymbol": "USD",
                    "leastMonetaryUnit": 0.0
                }
            },
            "to": {
                "value": 0.09,
                "currency": {
                    "isoCurrencySymbol": "USD",
                    "leastMonetaryUnit": 0.0
                }
            },
            "amount": {
                "value": 0.0,
                "currency": {
                    "isoCurrencySymbol": "USD",
                    "leastMonetaryUnit": 0.0
                }
            }
        },
        {
            "from": {
                "value": 0.1,
                "currency": {
                    "isoCurrencySymbol": "USD",
                    "leastMonetaryUnit": 0.0
                }
            },
            "to": {
                "value": 0.16,
                "currency": {
                    "isoCurrencySymbol": "USD",
                    "leastMonetaryUnit": 0.0
                }
            },
            "amount": {
                "value": 0.01,
                "currency": {
                    "isoCurrencySymbol": "USD",
                    "leastMonetaryUnit": 0.0
                }
            }
        },
        {
            "from": {
                "value": 0.17,
                "currency": {
                    "isoCurrencySymbol": "USD",
                    "leastMonetaryUnit": 0.0
                }
            },
            "to": {
                "value": 0.32,
                "currency": {
                    "isoCurrencySymbol": "USD",
                    "leastMonetaryUnit": 0.0
                }
            },
            "amount": {
                "value": 0.02,
                "currency": {
                    "isoCurrencySymbol": "USD",
                    "leastMonetaryUnit": 0.0
                }
            }
        },
        {
            "from": {
                "value": 0.33,
                "currency": {
                    "isoCurrencySymbol": "USD",
                    "leastMonetaryUnit": 0.0
                }
            },
            "to": {
                "value": 0.48,
                "currency": {
                    "isoCurrencySymbol": "USD",
                    "leastMonetaryUnit": 0.0
                }
            },
            "amount": {
                "value": 0.03,
                "currency": {
                    "isoCurrencySymbol": "USD",
                    "leastMonetaryUnit": 0.0
                }
            }
        },
        {
            "from": {
                "value": 0.49,
                "currency": {
                    "isoCurrencySymbol": "USD",
                    "leastMonetaryUnit": 0.0
                }
            },
            "to": {
                "value": 0.64,
                "currency": {
                    "isoCurrencySymbol": "USD",
                    "leastMonetaryUnit": 0.0
                }
            },
            "amount": {
                "value": 0.04,
                "currency": {
                    "isoCurrencySymbol": "USD",
                    "leastMonetaryUnit": 0.0
                }
            }
        },
        {
            "from": {
                "value": 0.65,
                "currency": {
                    "isoCurrencySymbol": "USD",
                    "leastMonetaryUnit": 0.0
                }
            },
            "to": {
                "value": 0.80,
                "currency": {
                    "isoCurrencySymbol": "USD",
                    "leastMonetaryUnit": 0.0
                }
            },
            "amount": {
                "value": 0.05,
                "currency": {
                    "isoCurrencySymbol": "USD",
                    "leastMonetaryUnit": 0.0
                }
            }
        },
        {
            "from": {
                "value": 0.81,
                "currency": {
                    "isoCurrencySymbol": "USD",
                    "leastMonetaryUnit": 0.0
                }
            },
            "to": {
                "value": 0.96,
                "currency": {
                    "isoCurrencySymbol": "USD",
                    "leastMonetaryUnit": 0.0
                }
            },
            "amount": {
                "value": 0.06,
                "currency": {
                    "isoCurrencySymbol": "USD",
                    "leastMonetaryUnit": 0.0
                }
            }
        },
        {
            "from": {
                "value": 0.97,
                "currency": {
                    "isoCurrencySymbol": "USD",
                    "leastMonetaryUnit": 0.0
                }
            },
            "to": {
                "value": 1.12,
                "currency": {
                    "isoCurrencySymbol": "USD",
                    "leastMonetaryUnit": 0.0
                }
            },
            "amount": {
                "value": 0.07,
                "currency": {
                    "isoCurrencySymbol": "USD",
                    "leastMonetaryUnit": 0.0
                }
            }
        },
        {
            "from": {
                "value": 1.13,
                "currency": {
                    "isoCurrencySymbol": "USD",
                    "leastMonetaryUnit": 0.0
                }
            },
            "to": {
                "value": 1.28,
                "currency": {
                    "isoCurrencySymbol": "USD",
                    "leastMonetaryUnit": 0.0
                }
            },
            "amount": {
                "value": 0.08,
                "currency": {
                    "isoCurrencySymbol": "USD",
                    "leastMonetaryUnit": 0.0
                }
            }
        },
        {
            "from": {
                "value": 1.29,
                "currency": {
                    "isoCurrencySymbol": "USD",
                    "leastMonetaryUnit": 0.0
                }
            },
            "to": {
                "value": 1.44,
                "currency": {
                    "isoCurrencySymbol": "USD",
                    "leastMonetaryUnit": 0.0
                }
            },
            "amount": {
                "value": 0.09,
                "currency": {
                    "isoCurrencySymbol": "USD",
                    "leastMonetaryUnit": 0.0
                }
            }
        },
        {
            "from": {
                "value": 1.45,
                "currency": {
                    "isoCurrencySymbol": "USD",
                    "leastMonetaryUnit": 0.0
                }
            },
            "to": {
                "value": 1.6,
                "currency": {
                    "isoCurrencySymbol": "USD",
                    "leastMonetaryUnit": 0.0
                }
            },
            "amount": {
                "value": 0.1,
                "currency": {
                    "isoCurrencySymbol": "USD",
                    "leastMonetaryUnit": 0.0
                }
            }
        },
        {
            "from": {
                "value": 1.61,
                "currency": {
                    "isoCurrencySymbol": "USD",
                    "leastMonetaryUnit": 0.0
                }
            },
            "to": {
                "value": 1.76,
                "currency": {
                    "isoCurrencySymbol": "USD",
                    "leastMonetaryUnit": 0.0
                }
            },
            "amount": {
                "value": 0.11,
                "currency": {
                    "isoCurrencySymbol": "USD",
                    "leastMonetaryUnit": 0.0
                }
            }
        },
        {
            "from": {
                "value": 1.77,
                "currency": {
                    "isoCurrencySymbol": "USD",
                    "leastMonetaryUnit": 0.0
                }
            },
            "to": {
                "value": 1.92,
                "currency": {
                    "isoCurrencySymbol": "USD",
                    "leastMonetaryUnit": 0.0
                }
            },
            "amount": {
                "value": 0.12,
                "currency": {
                    "isoCurrencySymbol": "USD",
                    "leastMonetaryUnit": 0.0
                }
            }
        }
    ],
    "isoCurrencySymbol": "IsoCurrencySymbol",
    "id": "Brackets625",
    "descriptions": [
        {
            "culture": "en-US",
            "value": "Brackets Definition Data Brackets625"
        }
    ],
    "percents": 6.25,
    "modulo": 1,
    "tableRepeatingPatternStartsAtRow": null
}

Response  200 OK
