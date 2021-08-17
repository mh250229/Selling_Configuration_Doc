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
