# Tax Brackets

The Tax Bracket tax calculation method is used to apply a complex calculation comprised of a tax rate on part of the taxable amount and a Tax Brackets table for the remaining amount.
Tax Brackets serve as cutoff levels for sales tax rates, and are required by regulation in certain US States, such as Maryland, Florida.
Tax Bracket tables are defined according to Tax Authority regulations, and contain the price increments between each cent increase in tax.

## Configuring Tax Brackets

Used to configure Tax Brackets.

Tax Bracket configuration is not part of the Base Configuration.

The following shows an example of Tax Bracket Configuration required for the flows in the Selling Services.

### Tax Bracket - Brackets Definition Data Brackets 625

**HTTP Method:**

PUT

/emerald/selling-service/selling-configuration/v1/tax-settings/brackets/Bracket625

Request

```json
{
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
```

Response  200 OK

### Configuring Tax Brackets MD 6%

**HTTP Method:**

PUT

/emerald/selling-service/selling-configuration/v1/tax-settings/brackets/MD6%

Request

```json
{
  "bracketsData": [
    {
      "from": {
        "value": 0.0,
        "currency": {
          "isoCurrencySymbol": "USD",
          "leastMonetaryUnit": 0.0
        }
      },
      "to": {
        "value": 0.19,
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
        "value": 0.2,
        "currency": {
          "isoCurrencySymbol": "USD",
          "leastMonetaryUnit": 0.0
        }
      },
      "to": {
        "value": 0.2,
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
        "value": 0.21,
        "currency": {
          "isoCurrencySymbol": "USD",
          "leastMonetaryUnit": 0.0
        }
      },
      "to": {
        "value": 0.34,
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
        "value": 0.35,
        "currency": {
          "isoCurrencySymbol": "USD",
          "leastMonetaryUnit": 0.0
        }
      },
      "to": {
        "value": 0.51,
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
        "value": 0.52,
        "currency": {
          "isoCurrencySymbol": "USD",
          "leastMonetaryUnit": 0.0
        }
      },
      "to": {
        "value": 0.84,
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
        "value": 0.85,
        "currency": {
          "isoCurrencySymbol": "USD",
          "leastMonetaryUnit": 0.0
        }
      },
      "to": {
        "value": 1.0,
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
        "value": 1.01,
        "currency": {
          "isoCurrencySymbol": "USD",
          "leastMonetaryUnit": 0.0
        }
      },
      "to": {
        "value": 1.16,
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
        "value": 1.17,
        "currency": {
          "isoCurrencySymbol": "USD",
          "leastMonetaryUnit": 0.0
        }
      },
      "to": {
        "value": 1.33,
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
        "value": 1.34,
        "currency": {
          "isoCurrencySymbol": "USD",
          "leastMonetaryUnit": 0.0
        }
      },
      "to": {
        "value": 1.5,
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
        "value": 1.51,
        "currency": {
          "isoCurrencySymbol": "USD",
          "leastMonetaryUnit": 0.0
        }
      },
      "to": {
        "value": 1.66,
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
        "value": 1.67,
        "currency": {
          "isoCurrencySymbol": "USD",
          "leastMonetaryUnit": 0.0
        }
      },
      "to": {
        "value": 1.83,
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
        "value": 1.84,
        "currency": {
          "isoCurrencySymbol": "USD",
          "leastMonetaryUnit": 0.0
        }
      },
      "to": {
        "value": 2.0,
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
    }
  ],
  "isoCurrencySymbol": "IsoCurrencySymbol",
  "id": "MD 6%",
  "descriptions": [
    {
      "culture": "en-US",
      "value": "Brackets Definition Data MD 6%"
    }
  ],
  "percents": 6.0,
  "modulo": 1,
  "tableRepeatingPatternStartsAtRow": null
}
```

### Configuring Tax Brackets FL 6%

**HTTP Method:**

PUT

/emerald/selling-service/selling-configuration/v1/tax-settings/brackets/FL6.25%

Request

```json


### Configuring Tax Brackets FL 6.25%

**HTTP Method:**

PUT

/emerald/selling-service/selling-configuration/v1/tax-settings/brackets/FL6.25%

Request

```json
{
  "bracketsData": [
    {
      "from": {
        "value": 0.0,
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
        "value": 0.8,
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
  "id": "FL 6.25%",
  "descriptions": [
    {
      "culture": "en-US",
      "value": "Brackets Definition Data FL 6.25%"
    }
  ],
  "percents": 6.25,
  "modulo": 1,
  "tableRepeatingPatternStartsAtRow": null
}
```

### Configuring Tax Brackets FL 8%

**HTTP Method:**

PUT

/emerald/selling-service/selling-configuration/v1/tax-settings/brackets/FL8%

Request

```json
{
  "bracketsData": [
    {
      "from": {
        "value": 0.0,
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
        "value": 0.12,
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
        "value": 0.13,
        "currency": {
          "isoCurrencySymbol": "USD",
          "leastMonetaryUnit": 0.0
        }
      },
      "to": {
        "value": 0.25,
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
        "value": 0.26,
        "currency": {
          "isoCurrencySymbol": "USD",
          "leastMonetaryUnit": 0.0
        }
      },
      "to": {
        "value": 0.37,
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
        "value": 0.38,
        "currency": {
          "isoCurrencySymbol": "USD",
          "leastMonetaryUnit": 0.0
        }
      },
      "to": {
        "value": 0.5,
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
        "value": 0.51,
        "currency": {
          "isoCurrencySymbol": "USD",
          "leastMonetaryUnit": 0.0
        }
      },
      "to": {
        "value": 0.62,
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
        "value": 0.63,
        "currency": {
          "isoCurrencySymbol": "USD",
          "leastMonetaryUnit": 0.0
        }
      },
      "to": {
        "value": 0.75,
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
        "value": 0.76,
        "currency": {
          "isoCurrencySymbol": "USD",
          "leastMonetaryUnit": 0.0
        }
      },
      "to": {
        "value": 0.87,
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
        "value": 0.88,
        "currency": {
          "isoCurrencySymbol": "USD",
          "leastMonetaryUnit": 0.0
        }
      },
      "to": {
        "value": 1.09,
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
    }
  ],
  "isoCurrencySymbol": "IsoCurrencySymbol",
  "id": "FL 8%",
  "descriptions": [
    {
      "culture": "en-US",
      "value": "Brackets Definition Data FL 8%"
    }
  ],
  "percents": 8.0,
  "modulo": 1,
  "tableRepeatingPatternStartsAtRow": null
}
```

### Configuring Tax Brackets 6

**HTTP Method:**

PUT

/emerald/selling-service/selling-configuration/v1/tax-settings/brackets/Brackets6

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
    "startDateTime": "2022-02-12T10:20:47.1250704",
    "endDateTime": null,
    "rateCondition": {
        "zoneId": null,
        "products": null,
        "categories": [
            {
                "categoryId": "Cheese Product Group",
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
                "to": 100.0,
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

### Configuring Tax Brackets 8

**HTTP Method:**

PUT

/emerald/selling-service/selling-configuration/v1/tax-settings/brackets/Brackets8

Request

```json

{
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
                "value": 0.12,
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
                "value": 0.13,
                "currency": {
                    "isoCurrencySymbol": "USD",
                    "leastMonetaryUnit": 0.0
                }
            },
            "to": {
                "value": 0.25,
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
                "value": 0.26,
                "currency": {
                    "isoCurrencySymbol": "USD",
                    "leastMonetaryUnit": 0.0
                }
            },
            "to": {
                "value": 0.37,
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
                "value": 0.38,
                "currency": {
                    "isoCurrencySymbol": "USD",
                    "leastMonetaryUnit": 0.0
                }
            },
            "to": {
                "value": 0.50,
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
                "value": 0.51,
                "currency": {
                    "isoCurrencySymbol": "USD",
                    "leastMonetaryUnit": 0.0
                }
            },
            "to": {
                "value": 0.62,
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
                "value": 0.63,
                "currency": {
                    "isoCurrencySymbol": "USD",
                    "leastMonetaryUnit": 0.0
                }
            },
            "to": {
                "value": 0.75,
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
                "value": 0.76,
                "currency": {
                    "isoCurrencySymbol": "USD",
                    "leastMonetaryUnit": 0.0
                }
            },
            "to": {
                "value": 0.87,
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
                "value": 0.88,
                "currency": {
                    "isoCurrencySymbol": "USD",
                    "leastMonetaryUnit": 0.0
                }
            },
            "to": {
                "value": 1.09,
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
        }
    ],
    "isoCurrencySymbol": "IsoCurrencySymbol",
    "id": "Brackets8",
    "descriptions": [
        {
            "culture": "en-US",
            "value": "Brackets Definition Data Brackets8"
        }
    ],
    "percents": 8.0,
    "modulo": 1,
    "tableRepeatingPatternStartsAtRow": null
}
```
