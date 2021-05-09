# Tender Types

## Additional Tender Types

The following tender types are supported:

* Check
* EFT Credit/Debit
* Gift Card

**HTTP Method:**

* PUT
* GET

### Add Check Tender Type

Used to add check tender types.

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

### Add EFT Credit/Debit Tender Type

Used to add EFT Credit/Debit tender types.

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
    "DB"
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

### Add Gift Card Tender Type

Used to add EFT Credit/Debit tender types.

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

### Get All Tender Types

Used to retrieve all the tender types.

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
