
# Return Policy

## Return Policy Types

This service allows to return items according to defined policies Non Receipt Returns (NRR), TBR (Transaction Based Returns (TBR), and Return All.
Emerald is integrated with the Business Service Platform (BSP) to support Central Returns. All retail transactions are retained in a central location in the BSP TDM application, which is accessible by all retailers.
The Return Policy determines how to handle items returned to the store by customers.
Return Policies can be managed centrally from head office. The Central Returns solution provides central management with all return transactions, and determines if items can be returned, when the items can be returned, and specific rules preventing items from being returned for different reasons. For example: Not accepting the return of an item after its return expiry date.

**Return Policy types include:**

* **Non Receipted** - to define the refund policy details to return an item without a receipt, the Cart API invokes the active NRR Policy, which is applied to return the item. If there is no active NRR Policy for the store, the Return Bin cannot be created, and items cannot be returned.
The NRR Policy can also be applied to Items returned within a Sale transaction, i.e. in a transaction in which items are purchased and returned.

* **Transaction Based** - to define refund policy details for all transactions in which items are returned with a receipt. On returning an item, the Cart API invokes the active TBR Policy, which is applied to transactions in which return items are returned based on an original receipt.  Both regular and weight items, as well as linked items and items with amount embedded barcodes can be returned using the TBR Policy. If there is no active TBR Policy for the store, the Return Bin cannot be created. When a Return Bin is created without the TransactionLogID, a "Cannot create a Return Bin. TBR must have TransactionLogID" exception is prompted.

* **Return All** - to define refund policy details for returns in which all the items in the transaction are returned.

* **Bottle Deposit** - to define a refund policy when empty bottles are returned to refund the deposit amount. The Restrictions and Reason Codes options applied to other return policies are supported by the Bottle Deposit Return Policy. If the cart has a Return Bin Type Bottle Deposit, only items associated to the Bottle Deposit groups in the catalog can be returned. A Return Bin from Type - Bottle Deposit can only be created if there is an effective Bottle Deposit Return Policy for the store.

**Note:**
Only Non Receipted Returns can be done without the BSP.

All Return Policies must be configured with the following mandatory options:

* State - the the state the policy is applied in, e.g., TBR, NRR, BDR, Return All.
* Name - the name of the Return Policy
* Start and End Date Times - defines the date and time during which the Return Policy is active.
* IsSubmitted - to indicate that the Return Policy was submitted.
* PriceVerificationRequired - indicates if during the return, the price of the item being returned must be verified.
* Receipt Lookup Period - to define the number of days up to which the system goes back in a search for transactions that were performed.
* Is Best for Guest - indicates if the refund policy favors the customer or the retailer, when the item is returned against a Receipt in which the same item was purchased more than once and sold for different prices. For example, open price items such as magazines.
  
All Return Policies can be configured with the following optional options:

* EnterpriseUnitsIds - all the business units to which the Return Policy is applied
* Reimbursement - to define the paid tender and refund tender details for the Return Policy:
  * The Paid tender defines the tender ID in the original transaction and the option to define the maximum refund amount to the tender can be defined, e.g., you can specify that if the paid tender was a Visa, you can refund up to a certain amount to the Visa.
  * The Refund tender defines the tender ID that can be used to refund the amount of the transaction and the amount up to which refunds with this tender are allowed.
  
* Reason configuration to define the return reason.
* Required Customer details to define that the customer details, such as name, address, etc., are captured during the return.

**HTTP Methods:**

POST - Get the effective return policy for business unit
GET - Get the effective return policy for business unit
DELETE - Deletes the specific Return Policy by policy ID
GET - Get Return Policy by Given Policy ID
PUT - Puts the specified Return Policy by given ID

## TBR Return Policy

The out of the box configuration for the TBR Policy includes the following:

* Reason Codes: The reason codes are prompted when a return item is scanned, and a reason code must be selected for each item during a return.

  * 11008 Damaged
  * Quality Problem
  * 11014 Package Condition
  * 11009 Not Needed
  * 11012 Product Recall
  * 11010 Price Problem
  * 11015 Expired
  * 11013 Activation Failed

* Restrictions – Items linked the ‘NonReceiptedReturnsRestrictedItemsGroup’ group are prohibited to return.
* Best for Customer – The customer is favored when the item is returned against a Receipt in which the same item was purchased more than once and sold for different prices.
* Receipt lookup period: - 90 days.

Example: Add a TBR Return Policy.

**HTTP Method:**

PUT

/emerald/selling-service/c1/selling-configuration/return-policy-settings/return-policy/{returnPolicyId}

Request

```json
{
  "state": "TBR",
  "name": "return-policy-TBR",
  "startDateTime": {
    "nominalValue": "2021-05-12T12:19:43.3768334"
  },
  "endDateTime": {
    "nominalValue": "2031-05-13T00:00:00"
  },
  "isSubmitted": true,
  "priceVerificationRequired": false,
  "receiptLookupPeriod": 90,
  "enterpriseUnitsIds": [
    "00000000000000000000000000035295"
  ],
   "isBestForGuest": "true",
  "returnRules": {
    "expressionRules": [
      {
        "name": "NonReceiptedReturnsRestrictedItemsGroup",
        "sequence": 14450092,
        "condition": {
          "includedGroups": [
            "NonReceiptedReturnsRestrictedItemsGroup"
          ]
        },
        "action": {
          "allowAction": null,
          "denyAction": {
            "actionStrategy": "Prohibit",
            "messageId": "Prohibit NonReceiptedReturnsRestrictedItemsGroup items"
          },
          "forcedExchangeItemAction": null,
          "forcedExchangeOverrideItemAction": null,
          "forcedExchangeOverrideThresholdAction": null,
          "forcedExchangeThresholdAction": null,
          "managerApprovalAction": null
        }
      }
    ],
    "thresholdRules": null,
  },
  "reimbursement": {
    "refundByPayments": [
      {
        "priority": 1,
        "paidTenderId": "10",
        "refundByAmounts": [
          {
            "refundTenderId": "10",
            "upToAmount": null,
          }
        ]
      }
      {
        "priority": 2,
        "paidTenderId": "1",
        "refundByAmounts": [
          {
            "refundTenderId": "1",
            "upToAmount": 1000.00
          }
        ]
      }
    ],
    "roles": [
      "String"
    ]
  },
  "reasonConfiguration": {
    "reasonCodePromtingMethod": "PerItem",
    "reasonAssociations": [
      {
        "reasonCodeId": "11008 Damaged",
        "disposalMethodDescription": [
          {
            "culture": "en-US",
            "value": "Damaged"
          }
        ],
        "productIds": [
          "String"
        ],
        "categoryIds": [
          "Dairy"
        ]
      }
    ]
  },
}
```

```json
Response 200 OK
{
}
```

## NRR Return Policy

Example: Add an NRR Return Policy.

**HTTP Method:**

PUT
/emerald/selling-service/c1/selling-configuration/return-policy-settings/return-policy/{returnPolicyId}

Request

```json
{
  "state": "NRR",
  "name": "return-policy-NRR",
  "startDateTime": {
    "nominalValue": "2021-04-24T12:24:51.4415108"
  },
  "endDateTime": {
    "nominalValue": "2031-04-25T00:00:00"
  },
  "isSubmitted": true,
  "priceVerificationRequired": false,
  "receiptLookupPeriod": 2,
  "enterpriseUnitsIds": [
    "00000000000000000000000000035295"
  ],
 "isBestForGuest": "false",
  "returnRules": null,
 "thresholdRules": [
      {
        "name": "NRR_threshold",
        "sequence": 60,
        "minValue": 1.00,
        "maxValue": 1000.00,
        "isOffline": null,
        "action": {}
      }
    ],

  "reimbursement": {
    "refundByAmounts": [
      {
        "refundTenderId": "1",
        "upToAmount": 1000.00
      }
    ],
    "roles": [
      "String"
    ]
  },
 "reasonConfiguration": {
    "reasonCodePromtingMethod": "PerTransaction",
    "reasonAssociations": [
      {
        "reasonCodeId": "11008 Damaged",
        "disposalMethodDescription": [
          {
            "culture": "en-US",
            "value": "Damaged"
          }
        ],
        "productIds": [
          "String"
        ],
        "categoryIds": [
          "Dairy"
        ]
      }
    ]
  },
  "requiredCustomerDetails": {
    "customerDetailsRequired": "true",
    "firstNameRequired": "true",
    "lastNameRequired": "true",
    "addressRequired": "true",
    "cityRequired ": "true",
    "provinceRequired": "true",
    "postalCodeRequired": "true"
  }
```

```json
Response 200 OK
{
}
```

## BDR Return Policy

The Out of Box configuration for the Bottle Deposit Return Policy includes the following:

* Best for Retailer – The retailer is favored when a bottle deposit is returned. (There is no business for best for customer/retailer in BDR)
* Receipt lookup period: - 0.

There is no Reason Code or Restriction configuration.

Example: Add a Bottle Deposit Return (BDR) Policy.

**HTTP Method:**

PUT
/emerald/selling-service/c1/selling-configuration/return-policy-settings/return-policy/{returnPolicyId}

Request

```json
{
  "state": "BDR",
  "name": "return-policy-BDR",
  "startDateTime": {
    "nominalValue": "2021-06-19T16:30:00.2348661"
  },
  "endDateTime": {
    "nominal
    Value": "2031-06-20T00:00:00"
  },
  "isSubmitted": true,
  "priceVerificationRequired": false,
  "receiptLookupPeriod": 0,
  "enterpriseUnitsIds": [
    "00000000000000000000000000035295"
  ],
  "isBestForGuest": true,
   "returnRules": {
    "expressionRules": [
      {
        "name": "AllowBottleDepositGroupOnly",
        "sequence": 14450092,
        "condition": {
          "includedGroups": [
            "BottleDepositGroup"
          ]
        },
        "action": {
          "AllowAction": {
            "actionStrategy": "Allow",
            "messageId": "BottleDepositGroups"
          },
          "forcedExchangeItemAction": null,
          "forcedExchangeOverrideItemAction": null,
          "forcedExchangeOverrideThresholdAction": null,
          "forcedExchangeThresholdAction": null,
          "managerApprovalAction": null
        }
      }
    ],
   "reimbursement": {
    "refundByAmounts": [
      {
        "refundTenderId": "1",
        "upToAmount": 1000.00
      }
    ],
  "reasonConfiguration": null,
  "requiredCustomerDetails": null
}
```

```json
Response 200 OK
{
}
```
