
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

## Add Coupon Data Patterns

**HTTP Method:**

PUT

/emerald/selling-configuration/data-pattern-settings/patterns/{dataPatternId}

### Add UPC5 Coupon Data Pattern

```json
Example 

Request
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
Response
{
   OK
}
```

### Add Databar Coupon Data Pattern

```json
Example 

Request
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
Response
{
   OK
}
```

## Add Customer Data Patterns

**HTTP Method:**

PUT

/emerald/selling-configuration/data-pattern-settings/patterns/{dataPatternId}

### Add Loyalty Customer Data Pattern

```json
Example 

Request
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
}
Response
{
   OK
}
```

## Add Transaction Data Patterns

### Add Transaction Barcode Data Pattern

```json
Example 

Request
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
Response
{
   OK
}
```

## Add Gift Receipt Data Patterns

**HTTP Method:**

PUT

/emerald/selling-configuration/data-pattern-settings/patterns/{dataPatternId}

### Add a Gift Receipt Data Pattern

```json
Example 

Request
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
Response
{
   OK
}
```

## Add Cashier Data Patterns

**HTTP Method:**

PUT

/emerald/selling-configuration/data-pattern-settings/patterns/{dataPatternId}

### Add a Cashier Barcode Data Pattern

```json
Example 

Request
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
Response
{
   OK
}
```

## Add BlindPickup Data Patterns

**HTTP Method:**

PUT

/emerald/selling-configuration/data-pattern-settings/patterns/{dataPatternId}

### Add a Blind Pickup Data Pattern

```json
Example 

Request
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
Response
{
   OK
}
```
