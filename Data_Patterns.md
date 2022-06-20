
# Data Patterns

Data patterns provide the Selling Service the ability to identify and decode barcode / QR-Code data.
For example, when Scanning an Item with a Bar-code data of "2010029020519", a predefined data pattern of 20PPPPPxCCCCz can be used to identify that this is a price embedded barcode, that the Item Id is "10029" and the price is "20.51".
Given such a data pattern, sending "2010029020519" to the Cart would result the item added to the Cart with that price.
Without the data pattern, the whole string "2010029020519" would be assumed to be an Item Code, resulting in an "Item not found" error.

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

## Item Data Patterns

### Define a data pattern to extract a 6 digit item code from a GITIN14 code with specific prefix

**HTTP Method:**

PUT

/emerald/selling-configuration/data-pattern-settings/patterns/{dataPatternId}

Request

```json
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
```

Response 200 OK

### Define a Data Pattern to extract Item Code and External Id from a custom gift card 31 digit barcode

**HTTP Method:**

PUT

/emerald/selling-configuration/data-pattern-settings/patterns/{dataPatternId}

Request

```json
{
    "decodedDataType": "Item",
    "encodingVariants": [],
    "extractors": [{
            "extractorType": "Simple",
            "decodedKey": "Code",
            "decoderName": "PositionLength",
            "extractorParameters": [{
                    "name": "Position",
                    "value": "1"
                }, {
                    "name": "Length",
                    "value": "12"
                }, {
                    "name": "StripLeadingZeros",
                    "value": "True"
                }
            ]
        }, {
            "extractorType": "Simple",
            "decodedKey": "ExternalId",
            "decoderName": "PositionLength",
            "extractorParameters": [{
                    "name": "Position",
                    "value": "16"
                }, {
                    "name": "Length",
                    "value": "16"
                }
            ]
        }
    ],
    "recognizers": [{
            "recognizerType": "PrefixLength",
            "recognizerParameters": [{
                    "name": "FromPrefix",
                    "value": "460"
                }, {
                    "name": "ToPrefix",
                    "value": "460"
                }, {
                    "name": "Length",
                    "value": "31"
                }, {
                    "name": "StripLeadingZeros",
                    "value": "True"
                }
            ]
        }
    ],
    "validators": [],
    "allowedBusinessUnits": []
}
```

Response 200 OK

### Define an EAN13 Data Pattern

**HTTP Method:**

PUT

/emerald/selling-configuration/data-pattern-settings/patterns/{dataPatternId}

Request

```json
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
```

Response 200 OK

### Define an EAN8 Data Pattern

**HTTP Method:**

PUT

/emerald/selling-configuration/data-pattern-settings/patterns/{dataPatternId}

Request

```json
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
```

Response 200 OK

### Define an Amount Embedded UPCA Data Pattern

**HTTP Method:**

PUT

/emerald/selling-configuration/data-pattern-settings/patterns/{dataPatternId}

Request

```json
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
```

Response 200 OK

### Define an Amount Embedded EAN Data Pattern

**HTTP Method:**

PUT

/emerald/selling-configuration/data-pattern-settings/patterns/{dataPatternId}

Request

```json
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
```

Response 200 OK

### Define a Pharmacy Item McKessons Data Pattern

**HTTP Method:**

PUT

/emerald/selling-configuration/data-pattern-settings/patterns/{dataPatternId}

Request

```json
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
```

Response 200 OK

## Coupon Data Patterns

### Define a UPC5 Coupon Data Pattern

**HTTP Method:**

PUT

/emerald/selling-configuration/data-pattern-settings/patterns/{dataPatternId}

Request

```json
{
  "decodedDataType": "Coupon",
  "encodingVariants": [],
  "extractors": [
    {
      "extractorType": "Simple",
      "decodedKey": "CouponPreFix",
      "decoderName": "PositionLength",
      "extractorParameters": [
        {
          "name": "Position",
          "value": "1"
        },
        {
          "name": "Length",
          "value": "1"
        }
      ]
    },
    {
      "extractorType": "Simple",
      "decodedKey": "ManufacturerNumber",
      "decoderName": "PositionLength",
      "extractorParameters": [
        {
          "name": "Position",
          "value": "2"
        },
        {
          "name": "Length",
          "value": "5"
        }
      ]
    },
    {
      "extractorType": "Simple",
      "decodedKey": "FamiliyCode",
      "decoderName": "PositionLength",
      "extractorParameters": [
        {
          "name": "Position",
          "value": "7"
        },
        {
          "name": "Length",
          "value": "3"
        }
      ]
    },
    {
      "extractorType": "Simple",
      "decodedKey": "ValueCode",
      "decoderName": "PositionLength",
      "extractorParameters": [
        {
          "name": "Position",
          "value": "10"
        },
        {
          "name": "Length",
          "value": "2"
        }
      ]
    },
    {
      "extractorType": "Simple",
      "decodedKey": "TenderId",
      "decoderName": "Fixed",
      "extractorParameters": [
        {
          "name": "FixedValue",
          "value": "60"
        }
      ]
    },
    {
      "extractorType": "Simple",
      "decodedKey": "CouponType",
      "decoderName": "Fixed",
      "extractorParameters": [
        {
          "name": "FixedValue",
          "value": "Vendor"
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
          "value": "5"
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
```

Response 200 OK

### Define a Databar Coupon Data Pattern

**HTTP Method:**

PUT

/emerald/selling-configuration/data-pattern-settings/patterns/{dataPatternId}

Request

```json
{
  "decodedDataType": "DatabarItem",
  "encodingVariants": [],
  "extractors": [],
  "recognizers": [
    {
      "recognizerType": "GS1DataBarItem",
      "decoderName": null,
      "recognizerParameters": []
    }
  ],
  "validators": [],
  "allowedBusinessUnits": [
    {
      "enterpriseUnitId": "00000000000000000000000000000000"
    }
  ]
}
```

Response 200 OK

## Customer Data Patterns

### Define a Loyalty Customer Data Pattern

**HTTP Method:**

PUT

/emerald/selling-configuration/data-pattern-settings/patterns/{dataPatternId}

Request

```json
{
  "decodedDataType": "Customer",
  "encodingVariants": [],
  "extractors": [
    {
      "extractorType": "Simple",
      "decodedKey": "LoyaltyCardId",
      "decoderName": "PositionLength",
      "extractorParameters": [
        {
          "name": "Position",
          "value": "1"
        },
        {
          "name": "Length",
          "value": "11"
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
          "value": "4"
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
```

Response 200 OK

## Transaction Data Patterns

### Define a Transaction Data Pattern

**HTTP Method:**

PUT

/emerald/selling-configuration/data-pattern-settings/patterns/{dataPatternId}

Request

```json
{
  "decodedDataType": "Transaction",
  "encodingVariants": [
    {
      "businessAction": "SaveTransaction",
      "defaultPrefix": "629"
    }
  ],
  "extractors": [
    {
      "extractorType": "Simple",
      "decodedKey": "StoreCode",
      "decoderName": "PositionLength",
      "extractorParameters": [
        {
          "name": "Position",
          "value": "4"
        },
        {
          "name": "Length",
          "value": "4"
        },
        {
          "name": "StripLeadingZeros",
          "value": "True"
        }
      ]
    },
    {
      "extractorType": "Simple",
      "decodedKey": "PosID",
      "decoderName": "PositionLength",
      "extractorParameters": [
        {
          "name": "Position",
          "value": "8"
        },
        {
          "name": "Length",
          "value": "3"
        },
        {
          "name": "StripLeadingZeros",
          "value": "True"
        }
      ]
    },
    {
      "extractorType": "Simple",
      "decodedKey": "TransactionID",
      "decoderName": "PositionLength",
      "extractorParameters": [
        {
          "name": "Position",
          "value": "11"
        },
        {
          "name": "Length",
          "value": "4"
        }
      ]
    },
    {
      "extractorType": "DateTime",
      "decodedKey": "OriginatingDate",
      "decoderName": "PositionLength",
      "extractorParameters": [
        {
          "name": "Position",
          "value": "15"
        },
        {
          "name": "Length",
          "value": "8"
        },
        {
          "name": "DateTimeFormat",
          "value": "MMddyyyy"
        },
        {
          "name": "AutocompleteDayTo",
          "value": "FirstDayOfMonth"
        },
        {
          "name": "AutocompleteMonthTo",
          "value": "FirstMonthOfYear"
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
          "name": "FixedPrefix",
          "value": "629"
        },
        {
          "name": "Length",
          "value": "22"
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
```

Response 200 OK

## Gift Receipt Data Patterns

### Define a Gift Receipt Data Pattern

**HTTP Method:**

PUT

/emerald/selling-configuration/data-pattern-settings/patterns/{dataPatternId}

Response

```json
{
  "decodedDataType": "GiftReceipt",
  "encodingVariants": [
    {
      "businessAction": "GiftReceiptItem",
      "defaultPrefix": "12"
    }
  ],
  "extractors": [
    {
      "extractorType": "Simple",
      "decodedKey": "Price",
      "decoderName": "PositionLength",
      "extractorParameters": [
        {
          "name": "Decimals",
          "value": "2"
        },
        {
          "name": "Length",
          "value": "5"
        },
        {
          "name": "Position",
          "value": "3"
        },
        {
          "name": "StripLeadingZeros",
          "value": "True"
        }
      ]
    },
    {
      "extractorType": "Simple",
      "decodedKey": "StoreCode",
      "decoderName": "PositionLength",
      "extractorParameters": [
        {
          "name": "Length",
          "value": "3"
        },
        {
          "name": "Position",
          "value": "8"
        },
        {
          "name": "StripLeadingZeros",
          "value": "True"
        }
      ]
    },
    {
      "extractorType": "Simple",
      "decodedKey": "PosID",
      "decoderName": "PositionLength",
      "extractorParameters": [
        {
          "name": "Length",
          "value": "3"
        },
        {
          "name": "Position",
          "value": "11"
        },
        {
          "name": "StripLeadingZeros",
          "value": "True"
        }
      ]
    },
    {
      "extractorType": "Simple",
      "decodedKey": "TransactionID",
      "decoderName": "PositionLength",
      "extractorParameters": [
        {
          "name": "Length",
          "value": "4"
        },
        {
          "name": "Position",
          "value": "14"
        },
        {
          "name": "StripLeadingZeros",
          "value": "True"
        }
      ]
    },
    {
      "extractorType": "DateTime",
      "decodedKey": "ExpiryDate",
      "decoderName": "PositionLength",
      "extractorParameters": [
        {
          "name": "DateTimeFormat",
          "value": "%yJJJ"
        },
        {
          "name": "Length",
          "value": "4"
        },
        {
          "name": "Position",
          "value": "18"
        }
      ]
    },
    {
      "extractorType": "DateTime",
      "decodedKey": "CloseTransactionDate",
      "decoderName": "PositionLength",
      "extractorParameters": [
        {
          "name": "DateTimeFormat",
          "value": "%yJJJ"
        },
        {
          "name": "Length",
          "value": "4"
        },
        {
          "name": "Position",
          "value": "22"
        }
      ]
    },
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
          "value": "26"
        },
        {
          "name": "Length",
          "value": "13"
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
          "value": "39"
        },
        {
          "name": "FromPrefix",
          "value": "12"
        },
        {
          "name": "ToPrefix",
          "value": "12"
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
          "value": "38"
        },
        {
          "name": "Algorithm",
          "value": "LUHN"
        },
        {
          "name": "CheckDigitPosition",
          "value": "39"
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
```

Response 200 OK

## Cashier Data Patterns

### Define a Cashier Barcode Data Pattern

**HTTP Method:**

PUT

/emerald/selling-configuration/data-pattern-settings/patterns/{dataPatternId}

Request

```json
{
  "decodedDataType": "Cashier",
  "encodingVariants": [
    {
      "businessAction": "Cashier",
      "defaultPrefix": "22500"
    }
  ],
  "extractors": [
    {
      "extractorType": "Simple",
      "decodedKey": "CashierReferenceId",
      "decoderName": "PositionLength",
      "extractorParameters": [
        {
          "name": "Position",
          "value": "6"
        },
        {
          "name": "Length",
          "value": "8"
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
          "value": "14"
        },
        {
          "name": "FixedPrefix",
          "value": "22500"
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
          "value": "13"
        },
        {
          "name": "Algorithm",
          "value": "UPC"
        },
        {
          "name": "CheckDigitPosition",
          "value": "14"
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
```

Response 200 OK

## BlindPickup Data Patterns

### Define a Blind Pickup Data Pattern

**HTTP Method:**

PUT

/emerald/selling-configuration/data-pattern-settings/patterns/{dataPatternId}

Request

```json
{
  "decodedDataType": "BlindPickup",
  "encodingVariants": [
    {
      "businessAction": "BlindPickup",
      "defaultPrefix": "98001"
    }
  ],
  "extractors": [
    {
      "extractorType": "Simple",
      "decodedKey": "BlindPickupType",
      "decoderName": "PositionLength",
      "extractorParameters": [
        {
          "name": "Position",
          "value": "6"
        },
        {
          "name": "Length",
          "value": "1"
        }
      ]
    },
    {
      "extractorType": "Simple",
      "decodedKey": "LiftNumber",
      "decoderName": "PositionLength",
      "extractorParameters": [
        {
          "name": "Position",
          "value": "7"
        },
        {
          "name": "Length",
          "value": "3"
        }
      ]
    },
    {
      "extractorType": "Simple",
      "decodedKey": "PosID",
      "decoderName": "PositionLength",
      "extractorParameters": [
        {
          "name": "Position",
          "value": "10"
        },
        {
          "name": "Length",
          "value": "3"
        }
      ]
    },
    {
      "extractorType": "DateTime",
      "decodedKey": "CreationDate",
      "decoderName": "PositionLength",
      "extractorParameters": [
        {
          "name": "Position",
          "value": "13"
        },
        {
          "name": "Length",
          "value": "10"
        },
        {
          "name": "DateTimeFormat",
          "value": "ddMMyyHHmm"
        },
        {
          "name": "AutocompleteDayTo",
          "value": "FirstDayOfMonth"
        },
        {
          "name": "AutocompleteMonthTo",
          "value": "FirstMonthOfYear"
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
          "value": "98001"
        },
        {
          "name": "ToPrefix",
          "value": "98001"
        },
        {
          "name": "Length",
          "value": "24"
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
          "value": "23"
        },
        {
          "name": "Algorithm",
          "value": "UPC"
        },
        {
          "name": "CheckDigitPosition",
          "value": "24"
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
```

Response 200 OK

## Driver License Data Pattern

### Define a Driver License Data Pattern

**HTTP Method:**

PUT

/emerald/selling-configuration/data-pattern-settings/patterns/{dataPatternId}

Request

```json
{
  "decodedDataType": "DriverLicense",
  "encodingVariants": [],
  "extractors": [],
  "recognizers": [
    {
      "recognizerType": "Regex",
      "decoderName": null,
      "recognizerParameters": [
        {
          "name": "Pattern",
          "value": "@ANSI*"
        }
      ]
    }
  ],
  "validators": [],
  "allowedBusinessUnits": []
}
```

Response 200 OK

## Tender Data Pattern

### Define a Bottle Return Data Pattern

**HTTP Method:**

PUT

/emerald/selling-configuration/data-pattern-settings/patterns/{dataPatternId}

Request

```json
{
  "decodedDataType": "Tender",
  "encodingVariants": [],
  "extractors": [
    {
      "extractorType": "Simple",
      "decodedKey": "Code",
      "decoderName": "Fixed",
      "extractorParameters": [
        {
          "name": "FixedValue",
          "value": "80"
        }
      ]
    },
    {
      "extractorType": "Simple",
      "decodedKey": "VoucherType",
      "decoderName": "Fixed",
      "extractorParameters": [
        {
          "name": "FixedValue",
          "value": "Tomra"
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
          "value": "14"
        },
        {
          "name": "FixedPrefix",
          "value": "B"
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
```

Response 200 OK

## Get Data Patterns

To retrieve data patterns by a specific ID, or by the Type of entity the data pattern matches.

### Retrieve a Item Data Pattern by Single ID (EAN13)

**HTTP Method:**

GET

/emerald/selling-service/c1/selling-configuration/data-pattern-settings/patterns/{dataPatternId}

Response

```json
{
    "dataPatternId": "EAN13",
    "decodedDataType": "Item",
    "description": null,
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
```

### Search for Item Data Pattern by Search Criteria

Search by the type of entity the data pattern matches.

Available values : Item, Tender, Customer, CustomerAltAndPIN, EndOfTrip, Cradle, DatabarItem, DriverLicense, WarmReboot, ReleaseDevice, Coupon, Transaction, GiftReceipt, BlindPickup, OnlineServicesProfile, Group, Cashier, IMEI, OrderServiceTransaction, UserCredentials

For example:

/emerald/selling-service/c1/selling-configuration/data-pattern-settings/patterns/DriverLicense

**HTTP Method:**

GET

/emerald/selling-service/c1/selling-configuration/data-pattern-settings/patterns/effective-patterns

Response

```json
{
    "dataPatternId": "DriverLicense",
    "decodedDataType": "DriverLicense",
    "description": null,
    "encodingVariants": [],
    "extractors": [],
    "recognizers": [
        {
            "recognizerType": "Regex",
            "decoderName": null,
            "recognizerParameters": [
                {
                    "name": "Pattern",
                    "value": "@ANSI*"
                }
            ]
        }
    ],
    "validators": [],
    "allowedBusinessUnits": []
}
```

### Retrieve all the Data Patterns Configured in the System

**HTTP Method:**

GET

/emerald/selling-service/c1/selling-configuration/data-pattern-settings/patterns

Response

```json
{
    "lastPage": true,
    "pageNumber": 0,
    "totalPages": 1,
    "totalResults": 23,
    "pageContent": [
        {
            "dataPatternId": "AmountEmbedded",
            "decodedDataType": "Item",
            "description": null,
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
        },
        {
            "dataPatternId": "AmountEmbeddedUPCA",
            "decodedDataType": "Item",
            "description": null,
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
        },
        {
            "dataPatternId": "EAN13",
            "decodedDataType": "Item",
            "description": null,
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
        },
        {
            "dataPatternId": "AmountEmbeddedEAN",
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
        },
        {
            "dataPatternId": "EAN8",
            "decodedDataType": "Item",
            "description": null,
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
        },
        {
            "dataPatternId": "DataBarCoupon",
            "decodedDataType": "DatabarItem",
            "description": null,
            "encodingVariants": [],
            "extractors": [],
            "recognizers": [
                {
                    "recognizerType": "GS1DataBarItem",
                    "decoderName": null,
                    "recognizerParameters": []
                }
            ],
            "validators": [],
            "allowedBusinessUnits": [
                {
                    "enterpriseUnitId": "00000000000000000000000000000000"
                }
            ]
        },
        {
            "dataPatternId": "DriverLicense",
            "decodedDataType": "DriverLicense",
            "description": null,
            "encodingVariants": [],
            "extractors": [],
            "recognizers": [
                {
                    "recognizerType": "Regex",
                    "decoderName": null,
                    "recognizerParameters": [
                        {
                            "name": "Pattern",
                            "value": "@ANSI*"
                        }
                    ]
                }
            ],
            "validators": [],
            "allowedBusinessUnits": []
        },
        {
            "dataPatternId": "AmountEmbeddedEAN13",
            "decodedDataType": "Item",
            "description": null,
            "encodingVariants": [],
            "extractors": [
                {
                    "extractorType": "Manipulated",
                    "decodedKey": "Code",
                    "decoderName": "PositionLength",
                    "extractorParameters": [
                        {
                            "name": "Position",
                            "value": "2"
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
                    "decoderName": null,
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
        },
        {
            "dataPatternId": "BlackhawkGiftCard",
            "decodedDataType": "Item",
            "description": null,
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
                        }
                    ]
                },
                {
                    "extractorType": "Simple",
                    "decodedKey": "ExternalId",
                    "decoderName": "PositionLength",
                    "extractorParameters": [
                        {
                            "name": "Position",
                            "value": "12"
                        },
                        {
                            "name": "Length",
                            "value": "19"
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
                            "value": "30"
                        },
                        {
                            "name": "FromPrefix",
                            "value": "076"
                        },
                        {
                            "name": "ToPrefix",
                            "value": "076"
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
        },
        {
            "dataPatternId": "BlindPickup",
            "decodedDataType": "BlindPickup",
            "description": null,
            "encodingVariants": [
                {
                    "businessAction": "BlindPickup",
                    "defaultPrefix": "98001"
                }
            ],
            "extractors": [
                {
                    "extractorType": "Simple",
                    "decodedKey": "BlindPickupType",
                    "decoderName": "PositionLength",
                    "extractorParameters": [
                        {
                            "name": "Position",
                            "value": "6"
                        },
                        {
                            "name": "Length",
                            "value": "1"
                        }
                    ]
                },
                {
                    "extractorType": "Simple",
                    "decodedKey": "LiftNumber",
                    "decoderName": "PositionLength",
                    "extractorParameters": [
                        {
                            "name": "Position",
                            "value": "7"
                        },
                        {
                            "name": "Length",
                            "value": "3"
                        }
                    ]
                },
                {
                    "extractorType": "Simple",
                    "decodedKey": "PosID",
                    "decoderName": "PositionLength",
                    "extractorParameters": [
                        {
                            "name": "Position",
                            "value": "10"
                        },
                        {
                            "name": "Length",
                            "value": "3"
                        }
                    ]
                },
                {
                    "extractorType": "DateTime",
                    "decodedKey": "CreationDate",
                    "decoderName": "PositionLength",
                    "extractorParameters": [
                        {
                            "name": "Position",
                            "value": "13"
                        },
                        {
                            "name": "Length",
                            "value": "10"
                        },
                        {
                            "name": "DateTimeFormat",
                            "value": "ddMMyyHHmm"
                        },
                        {
                            "name": "AutocompleteDayTo",
                            "value": "FirstDayOfMonth"
                        },
                        {
                            "name": "AutocompleteMonthTo",
                            "value": "FirstMonthOfYear"
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
                            "value": "98001"
                        },
                        {
                            "name": "ToPrefix",
                            "value": "98001"
                        },
                        {
                            "name": "Length",
                            "value": "24"
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
                            "value": "23"
                        },
                        {
                            "name": "Algorithm",
                            "value": "UPC"
                        },
                        {
                            "name": "CheckDigitPosition",
                            "value": "24"
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
        },
        {
            "dataPatternId": "BottleReturn",
            "decodedDataType": "Tender",
            "description": null,
            "encodingVariants": [],
            "extractors": [
                {
                    "extractorType": "Simple",
                    "decodedKey": "Code",
                    "decoderName": "Fixed",
                    "extractorParameters": [
                        {
                            "name": "FixedValue",
                            "value": "80"
                        }
                    ]
                },
                {
                    "extractorType": "Simple",
                    "decodedKey": "VoucherType",
                    "decoderName": "Fixed",
                    "extractorParameters": [
                        {
                            "name": "FixedValue",
                            "value": "Tomra"
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
                            "value": "14"
                        },
                        {
                            "name": "FixedPrefix",
                            "value": "B"
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
        },
        {
            "dataPatternId": "Cashier_Barcode",
            "decodedDataType": "Cashier",
            "description": null,
            "encodingVariants": [
                {
                    "businessAction": "Cashier",
                    "defaultPrefix": "22500"
                }
            ],
            "extractors": [
                {
                    "extractorType": "Simple",
                    "decodedKey": "CashierReferenceId",
                    "decoderName": "PositionLength",
                    "extractorParameters": [
                        {
                            "name": "Position",
                            "value": "6"
                        },
                        {
                            "name": "Length",
                            "value": "8"
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
                            "value": "14"
                        },
                        {
                            "name": "FixedPrefix",
                            "value": "22500"
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
                            "value": "13"
                        },
                        {
                            "name": "Algorithm",
                            "value": "UPC"
                        },
                        {
                            "name": "CheckDigitPosition",
                            "value": "14"
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
        },
        {
            "dataPatternId": "Coinstar",
            "decodedDataType": "Tender",
            "description": null,
            "encodingVariants": [],
            "extractors": [
                {
                    "extractorType": "Simple",
                    "decodedKey": "Code",
                    "decoderName": "Fixed",
                    "extractorParameters": [
                        {
                            "name": "FixedValue",
                            "value": "81"
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
                    "decoderName": null,
                    "recognizerParameters": [
                        {
                            "name": "Length",
                            "value": "13"
                        },
                        {
                            "name": "FixedPrefix",
                            "value": "27"
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
        },
        {
            "dataPatternId": "Coupon_DataBar",
            "decodedDataType": "Coupon",
            "description": null,
            "encodingVariants": [],
            "extractors": [
                {
                    "extractorType": "Simple",
                    "decodedKey": "CouponPreFix",
                    "decoderName": "PositionLength",
                    "extractorParameters": [
                        {
                            "name": "Position",
                            "value": "1"
                        },
                        {
                            "name": "Length",
                            "value": "4"
                        }
                    ]
                },
                {
                    "extractorType": "Simple",
                    "decodedKey": "CouponType",
                    "decoderName": "Fixed",
                    "extractorParameters": [
                        {
                            "name": "FixedValue",
                            "value": "DataBar"
                        }
                    ]
                },
                {
                    "extractorType": "Simple",
                    "decodedKey": "TenderId",
                    "decoderName": "Fixed",
                    "extractorParameters": [
                        {
                            "name": "FixedValue",
                            "value": "60"
                        }
                    ]
                }
            ],
            "recognizers": [
                {
                    "recognizerType": "Regex",
                    "decoderName": null,
                    "recognizerParameters": [
                        {
                            "name": "Pattern",
                            "value": "8110\\d{22,}"
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
        },
        {
            "dataPatternId": "GiftReceipt",
            "decodedDataType": "GiftReceipt",
            "description": null,
            "encodingVariants": [
                {
                    "businessAction": "GiftReceiptItem",
                    "defaultPrefix": "12"
                }
            ],
            "extractors": [
                {
                    "extractorType": "Simple",
                    "decodedKey": "Price",
                    "decoderName": "PositionLength",
                    "extractorParameters": [
                        {
                            "name": "Decimals",
                            "value": "2"
                        },
                        {
                            "name": "Length",
                            "value": "5"
                        },
                        {
                            "name": "Position",
                            "value": "3"
                        },
                        {
                            "name": "StripLeadingZeros",
                            "value": "True"
                        }
                    ]
                },
                {
                    "extractorType": "Simple",
                    "decodedKey": "StoreCode",
                    "decoderName": "PositionLength",
                    "extractorParameters": [
                        {
                            "name": "Length",
                            "value": "3"
                        },
                        {
                            "name": "Position",
                            "value": "8"
                        },
                        {
                            "name": "StripLeadingZeros",
                            "value": "True"
                        }
                    ]
                },
                {
                    "extractorType": "Simple",
                    "decodedKey": "PosID",
                    "decoderName": "PositionLength",
                    "extractorParameters": [
                        {
                            "name": "Length",
                            "value": "3"
                        },
                        {
                            "name": "Position",
                            "value": "11"
                        },
                        {
                            "name": "StripLeadingZeros",
                            "value": "True"
                        }
                    ]
                },
                {
                    "extractorType": "Simple",
                    "decodedKey": "TransactionID",
                    "decoderName": "PositionLength",
                    "extractorParameters": [
                        {
                            "name": "Length",
                            "value": "4"
                        },
                        {
                            "name": "Position",
                            "value": "14"
                        },
                        {
                            "name": "StripLeadingZeros",
                            "value": "True"
                        }
                    ]
                },
                {
                    "extractorType": "DateTime",
                    "decodedKey": "ExpiryDate",
                    "decoderName": "PositionLength",
                    "extractorParameters": [
                        {
                            "name": "DateTimeFormat",
                            "value": "%yJJJ"
                        },
                        {
                            "name": "Length",
                            "value": "4"
                        },
                        {
                            "name": "Position",
                            "value": "18"
                        }
                    ]
                },
                {
                    "extractorType": "DateTime",
                    "decodedKey": "CloseTransactionDate",
                    "decoderName": "PositionLength",
                    "extractorParameters": [
                        {
                            "name": "DateTimeFormat",
                            "value": "%yJJJ"
                        },
                        {
                            "name": "Length",
                            "value": "4"
                        },
                        {
                            "name": "Position",
                            "value": "22"
                        }
                    ]
                },
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
                            "value": "26"
                        },
                        {
                            "name": "Length",
                            "value": "13"
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
                            "value": "39"
                        },
                        {
                            "name": "FromPrefix",
                            "value": "12"
                        },
                        {
                            "name": "ToPrefix",
                            "value": "12"
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
                            "value": "38"
                        },
                        {
                            "name": "Algorithm",
                            "value": "LUHN"
                        },
                        {
                            "name": "CheckDigitPosition",
                            "value": "39"
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
        },
        {
            "dataPatternId": "Coupon_UPC",
            "decodedDataType": "Coupon",
            "description": null,
            "encodingVariants": [],
            "extractors": [
                {
                    "extractorType": "Simple",
                    "decodedKey": "CouponPreFix",
                    "decoderName": "PositionLength",
                    "extractorParameters": [
                        {
                            "name": "Position",
                            "value": "1"
                        },
                        {
                            "name": "Length",
                            "value": "1"
                        }
                    ]
                },
                {
                    "extractorType": "Simple",
                    "decodedKey": "ManufacturerNumber",
                    "decoderName": "PositionLength",
                    "extractorParameters": [
                        {
                            "name": "Position",
                            "value": "2"
                        },
                        {
                            "name": "Length",
                            "value": "5"
                        }
                    ]
                },
                {
                    "extractorType": "Simple",
                    "decodedKey": "FamiliyCode",
                    "decoderName": "PositionLength",
                    "extractorParameters": [
                        {
                            "name": "Position",
                            "value": "7"
                        },
                        {
                            "name": "Length",
                            "value": "3"
                        }
                    ]
                },
                {
                    "extractorType": "Simple",
                    "decodedKey": "ValueCode",
                    "decoderName": "PositionLength",
                    "extractorParameters": [
                        {
                            "name": "Position",
                            "value": "10"
                        },
                        {
                            "name": "Length",
                            "value": "2"
                        }
                    ]
                },
                {
                    "extractorType": "Simple",
                    "decodedKey": "TenderId",
                    "decoderName": "Fixed",
                    "extractorParameters": [
                        {
                            "name": "FixedValue",
                            "value": "60"
                        }
                    ]
                },
                {
                    "extractorType": "Simple",
                    "decodedKey": "CouponType",
                    "decoderName": "Fixed",
                    "extractorParameters": [
                        {
                            "name": "FixedValue",
                            "value": "Vendor"
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
                            "value": "5"
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
        },
        {
            "dataPatternId": "DataBarItem",
            "decodedDataType": "DatabarItem",
            "description": null,
            "encodingVariants": [],
            "extractors": [],
            "recognizers": [
                {
                    "recognizerType": "GS1DataBarItem",
                    "decoderName": null,
                    "recognizerParameters": []
                }
            ],
            "validators": [],
            "allowedBusinessUnits": [
                {
                    "enterpriseUnitId": "00000000000000000000000000000000"
                }
            ]
        },
        {
            "dataPatternId": "GiftReceiptBarcode",
            "decodedDataType": "GiftReceipt",
            "description": null,
            "encodingVariants": [
                {
                    "businessAction": "GiftReceiptItem",
                    "defaultPrefix": "12"
                }
            ],
            "extractors": [
                {
                    "extractorType": "Simple",
                    "decodedKey": "Price",
                    "decoderName": "PositionLength",
                    "extractorParameters": [
                        {
                            "name": "Decimals",
                            "value": "2"
                        },
                        {
                            "name": "Length",
                            "value": "5"
                        },
                        {
                            "name": "Position",
                            "value": "3"
                        },
                        {
                            "name": "StripLeadingZeros",
                            "value": "True"
                        }
                    ]
                },
                {
                    "extractorType": "Simple",
                    "decodedKey": "StoreCode",
                    "decoderName": "PositionLength",
                    "extractorParameters": [
                        {
                            "name": "Length",
                            "value": "3"
                        },
                        {
                            "name": "Position",
                            "value": "8"
                        },
                        {
                            "name": "StripLeadingZeros",
                            "value": "True"
                        }
                    ]
                },
                {
                    "extractorType": "Simple",
                    "decodedKey": "PosID",
                    "decoderName": "PositionLength",
                    "extractorParameters": [
                        {
                            "name": "Length",
                            "value": "3"
                        },
                        {
                            "name": "Position",
                            "value": "11"
                        },
                        {
                            "name": "StripLeadingZeros",
                            "value": "True"
                        }
                    ]
                },
                {
                    "extractorType": "Simple",
                    "decodedKey": "TransactionID",
                    "decoderName": "PositionLength",
                    "extractorParameters": [
                        {
                            "name": "Length",
                            "value": "4"
                        },
                        {
                            "name": "Position",
                            "value": "14"
                        },
                        {
                            "name": "StripLeadingZeros",
                            "value": "True"
                        }
                    ]
                },
                {
                    "extractorType": "DateTime",
                    "decodedKey": "ExpiryDate",
                    "decoderName": "PositionLength",
                    "extractorParameters": [
                        {
                            "name": "DateTimeFormat",
                            "value": "%yJJJ"
                        },
                        {
                            "name": "Length",
                            "value": "4"
                        },
                        {
                            "name": "Position",
                            "value": "18"
                        }
                    ]
                },
                {
                    "extractorType": "DateTime",
                    "decodedKey": "CloseTransactionDate",
                    "decoderName": "PositionLength",
                    "extractorParameters": [
                        {
                            "name": "DateTimeFormat",
                            "value": "%yJJJ"
                        },
                        {
                            "name": "Length",
                            "value": "4"
                        },
                        {
                            "name": "Position",
                            "value": "22"
                        }
                    ]
                },
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
                            "value": "26"
                        },
                        {
                            "name": "Length",
                            "value": "13"
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
                            "value": "39"
                        },
                        {
                            "name": "FromPrefix",
                            "value": "12"
                        },
                        {
                            "name": "ToPrefix",
                            "value": "12"
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
                            "value": "38"
                        },
                        {
                            "name": "Algorithm",
                            "value": "LUHN"
                        },
                        {
                            "name": "CheckDigitPosition",
                            "value": "39"
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
        },
        {
            "dataPatternId": "Loyality_Card",
            "decodedDataType": "Customer",
            "description": null,
            "encodingVariants": [],
            "extractors": [
                {
                    "extractorType": "Simple",
                    "decodedKey": "LoyaltyCardId",
                    "decoderName": "PositionLength",
                    "extractorParameters": [
                        {
                            "name": "Position",
                            "value": "1"
                        },
                        {
                            "name": "Length",
                            "value": "11"
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
                            "value": "4"
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
        },
        {
            "dataPatternId": "Pharmacy_McKessonRxBarcode",
            "decodedDataType": "Item",
            "description": null,
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
        },
        {
            "dataPatternId": "RDP_OrderTransaction",
            "decodedDataType": "OrderServiceTransaction",
            "description": null,
            "encodingVariants": [
                {
                    "businessAction": "SaveOrder",
                    "defaultPrefix": "91"
                }
            ],
            "extractors": [
                {
                    "extractorType": "Simple",
                    "decodedKey": "Type",
                    "decoderName": "PositionLength",
                    "extractorParameters": [
                        {
                            "name": "Position",
                            "value": "1"
                        },
                        {
                            "name": "Length",
                            "value": "2"
                        }
                    ]
                },
                {
                    "extractorType": "Simple",
                    "decodedKey": "OrderNumber",
                    "decoderName": "PositionLength",
                    "extractorParameters": [
                        {
                            "name": "Position",
                            "value": "3"
                        },
                        {
                            "name": "Length",
                            "value": "20"
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
                            "name": "FixedPrefix",
                            "value": "91"
                        },
                        {
                            "name": "Length",
                            "value": "22"
                        }
                    ]
                }
            ],
            "validators": [],
            "allowedBusinessUnits": []
        },
        {
            "dataPatternId": "Transaction_Barcode",
            "decodedDataType": "Transaction",
            "description": null,
            "encodingVariants": [
                {
                    "businessAction": "SaveTransaction",
                    "defaultPrefix": "629"
                }
            ],
            "extractors": [
                {
                    "extractorType": "Simple",
                    "decodedKey": "StoreCode",
                    "decoderName": "PositionLength",
                    "extractorParameters": [
                        {
                            "name": "Position",
                            "value": "4"
                        },
                        {
                            "name": "Length",
                            "value": "4"
                        },
                        {
                            "name": "StripLeadingZeros",
                            "value": "True"
                        }
                    ]
                },
                {
                    "extractorType": "Simple",
                    "decodedKey": "PosID",
                    "decoderName": "PositionLength",
                    "extractorParameters": [
                        {
                            "name": "Position",
                            "value": "8"
                        },
                        {
                            "name": "Length",
                            "value": "3"
                        },
                        {
                            "name": "StripLeadingZeros",
                            "value": "True"
                        }
                    ]
                },
                {
                    "extractorType": "Simple",
                    "decodedKey": "TransactionID",
                    "decoderName": "PositionLength",
                    "extractorParameters": [
                        {
                            "name": "Position",
                            "value": "11"
                        },
                        {
                            "name": "Length",
                            "value": "4"
                        }
                    ]
                },
                {
                    "extractorType": "DateTime",
                    "decodedKey": "OriginatingDate",
                    "decoderName": "PositionLength",
                    "extractorParameters": [
                        {
                            "name": "Position",
                            "value": "15"
                        },
                        {
                            "name": "Length",
                            "value": "8"
                        },
                        {
                            "name": "DateTimeFormat",
                            "value": "MMddyyyy"
                        },
                        {
                            "name": "AutocompleteDayTo",
                            "value": "FirstDayOfMonth"
                        },
                        {
                            "name": "AutocompleteMonthTo",
                            "value": "FirstMonthOfYear"
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
                            "name": "FixedPrefix",
                            "value": "629"
                        },
                        {
                            "name": "Length",
                            "value": "22"
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
        },
        {
            "dataPatternId": "UPCA",
            "decodedDataType": "Item",
            "description": null,
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
    ]
}
```
