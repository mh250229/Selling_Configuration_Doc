
# Tender Types

Tender types resources define the payment means (Cash, CreditDebit, Voucher etc.) that can be used to Tender a Cart and their respective restrictions and validations.
The resource Tender Id is a mandatory parameter when adding tender to a Cart.

The following tender types are supported:

*  Cash
*  Check
*  EFT Credit/Debit
*  Gift Card

**HTTP Methods:**

*  PUT - Save or update a Tender
*  GET -  Get all Tenders
*  GET -  Get a Single Tender single by Given Tender ID
*  Delete - Delete Single Tender Rate by Tender ID

## Add Cash Tender
Add a cash tender, define the payment and change options.
The {tenderId} is the ID of the tender, e.g., 1 or Cash, etc.

**HTTP Method:**

PUT
/emerald/selling-service/c1/selling-configuration/tender-settings/tender-types/{tenderId}

```json

Request
{
   "tenderType": "Cash",
  "descriptions": [
    {
      "culture": "en-us",
      "value": "Cash"
    }
  ],
  "validators": [
    "string"
  ],
  "checkValidatorName": Name,
  "currency": "USD",
  "manualEntry": false,
  "isProcessedByEps": false,
  "isEcc": false,
  "alternateTenderId": "23",
  "isUniquelyIdentifiable": false,
  "check21ValidationEnabled": false,
  "isBottleDepositVoucher": false,
  "tenderReferences": [
  ],
  "isLoyaltyRequired": false,
  "loyaltySVAccountType": null

}

Response
{
   OK
}
```

### Payment Options

Define Options for Tender Type, per Enterprise Units and Touchpoint Group (Optional).
Each Tender Type can have a separate sub resource defining options for it per  the Enterprise Unit.

**HTTP Method:**

PUT
/emerald/selling-service/c1/selling-configuration/tender-settings/tender-types/{tenderId}/payment-options

The {tenderId} is the ID of the tender for which you are defining payment options.
'payment-options' is the tender definition options that you defining, e.g., amountEntryOption, suggestedAmounts, etc.

/emerald/selling-configuration/tender-settings/tender-types/{tenderId}/payment-options

```json
Request
{
    "amountEntryOption": [
    {
      "enterpriseUnitId": "00000000000000000000000000035295",
      "touchPointGroupId": "Default",
      "value": "YesWithoutDefault"
    }
  ],
  "suggestedAmounts": [
    {
      "enterpriseUnitId": "00000000000000000000000000035295",
      "touchPointGroupId": "Default",
      "value": [
        100,
        200,
        300
      ]
    }
  ],
  "openTillDrawerOption": [
    {
      "enterpriseUnitId": "00000000000000000000000000035295",
      "touchPointGroupId": "Default",
      "value": "AlwaysOpen"
    }
  ],
  "signatureVerificationPolicy": [
    {
      "enterpriseUnitId": "00000000000000000000000000035295",
      "touchPointGroupId": "Default",
      "value": "None"
    }
  ],
  "isAutoReconcile": [
    {
      "enterpriseUnitId": "00000000000000000000000000035295",
      "touchPointGroupId": "Default",
      "value": false
    }
  ],
  "isRound": [
    {
      "enterpriseUnitId": "00000000000000000000000000035295",
      "touchPointGroupId": "Default",
      "value": true
    }
  ],
  "isProcessedByAtm": [
    {
      "enterpriseUnitId": "00000000000000000000000000035295",
      "touchPointGroupId": "Default",
      "value": false
    }
  ],
  "blockPartialPayment": [
    {
      "enterpriseUnitId": "00000000000000000000000000035295",
      "touchPointGroupId": "Default",
      "value": false
    }
  ],
  "priority": [
    {
      "enterpriseUnitId": "00000000000000000000000000035295",
      "touchPointGroupId": "Default",
      "value": 1
    }
  ],
  "check21OffLineTresholdAmount": [
    {
      "enterpriseUnitId": "00000000000000000000000000035295",
      "touchPointGroupId": "Default",
      "value": 10
    }
  ]
}
```
```json
Response
{
   OK
}
```

### Change Options

Used to define the change settings for each tender, when issuing change at the POS terminal. A change tender is the method of payment used to give change to the customer. For example, if the customer purchases an item for the value of $350.00 and pays with a Gift Card with the value of $400.00, the cashier can only give the $50.00 change with the specified change tender, e.g., Cash.


**HTTP Method:**

PUT
/emerald/selling-configuration/tender-settings/tender-types/{tenderId}/change-options

```json
Request
{
    "isConsolidateOnChange": false,
  "isAutoVoidDisabled": false,
  "changePriority": [
    {
      "enterpriseUnitId": "00000000000000000000000000035295",
      "touchPointGroupId": "Default",
      "value": 1
    }
  ],
  "changeDefinitions": [
    {
      "enterpriseUnitId": "00000000000000000000000000035295",
      "touchPointGroupId": "Default",
      "value": [
        {
          "tenderChangeId": "1",
          "upToAmount": 1500
        }
      ]
    }
  ]

}

Response
{
   OK
}
```


## Add Check Tender Type

Used to add check tender types.
The {tenderId} is the ID of the tender you are defining, e.g., 2 or Cheque, Check, etc

PUT

/emerald/selling-service/c1/selling-configuration/tender-settings/tender-types/{tenderId}

```json
Request
{
  "tenderType": "Check",
  "descriptions": [
    {
      "culture": "en-US",
      "value": "Check"
    }
  ],
  "validators": [
    "string"
  ],
  "checkValidatorName": "null",
  "currency": "USD",
  "manualEntry": false,
  "isProcessedByEps": false,
  "isEcc": false,
  "alternateTenderId": "null",
  "isUniquelyIdentifiable": false,
  "check21ValidationEnabled": false,
  "isBottleDepositVoucher": false,
  "tenderReferences": [
    "null"
  ],
  "isLoyaltyRequired": false,
  "loyaltySVAccountType": "string"
}
```

```json
Response Status OK
{
   OK
}
```

## Add EFT Credit/Debit Tender Type

Used to add EFT Credit/Debit tender types.
The {tenderId} is the ID of the tender, e.g., 3 or Visa, etc
Note the "tenderReference" array links this Tender type to the code value used by an EPS provider.

PUT

/emerald/selling-service/c1/selling-configuration/tender-settings/tender-types/{tenderId}

```json
Request
{
  "tenderType": "CreditDebit",
  "descriptions": [
    {
      "culture": "en-US",
      "value": "Visa"
    }
  ],
  "validators": [
    "string"
  ],
  "checkValidatorName": "null",
  "currency": "USD",
  "manualEntry": false,
  "isProcessedByEps": true,
  "isEcc": false,
  "alternateTenderId": "null",
  "isUniquelyIdentifiable": false,
  "check21ValidationEnabled": false,
  "isBottleDepositVoucher": false,
  "tenderReferences": [
     "VS","MC"
  ],
  "isLoyaltyRequired": false,
  "loyaltySVAccountType": "string"
}
```

```json
Response Status OK
{
   OK
}
```

## Add Gift Card Tender Type

Used to add EFT Credit/Debit tender type for Gift Cards.
Gift Cards are Credit/Debit tender types.
The {tenderId} is the ID of the tender, e.g., 4 or ITunes, etc

PUT

/emerald/selling-service/c1/selling-configuration/tender-settings/tender-types/{tenderId}

```json
Request
{
  "tenderType": "CreditDebit",
  "descriptions": [
    {
      "culture": "en-US",
      "value": "GiftCard"
    }
  ],
  "validators": [
    "string"
  ],
  "checkValidatorName": "null",
  "currency": "USD",
  "manualEntry": true,
  "isProcessedByEps": true,
  "isEcc": false,
  "alternateTenderId": "null",
  "isUniquelyIdentifiable": true,
  "check21ValidationEnabled": false,
  "isBottleDepositVoucher": false,
  "tenderReferences": [
    "GC"
  ],
  "isLoyaltyRequired": false,
  "loyaltySVAccountType": "string"
}
```

```json
Response Status OK
{
   OK
}
```

## Get a Specific Tender Type by ID

Used to retrieve a defined tender type by the Tender ID.
The {tenderId} is the tender you are retrieving.

GET
/emerald/selling-service/c1/selling-configuration/tender-settings/tender-types/{tenderId}

```json
Response
{
    "tenderId": "66",
    "tenderType": "CreditDebit",
    "descriptions": [
        {
            "culture": "en-US",
            "value": "Visa"
        }
    ],
    "validators": [
        "string"
    ],
    "checkValidatorName": "null",
    "currency": "USD",
    "manualEntry": false,
    "isProcessedByEps": true,
    "isEcc": false,
    "alternateTenderId": "null",
    "isUniquelyIdentifiable": false,
    "check21ValidationEnabled": false,
    "isBottleDepositVoucher": false,
    "tenderReferences": [
        "DB"
    ],
    "isLoyaltyRequired": false,
    "loyaltySVAccountType": "string"
}
```

##  Get Change Options per Tender Type by Tender ID

Used to retrieve the change options defined for a specific Tender ID. 
The following example is for the Cash Tender. The UpToAmount indicates the maximum amount of change that can be given with Cash.

GET
/emerald/selling-service/c1/selling-configuration/tender-settings/tender-types/{tenderId}/change-options

```json
Response Status OK
{
    "isConsolidateOnChange": true,
    "isAutoVoidDisabled": false,
    "changePriority": [
        {
            "enterpriseUnitId": "00000000000000000000000000000000",
            "touchPointGroupId": null,
            "value": 1
        }
    ],
    "changeDefinitions": [
        {
            "enterpriseUnitId": "00000000000000000000000000000000",
            "touchPointGroupId": null,
            "value": [
                {
                    "tenderChangeId": "1",
                    "upToAmount": 100
                }
            ]
        }
    ]
}
   ```

## Get All Tender Types

Used to retrieve all the tender types defined.

GET

/emerald/selling-service/c1/selling-configuration/tender-settings/tender-types

```json
Response Status OK
{
    "lastPage": true,
    "pageNumber": 0,
    "totalPages": 1,
    "totalResults": 27,
    "pageContent": [
        {
            "tenderId": "15",
            "tenderType": "CreditDebit",
            "descriptions": [
                {
                    "culture": "en-US",
                    "value": "Debit"
                }
            ],
            "validators": [],
            "checkValidatorName": null,
            "currency": "USD",
            "manualEntry": false,
            "isProcessedByEps": true,
            "isEcc": false,
            "alternateTenderId": null,
            "isUniquelyIdentifiable": false,
            "check21ValidationEnabled": false,
            "isBottleDepositVoucher": false,
            "tenderReferences": [
                "DB"
            ],
            "isLoyaltyRequired": false,
            "loyaltySVAccountType": null
        },
        {
            "tenderId": "30",
            "tenderType": "CreditDebit",
            "descriptions": [
                {
                    "culture": "en-US",
                    "value": "Gift Card"
                }
            ],
            "validators": [],
            "checkValidatorName": null,
            "currency": "USD",
            "manualEntry": false,
            "isProcessedByEps": true,
            "isEcc": false,
            "alternateTenderId": null,
            "isUniquelyIdentifiable": true,
            "check21ValidationEnabled": false,
            "isBottleDepositVoucher": false,
            "tenderReferences": [
                "GC"
            ],
            "isLoyaltyRequired": false,
            "loyaltySVAccountType": null
        },
        {
            "tenderId": "42",
            "tenderType": "eWIC",
            "descriptions": [
                {
                    "culture": "en-US",
                    "value": "eWIC"
                }
            ],
            "validators": [],
            "checkValidatorName": null,
            "currency": "USD",
            "manualEntry": false,
            "isProcessedByEps": true,
            "isEcc": false,
            "alternateTenderId": null,
            "isUniquelyIdentifiable": false,
            "check21ValidationEnabled": false,
            "isBottleDepositVoucher": false,
            "tenderReferences": [
                "EW",
                "EWeWic"
            ],
            "isLoyaltyRequired": false,
            "loyaltySVAccountType": null
        },
        {
            "tenderId": "45",
            "tenderType": "WicCvv",
            "descriptions": [
                {
                    "culture": "en-US",
                    "value": "WIC CVV"
                }
            ],
            "validators": [],
            "checkValidatorName": null,
            "currency": "USD",
            "manualEntry": false,
            "isProcessedByEps": false,
            "isEcc": false,
            "alternateTenderId": null,
            "isUniquelyIdentifiable": false,
            "check21ValidationEnabled": false,
            "isBottleDepositVoucher": false,
            "tenderReferences": [],
            "isLoyaltyRequired": false,
            "loyaltySVAccountType": null
        },
        {
            "tenderId": "60",
            "tenderType": "Reward",
            "descriptions": [
                {
                    "culture": "en-US",
                    "value": "MFR Coupon"
                }
            ],
            "validators": [],
            "checkValidatorName": null,
            "currency": "USD",
            "manualEntry": false,
            "isProcessedByEps": false,
            "isEcc": false,
            "alternateTenderId": null,
            "isUniquelyIdentifiable": false,
            "check21ValidationEnabled": false,
            "isBottleDepositVoucher": false,
            "tenderReferences": [],
            "isLoyaltyRequired": false,
            "loyaltySVAccountType": null
        },
        {
            "tenderId": "70",
            "tenderType": "CreditDebit",
            "descriptions": [
                {
                    "culture": "en-US",
                    "value": "FSA"
                }
            ],
            "validators": [],
            "checkValidatorName": null,
            "currency": "USD",
            "manualEntry": false,
            "isProcessedByEps": true,
            "isEcc": false,
            "alternateTenderId": null,
            "isUniquelyIdentifiable": false,
            "check21ValidationEnabled": false,
            "isBottleDepositVoucher": false,
            "tenderReferences": [
                "FSA"
            ],
            "isLoyaltyRequired": false,
            "loyaltySVAccountType": null
        },
        {
            "tenderId": "80",
            "tenderType": "Voucher",
            "descriptions": [
                {
                    "culture": "en-US",
                    "value": "Bottle Deposit Return"
                }
            ],
            "validators": [],
            "checkValidatorName": null,
            "currency": "USD",
            "manualEntry": false,
            "isProcessedByEps": false,
            "isEcc": false,
            "alternateTenderId": null,
            "isUniquelyIdentifiable": true,
            "check21ValidationEnabled": false,
            "isBottleDepositVoucher": true,
            "tenderReferences": [],
            "isLoyaltyRequired": false,
            "loyaltySVAccountType": null
        },
        {
            "tenderId": "11",
            "tenderType": "CreditDebit",
            "descriptions": [
                {
                    "culture": "en-US",
                    "value": "MasterCard"
                }
            ],
            "validators": [],
            "checkValidatorName": null,
            "currency": "USD",
            "manualEntry": false,
            "isProcessedByEps": true,
            "isEcc": false,
            "alternateTenderId": null,
            "isUniquelyIdentifiable": false,
            "check21ValidationEnabled": false,
            "isBottleDepositVoucher": false,
            "tenderReferences": [
                "MC"
            ],
            "isLoyaltyRequired": false,
            "loyaltySVAccountType": null
        },
        {
            "tenderId": "50",
            "tenderType": "Check",
            "descriptions": [
                {
                    "culture": "en-US",
                    "value": "Personal Check"
                }
            ],
            "validators": [
                "NorthAmericaStandardCheckValidator"
            ],
            "checkValidatorName": "NorthAmericaStandardCheckValidator",
            "currency": "USD",
            "manualEntry": false,
            "isProcessedByEps": false,
            "isEcc": false,
            "alternateTenderId": null,
            "isUniquelyIdentifiable": false,
            "check21ValidationEnabled": false,
            "isBottleDepositVoucher": false,
            "tenderReferences": [],
            "isLoyaltyRequired": false,
            "loyaltySVAccountType": null
        },
        {
            "tenderId": "3",
            "tenderType": "Check",
            "descriptions": [
                {
                    "culture": "en-US",
                    "value": "Check"
                }
            ],
            "validators": [
                "string"
            ],
            "checkValidatorName": "null",
            "currency": "USD",
            "manualEntry": false,
            "isProcessedByEps": false,
            "isEcc": false,
            "alternateTenderId": "null",
            "isUniquelyIdentifiable": false,
            "check21ValidationEnabled": false,
            "isBottleDepositVoucher": false,
            "tenderReferences": [
                "null"
            ],
            "isLoyaltyRequired": false,
            "loyaltySVAccountType": "string"
        },
        {
            "tenderId": "Check",
            "tenderType": "Check",
            "descriptions": [
                {
                    "culture": "en-US",
                    "value": "Check"
                }
            ],
            "validators": [
                "string"
            ],
            "checkValidatorName": "null",
            "currency": "USD",
            "manualEntry": false,
            "isProcessedByEps": false,
            "isEcc": false,
            "alternateTenderId": "null",
            "isUniquelyIdentifiable": false,
            "check21ValidationEnabled": false,
            "isBottleDepositVoucher": false,
            "tenderReferences": [
                "null"
            ],
            "isLoyaltyRequired": false,
            "loyaltySVAccountType": "string"
        },
        {
            "tenderId": "1",
            "tenderType": "Cash",
            "descriptions": [
                {
                    "culture": "en-US",
                    "value": "Cash"
                }
            ],
            "validators": [],
            "checkValidatorName": null,
            "currency": "USD",
            "manualEntry": false,
            "isProcessedByEps": false,
            "isEcc": false,
            "alternateTenderId": null,
            "isUniquelyIdentifiable": false,
            "check21ValidationEnabled": false,
            "isBottleDepositVoucher": false,
            "tenderReferences": [],
            "isLoyaltyRequired": false,
            "loyaltySVAccountType": null
        },
        {
            "tenderId": "66",
            "tenderType": "CreditDebit",
            "descriptions": [
                {
                    "culture": "en-US",
                    "value": "Visa"
                }
            ],
            "validators": [
                "string"
            ],
            "checkValidatorName": "null",
            "currency": "USD",
            "manualEntry": false,
            "isProcessedByEps": true,
            "isEcc": false,
            "alternateTenderId": "null",
            "isUniquelyIdentifiable": false,
            "check21ValidationEnabled": false,
            "isBottleDepositVoucher": false,
            "tenderReferences": [
                "DB"
            ],
            "isLoyaltyRequired": false,
            "loyaltySVAccountType": "string"
        },
        {
            "tenderId": "10",
            "tenderType": "CreditDebit",
            "descriptions": [
                {
                    "culture": "en-US",
                    "value": "Visa"
                }
            ],
            "validators": [],
            "checkValidatorName": null,
            "currency": "USD",
            "manualEntry": false,
            "isProcessedByEps": true,
            "isEcc": false,
            "alternateTenderId": null,
            "isUniquelyIdentifiable": false,
            "check21ValidationEnabled": false,
            "isBottleDepositVoucher": false,
            "tenderReferences": [
                "VS"
            ],
            "isLoyaltyRequired": false,
            "loyaltySVAccountType": null
        },
        {
            "tenderId": "12",
            "tenderType": "CreditDebit",
            "descriptions": [
                {
                    "culture": "en-US",
                    "value": "American Express"
                }
            ],
            "validators": [],
            "checkValidatorName": null,
            "currency": "USD",
            "manualEntry": false,
            "isProcessedByEps": true,
            "isEcc": false,
            "alternateTenderId": null,
            "isUniquelyIdentifiable": false,
            "check21ValidationEnabled": false,
            "isBottleDepositVoucher": false,
            "tenderReferences": [
                "AX"
            ],
            "isLoyaltyRequired": false,
            "loyaltySVAccountType": null
        },
        {
            "tenderId": "13",
            "tenderType": "CreditDebit",
            "descriptions": [
                {
                    "culture": "en-US",
                    "value": "Discover"
                }
            ],
            "validators": [],
            "checkValidatorName": null,
            "currency": "USD",
            "manualEntry": false,
            "isProcessedByEps": true,
            "isEcc": false,
            "alternateTenderId": null,
            "isUniquelyIdentifiable": false,
            "check21ValidationEnabled": false,
            "isBottleDepositVoucher": false,
            "tenderReferences": [
                "DS"
            ],
            "isLoyaltyRequired": false,
            "loyaltySVAccountType": null
        },
        {
            "tenderId": "14",
            "tenderType": "CreditDebit",
            "descriptions": [
                {
                    "culture": "en-US",
                    "value": "Diners"
                }
            ],
            "validators": [],
            "checkValidatorName": null,
            "currency": "USD",
            "manualEntry": false,
            "isProcessedByEps": true,
            "isEcc": false,
            "alternateTenderId": null,
            "isUniquelyIdentifiable": false,
            "check21ValidationEnabled": false,
            "isBottleDepositVoucher": false,
            "tenderReferences": [
                "DICL"
            ],
            "isLoyaltyRequired": false,
            "loyaltySVAccountType": null
        },
        {
            "tenderId": "16",
            "tenderType": "CreditDebit",
            "descriptions": [
                {
                    "culture": "en-US",
                    "value": "Manual EFT"
                }
            ],
            "validators": [],
            "checkValidatorName": null,
            "currency": "USD",
            "manualEntry": true,
            "isProcessedByEps": true,
            "isEcc": false,
            "alternateTenderId": null,
            "isUniquelyIdentifiable": false,
            "check21ValidationEnabled": false,
            "isBottleDepositVoucher": false,
            "tenderReferences": [],
            "isLoyaltyRequired": false,
            "loyaltySVAccountType": null
        },
        {
            "tenderId": "40",
            "tenderType": "CreditDebit",
            "descriptions": [
                {
                    "culture": "en-US",
                    "value": "EBT Food Stamps"
                }
            ],
            "validators": [],
            "checkValidatorName": null,
            "currency": "USD",
            "manualEntry": false,
            "isProcessedByEps": true,
            "isEcc": false,
            "alternateTenderId": null,
            "isUniquelyIdentifiable": false,
            "check21ValidationEnabled": false,
            "isBottleDepositVoucher": false,
            "tenderReferences": [
                "EF"
            ],
            "isLoyaltyRequired": false,
            "loyaltySVAccountType": null
        },
        {
            "tenderId": "67",
            "tenderType": "CreditDebit",
            "descriptions": [
                {
                    "culture": "en-US",
                    "value": "GiftCard"
                }
            ],
            "validators": [
                "string"
            ],
            "checkValidatorName": "null",
            "currency": "USD",
            "manualEntry": true,
            "isProcessedByEps": true,
            "isEcc": false,
            "alternateTenderId": "null",
            "isUniquelyIdentifiable": true,
            "check21ValidationEnabled": false,
            "isBottleDepositVoucher": false,
            "tenderReferences": [
                "GC"
            ],
            "isLoyaltyRequired": false,
            "loyaltySVAccountType": "string"
        },
        {
            "tenderId": "41",
            "tenderType": "CreditDebit",
            "descriptions": [
                {
                    "culture": "en-US",
                    "value": "EBT Cash"
                }
            ],
            "validators": [],
            "checkValidatorName": null,
            "currency": "USD",
            "manualEntry": false,
            "isProcessedByEps": true,
            "isEcc": false,
            "alternateTenderId": null,
            "isUniquelyIdentifiable": false,
            "check21ValidationEnabled": false,
            "isBottleDepositVoucher": false,
            "tenderReferences": [
                "EC"
            ],
            "isLoyaltyRequired": false,
            "loyaltySVAccountType": null
        },
        {
            "tenderId": "43",
            "tenderType": "SmartWIC",
            "descriptions": [
                {
                    "culture": "en-US",
                    "value": "sWIC"
                }
            ],
            "validators": [],
            "checkValidatorName": null,
            "currency": "USD",
            "manualEntry": false,
            "isProcessedByEps": true,
            "isEcc": false,
            "alternateTenderId": null,
            "isUniquelyIdentifiable": false,
            "check21ValidationEnabled": false,
            "isBottleDepositVoucher": false,
            "tenderReferences": [
                "SW"
            ],
            "isLoyaltyRequired": false,
            "loyaltySVAccountType": null
        },
        {
            "tenderId": "44",
            "tenderType": "WicCheck",
            "descriptions": [
                {
                    "culture": "en-US",
                    "value": "WIC Check"
                }
            ],
            "validators": [],
            "checkValidatorName": null,
            "currency": "USD",
            "manualEntry": false,
            "isProcessedByEps": false,
            "isEcc": false,
            "alternateTenderId": null,
            "isUniquelyIdentifiable": false,
            "check21ValidationEnabled": false,
            "isBottleDepositVoucher": false,
            "tenderReferences": [],
            "isLoyaltyRequired": false,
            "loyaltySVAccountType": null
        },
        {
            "tenderId": "51",
            "tenderType": "Check",
            "descriptions": [
                {
                    "culture": "en-US",
                    "value": "Personal ECC Check"
                }
            ],
            "validators": [
                "NorthAmericaStandardCheckValidator"
            ],
            "checkValidatorName": "NorthAmericaStandardCheckValidator",
            "currency": "USD",
            "manualEntry": true,
            "isProcessedByEps": true,
            "isEcc": true,
            "alternateTenderId": null,
            "isUniquelyIdentifiable": false,
            "check21ValidationEnabled": false,
            "isBottleDepositVoucher": false,
            "tenderReferences": [],
            "isLoyaltyRequired": false,
            "loyaltySVAccountType": null
        },
        {
            "tenderId": "52",
            "tenderType": "Check",
            "descriptions": [
                {
                    "culture": "en-US",
                    "value": "Personal non ECC Check"
                }
            ],
            "validators": [
                "NorthAmericaStandardCheckValidator"
            ],
            "checkValidatorName": "NorthAmericaStandardCheckValidator",
            "currency": "USD",
            "manualEntry": true,
            "isProcessedByEps": true,
            "isEcc": false,
            "alternateTenderId": null,
            "isUniquelyIdentifiable": false,
            "check21ValidationEnabled": false,
            "isBottleDepositVoucher": false,
            "tenderReferences": [],
            "isLoyaltyRequired": false,
            "loyaltySVAccountType": null
        },
        {
            "tenderId": "61",
            "tenderType": "Reward",
            "descriptions": [
                {
                    "culture": "en-US",
                    "value": "Digital Coupon"
                }
            ],
            "validators": [],
            "checkValidatorName": null,
            "currency": "USD",
            "manualEntry": false,
            "isProcessedByEps": false,
            "isEcc": false,
            "alternateTenderId": null,
            "isUniquelyIdentifiable": false,
            "check21ValidationEnabled": false,
            "isBottleDepositVoucher": false,
            "tenderReferences": [],
            "isLoyaltyRequired": false,
            "loyaltySVAccountType": null
        },
        {
            "tenderId": "81",
            "tenderType": "Voucher",
            "descriptions": [
                {
                    "culture": "en-US",
                    "value": "Coinstar Voucher"
                }
            ],
            "validators": [],
            "checkValidatorName": null,
            "currency": "USD",
            "manualEntry": false,
            "isProcessedByEps": false,
            "isEcc": false,
            "alternateTenderId": null,
            "isUniquelyIdentifiable": true,
            "check21ValidationEnabled": false,
            "isBottleDepositVoucher": false,
            "tenderReferences": [],
            "isLoyaltyRequired": false,
            "loyaltySVAccountType": null
        }
    ]
}
```
