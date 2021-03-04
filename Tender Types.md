
# Tender Types

**Description:**

Tenders definitions are needed in order to add payments to a Cart.

**HTTP Methods:**

* PUT - Save or update Tender Mapping Configuratio

## Cash Tender

**HTTP Method:**

PUT

/emerald/selling-configuration/tender-settings/tender-types/1

```json
Example 1
Add a Cash Tender

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

**HTTP Method:**

PUT

/emerald/selling-configuration/tender-settings/tender-types/1/payment-options

```json
Example 2
Define Options for Tender Type, per Enterprise Units Taxonomy and Touchpoint Group (Optional)

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

Response
{
   OK
}
```
**HTTP Method:**

PUT

/emerald/selling-configuration/tender-settings/tender-types/1/change-options

```json
Example 3
Set Change Options for the Tender Type per Enterprise Units Taxonomy and Touchpoint Group (Optional)

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
