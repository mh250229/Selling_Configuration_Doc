
# Data Patterns

Defines how scanned barcode data is decomposed to fields on added items.
The following barcodes are supported:

* Item
* Coupon
* Customer

**HTTP Methods:**

* PUT
* GET
* POST
* DELETE

The following examples show adding different types of Data Patterns.

## Add Item Data Patterns

**HTTP Method:**

PUT

/emerald/selling-configuration/data-pattern-settings/patterns/{dataPatternId}

```json
Example 
Define a data pattern to extract a 6 digit item code from a GITIN14 code with specific prefix

Request
{
            "decodedDataType": "Item",
            "encodingVariants": [],
            "extractors": [
                {
                    "extractorType": "Simple",
                    "decodedKey": "Code",
                    "decoderName": "PositionLength",
                    "extractorParameters": [
                        {
                            "name": "Position",
                            "value": "8"
                        },
                        {
                            "name": "Length",
                            "value": "6"
                        }
                    ]
                }
            ],
            "recognizers": [
                {
                    "recognizerType": "PrefixLength",
                    "decoderName": null,
                    "recognizerParameters": [
                        {
                            "name": "FromPrefix",
                            "value": "450"
                        },
                        {
                            "name": "ToPrefix",
                            "value": "460"
                        },
                        {
                            "name": "Length",
                            "value": "14"
                        }
                    ]
                }
            ],
            "validators": [],
            "allowedBusinessUnits": []
        }


Response
{
   OK
}
```

### EAN13 Data Pattern

```json
Example 

Request
{
  "decodedDataType": "Item",
  "encodingVariants": [],
  "extractors": [
    {
      "extractorType": "Simple",
      "decodedKey": "Code",
      "decoderName": "PositionLength",
      "extractorParameters": [
        {
          "name": "StripLeadingZeros",
          "value": "True"
        },
        {
          "name": "Position",
          "value": "1"
        },
        {
          "name": "Length",
          "value": "12"
        }
      ]
    }
  ],
  "recognizers": [
    {
      "recognizerType": "PrefixLength",
      "decoderName": null,
      "recognizerParameters": [
        {
          "name": "Length",
          "value": "13"
        },
        {
          "name": "FromPrefix",
          "value": "00"
        },
        {
          "name": "ToPrefix",
          "value": "01"
        }
      ]
    },
    {
      "recognizerType": "PrefixLength",
      "decoderName": null,
      "recognizerParameters": [
        {
          "name": "Length",
          "value": "13"
        },
        {
          "name": "FromPrefix",
          "value": "03"
        },
        {
          "name": "ToPrefix",
          "value": "19"
        }
      ]
    },
    {
      "recognizerType": "PrefixLength",
      "decoderName": null,
      "recognizerParameters": [
        {
          "name": "Length",
          "value": "13"
        },
        {
          "name": "FromPrefix",
          "value": "30"
        },
        {
          "name": "ToPrefix",
          "value": "97"
        }
      ]
    }
  ],
  "validators": [
    {
      "validatorType": "CheckDigit",
      "validatorDecoderName": "PositionLength",
      "validatorParameters": [
        {
          "name": "Position",
          "value": "1"
        },
        {
          "name": "Length",
          "value": "12"
        },
        {
          "name": "Algorithm",
          "value": "UPC"
        },
        {
          "name": "CheckDigitPosition",
          "value": "13"
        },
        {
          "name": "CheckDigitLength",
          "value": "1"
        }
      ]
    }
  ],
  "allowedBusinessUnits": [
    {
      "enterpriseUnitId": "00000000000000000000000000000000"
    }
  ]
}
Response
{
   OK
}
```

### EAN8 Data Pattern

```json
Example 

Request
{
  "decodedDataType": "Item",
  "encodingVariants": [],
  "extractors": [
    {
      "extractorType": "Simple",
      "decodedKey": "Code",
      "decoderName": "PositionLength",
      "extractorParameters": [
        {
          "name": "StripLeadingZeros",
          "value": "True"
        },
        {
          "name": "Position",
          "value": "1"
        },
        {
          "name": "Length",
          "value": "7"
        }
      ]
    }
  ],
  "recognizers": [
    {
      "recognizerType": "PrefixLength",
      "decoderName": null,
      "recognizerParameters": [
        {
          "name": "Length",
          "value": "8"
        },
        {
          "name": "FromPrefix",
          "value": "0"
        },
        {
          "name": "ToPrefix",
          "value": "9"
        }
      ]
    }
  ],
  "validators": [
    {
      "validatorType": "CheckDigit",
      "validatorDecoderName": "PositionLength",
      "validatorParameters": [
        {
          "name": "Position",
          "value": "1"
        },
        {
          "name": "Length",
          "value": "7"
        },
        {
          "name": "Algorithm",
          "value": "UPC"
        },
        {
          "name": "CheckDigitPosition",
          "value": "8"
        },
        {
          "name": "CheckDigitLength",
          "value": "1"
        }
      ]
    }
  ],
  "allowedBusinessUnits": [
    {
      "enterpriseUnitId": "00000000000000000000000000000000"
    }
  ]
}
Response
{
   OK
}
```

### Amount Embedded UPCA Data Pattern

```json
Example 

Request
{
  "decodedDataType": "Item",
  "encodingVariants": [],
  "extractors": [
    {
      "extractorType": "Simple",
      "decodedKey": "Code",
      "decoderName": "PositionLength",
      "extractorParameters": [
        {
          "name": "Position",
          "value": "1"
        },
        {
          "name": "Length",
          "value": "11"
        },
        {
          "name": "StripLeadingZeros",
          "value": "True"
        }
      ]
    }
  ],
  "recognizers": [
    {
      "recognizerType": "PrefixLength",
      "decoderName": null,
      "recognizerParameters": [
        {
          "name": "Length",
          "value": "12"
        },
        {
          "name": "FixedPrefix",
          "value": "0"
        }
      ]
    },
    {
      "recognizerType": "PrefixLength",
      "decoderName": null,
      "recognizerParameters": [
        {
          "name": "Length",
          "value": "12"
        },
        {
          "name": "FixedPrefix",
          "value": "1"
        }
      ]
    },
    {
      "recognizerType": "PrefixLength",
      "decoderName": null,
      "recognizerParameters": [
        {
          "name": "Length",
          "value": "12"
        },
        {
          "name": "FixedPrefix",
          "value": "3"
        }
      ]
    },
    {
      "recognizerType": "PrefixLength",
      "decoderName": null,
      "recognizerParameters": [
        {
          "name": "Length",
          "value": "12"
        },
        {
          "name": "FromPrefix",
          "value": "6"
        },
        {
          "name": "ToPrefix",
          "value": "8"
        }
      ]
    }
  ],
  "validators": [
    {
      "validatorType": "CheckDigit",
      "validatorDecoderName": "PositionLength",
      "validatorParameters": [
        {
          "name": "Position",
          "value": "1"
        },
        {
          "name": "Length",
          "value": "11"
        },
        {
          "name": "Algorithm",
          "value": "UPC"
        },
        {
          "name": "CheckDigitPosition",
          "value": "12"
        },
        {
          "name": "CheckDigitLength",
          "value": "1"
        }
      ]
    }
  ],
  "allowedBusinessUnits": [
    {
      "enterpriseUnitId": "00000000000000000000000000000000"
    }
  ]
}
Response
{
   OK
}
```

### Amount Embedded EAN Data Pattern

```json
Example 

Request
{
    "decodedDataType": "Item",
    "description": "Amount_Embedded",
    "encodingVariants": [
        {
            "businessAction": "String",
            "defaultPrefix": "String"
        }
    ],
    "extractors": [
        {
            "extractorType": "Manipulated",
            "decodedKey": "Code",
            "decoderName": "PositionLength",
            "extractorParameters": [
                {
                    "name": "Position",
                    "value": "1"
                },
                {
                    "name": "Length",
                    "value": "6"
                },
                {
                    "name": "Suffix",
                    "value": "00000"
                }
            ]
        },
        {
      "extractorType": "Simple",
      "decodedKey": "Amount",
      "decoderName": "PositionLength",
      "extractorParameters": [
        {
          "name": "Position",
          "value": "8"
        },
        {
          "name": "Length",
          "value": "5"
        },
        {
          "name": "Decimals",
          "value": "2"
        }
      ]
    }
    ],
    "recognizers": [
        {
            "recognizerType": "PrefixLength",
            "decoderName": "null",
            "recognizerParameters": [
                {
                    "name": "Length",
                    "value": "13"
                },
                {
                    "name": "FixedPrefix",
                    "value": "02"
                }
            ]
        }
    ],
    "validators": [
        {
            "validatorType": "CheckDigit",
            "validatorDecoderName": "PositionLength",
            "validatorParameters": [
                {
                    "name": "Position",
                    "value": "1"
                },
               {
                   "name": "Length",
                   "value": "12"
               },
               {
                   "name": "Algorithm",
                   "value": "UPC"
               },
               {
                  "name": "CheckDigitPosition",
                  "value": "12"
              },
              {
                  "name": "CheckDigitLength",
                  "value": "1"
              }
            ]
        }
    ],
    "allowedBusinessUnits": [
        {
            "enterpriseUnitId": "00000000000000000000000000000000"
        }
    ]
}
Response
{
   OK
}
```

### Pharmacy Item McKessons Data Pattern

```json
Example 

Request
{
  "decodedDataType": "Item",
  "encodingVariants": [],
  "extractors": [
    {
      "extractorType": "Simple",
      "decodedKey": "Code",
      "decoderName": "Fixed",
      "extractorParameters": [
        {
          "name": "FixedValue",
          "value": "Rx"
        }
      ]
    },
    {
      "extractorType": "Simple",
      "decodedKey": "RxNumber",
      "decoderName": "PositionLength",
      "extractorParameters": [
        {
          "name": "Position",
          "value": "3"
        },
        {
          "name": "Length",
          "value": "8"
        }
      ]
    },
    {
      "extractorType": "Simple",
      "decodedKey": "RxFillNumber",
      "decoderName": "PositionLength",
      "extractorParameters": [
        {
          "name": "Position",
          "value": "11"
        },
        {
          "name": "Length",
          "value": "2"
        }
      ]
    },
    {
      "extractorType": "Simple",
      "decodedKey": "RxPartialFillSequence",
      "decoderName": "PositionLength",
      "extractorParameters": [
        {
          "name": "Position",
          "value": "13"
        },
        {
          "name": "Length",
          "value": "2"
        }
      ]
    },
    {
      "extractorType": "Simple",
      "decodedKey": "RxPatientCopay",
      "decoderName": "PositionLength",
      "extractorParameters": [
        {
          "name": "Position",
          "value": "18"
        },
        {
          "name": "Length",
          "value": "7"
        },
        {
          "name": "Decimals",
          "value": "2"
        }
      ]
    }
  ],
  "recognizers": [
    {
      "recognizerType": "PrefixLength",
      "decoderName": null,
      "recognizerParameters": [
        {
          "name": "Length",
          "value": "24"
        },
        {
          "name": "FixedPrefix",
          "value": "92"
        }
      ]
    }
  ],
  "validators": [],
  "allowedBusinessUnits": [
    {
      "enterpriseUnitId": "00000000000000000000000000000000"
    }
  ]
}
Response
{
   OK
}
```
