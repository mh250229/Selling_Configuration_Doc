# Return Policy

## Return Policy Types

This service allows to return items according to defined policies Non Receipt Returns (NRR), TBR (Transaction Based Returns (TBR), and Return All.

Emerald 2.0 is integrated with the Business Service Platform (BSP) to support Central Returns. All retail transactions are retained in a central location in the BSP TDM application, which is accessible by all retailers.
The Return Policy determines how to handle items returned to the store by customers.

Return Policies can be managed centrally from head office. The Central Returns solution provides central management with all return transactions, and determines if items can be returned, when the items can be returned, and specific rules preventing items from being returned for different reasons. For example: Not accepting the return of an item after its return expiry date.

**Return Policy types include:**

* **Non Receipted** - to define the refund policy details to return an item without a receipt. The Cart API invokes the active NRR Policy, which is applied to return the item. If there is no active NRR Policy for the store, the Return Bin cannot be created, and items cannot be returned.
The NRR Policy can also be applied to Items returned within a Sale transaction, i.e. in a transaction in which items are purchased and returned.

* **Transaction Based** - to define refund policy details for all transactions in which items are returned with a receipt. On returning an item, the Cart API invokes the active TBR Policy, which is applied to transactions in which return items are returned based on an original receipt.  Both regular and weight items, as well as linked items and items with amount embedded barcodes can be returned using the TBR Policy. If there is no active TBR Policy for the store, the Return Bin cannot be created. When a Return Bin is created without the TransactionLogID, a "Cannot create a Return Bin. TBR must have TransactionLogID" exception is prompted.

* **Return All** - to define refund policy details for returns in which all the items in the transaction are returned.

* **Bottle Deposit** - to define a refund policy when empty bottles are returned to refund the deposit amount. The Restrictions and Reason Codes options applied to other return policies are supported by the Bottle Deposit Return Policy. If the cart has a Return Bin Type Bottle Deposit, only items associated to the Bottle Deposit groups in the catalog can be returned. A Return Bin from Type - Bottle Deposit can only be created if there is an effective Bottle Deposit Return Policy for the store.

**Note:**
Only Non Receipted Returns can be done without the BSP.

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

* Restrictions – Items linked to the ‘NonReceiptedReturnsRestrictedItemsGroup’ group are prohibited to return.
* Best for Customer – The customer is favored when the item is returned against a Receipt in which the same item was purchased more than once and sold for different prices.
* Receipt lookup period: - 90 days.

### Add a TBR Return Policy

**HTTP Method:**

PUT

/emerald/selling-service/c1/selling-configuration/return-policy-settings/return-policy/returnpolicy4

Request

```json
{
    "state": "TBR",
    "name": "return-policy-4",
    "startDateTime": {
        "nominalValue": "2020-05-14T00:00:00"
    },
    "endDateTime": {
        "nominalValue": "2020-05-14T00:00:00"
    },
    "isSubmitted": true,
    "priceVerificationRequired": false,
    "receiptLookupPeriod": 2,
    "enterpriseUnitsIds": [
        "00000000000000000000000brooklyn1",
        "enterprise-units-id-2"
    ],
    "isBestForGuest": false,
    "returnRules": {
        "expressionRules": [
            {
                "name": "return-rule-1",
                "sequence": 1,
                "condition": {},
                "action": {
                    "denyAction": {
                        "actionStrategy": "deny-action-strategy-1",
                        "messageId": "deny-action-message-id-1"
                    },
                    "managerApprovalAction": {
                        "roles": [
                            "forced-exchange-override-threshold-#1-role-name-1"
                        ],
                        "scope": "Request",
                        "actionStrategy": "manager-approval-action-strategy-1",
                        "messageId": "manager-approval-message-id-1"
                    },
                    "confirmationAction": {
                        "actionStrategy": "Confirmation-action-strategy-1",
                        "messageId": "Confirmation-message-id-1"
                    }
                }
            }
        ],
        "behaviorRules": [
            {
                "name": "Behavior-rule-1",
                "sequence": 1,
                "condition": {},
                "action": {
                    "denyAction": {
                        "actionStrategy": "deny-action-strategy-1",
                        "messageId": "deny-action-message-id-1"
                    },
                    "managerApprovalAction": {
                        "roles": [
                            "forced-exchange-override-threshold-#1-role-name-1"
                        ],
                        "scope": "Request",
                        "actionStrategy": "manager-approval-action-strategy-1",
                        "messageId": "manager-approval-message-id-1"
                    },
                    "confirmationAction": {
                        "actionStrategy": "Confirmation-action-strategy-1",
                        "messageId": "Confirmation-message-id-1"
                    }
                },
                "type": "SWITCH_TENDER"
            }
        ],
        "thresholdRules": [
            {
                "name": "return-threshold-rule-1",
                "sequence": 1,
                "isOffline": true,
                "action": {
                    "denyAction": null,
                    "managerApprovalAction": null,
                    "confirmationAction": null
                }
            }
        ]
    },
    "reimbursement": {
        "refundByPayments": [
            {
                "priority": 1,
                "paidTenderId": "refund-by-payment-paid-tender-id-1",
                "refundByAmounts": [
                    {
                        "refundTenderId": "refund-by-payment-refund-tender-id-1",
                        "upToAmount": 10.0
                    }
                ]
            }
        ],
        "refundByAmounts": null
    },
    "reasonConfiguration": {
        "reasonCodePromtingMethod": "PerTransaction",
        "reasonAssociations": [
            {
                "reasonCodeId": "reason-configuration-associations-code-id 1",
                "disposalMethodDescription": [
                    {
                        "culture": "reason-associations-description-Culture-1",
                        "value": "reason-associations-description-value-1"
                    }
                ],
                "productIds": [
                    "reason-associations-product-id-1"
                ],
                "categoryIds": [
                    "reason-associations-category-id-1"
                ]
            }
        ]
    },
    "requiredCustomerDetails": {
        "customerDetailsRequired": true,
        "firstNameRequired": true,
        "lastNameRequired": true,
        "addressRequired": true,
        "cityRequired ": true,
        "provinceRequired": true,
        "postalCodeRequired": true
    }
}
```

Response 200 OK

### Get a TBR Return Policy

**HTTP Method:**

GET

/emerald/selling-service/c1/selling-configuration/return-policy-settings/return-policy/returnpolicy4

Response

```json
{
    "returnPolicyId": "returnpolicy4",
    "state": "TBR",
    "name": "return-policy-4",
    "startDateTime": {
        "nominalValue": "2020-05-14T00:00:00"
    },
    "endDateTime": {
        "nominalValue": "2020-05-14T00:00:00"
    },
    "isSubmitted": true,
    "priceVerificationRequired": false,
    "receiptLookupPeriod": 2,
    "enterpriseUnitsIds": [
        "00000000000000000000000brooklyn1",
        "enterprise-units-id-2"
    ],
    "isBestForGuest": false,
    "returnRules": {
        "expressionRules": [
            {
                "name": "return-rule-1",
                "sequence": 1,
                "condition": {},
                "action": {
                    "denyAction": {
                        "actionStrategy": "deny-action-strategy-1",
                        "messageId": "deny-action-message-id-1"
                    },
                    "managerApprovalAction": {
                        "roles": [
                            "forced-exchange-override-threshold-#1-role-name-1"
                        ],
                        "scope": "Request",
                        "actionStrategy": "manager-approval-action-strategy-1",
                        "messageId": "manager-approval-message-id-1"
                    },
                    "confirmationAction": {
                        "actionStrategy": "Confirmation-action-strategy-1",
                        "messageId": "Confirmation-message-id-1"
                    }
                }
            }
        ],
        "behaviorRules": [
            {
                "name": "Behavior-rule-1",
                "sequence": 1,
                "condition": {},
                "action": {
                    "denyAction": {
                        "actionStrategy": "deny-action-strategy-1",
                        "messageId": "deny-action-message-id-1"
                    },
                    "managerApprovalAction": {
                        "roles": [
                            "forced-exchange-override-threshold-#1-role-name-1"
                        ],
                        "scope": "Request",
                        "actionStrategy": "manager-approval-action-strategy-1",
                        "messageId": "manager-approval-message-id-1"
                    },
                    "confirmationAction": {
                        "actionStrategy": "Confirmation-action-strategy-1",
                        "messageId": "Confirmation-message-id-1"
                    }
                },
                "type": "SWITCH_TENDER"
            }
        ],
        "thresholdRules": [
            {
                "name": "return-threshold-rule-1",
                "sequence": 1,
                "isOffline": true,
                "action": {
                    "denyAction": null,
                    "managerApprovalAction": null,
                    "confirmationAction": null
                }
            }
        ]
    },
    "reimbursement": {
        "refundByPayments": [
            {
                "priority": 1,
                "paidTenderId": "refund-by-payment-paid-tender-id-1",
                "refundByAmounts": [
                    {
                        "refundTenderId": "refund-by-payment-refund-tender-id-1",
                        "upToAmount": 10.0
                    }
                ]
            }
        ],
        "refundByAmounts": null
    },
    "reasonConfiguration": {
        "reasonCodePromtingMethod": "PerTransaction",
        "reasonAssociations": [
            {
                "reasonCodeId": "reason-configuration-associations-code-id 1",
                "disposalMethodDescription": [
                    {
                        "culture": "reason-associations-description-Culture-1",
                        "value": "reason-associations-description-value-1"
                    }
                ],
                "productIds": [
                    "reason-associations-product-id-1"
                ],
                "categoryIds": [
                    "reason-associations-category-id-1"
                ]
            }
        ]
    },
    "requiredCustomerDetails": {
        "customerDetailsRequired": true,
        "firstNameRequired": true,
        "lastNameRequired": true,
        "addressRequired": true,
        "cityRequired ": true,
        "provinceRequired": true,
        "postalCodeRequired": true
    }
}
```

## NRR Return Policy

### Add an NRR Return Policy

**HTTP Method:**

PUT

/emerald/selling-service/c1/selling-configuration/return-policy-settings/return-policy/returnpolicy1

Request

```json
{
    "state": "NRR",
    "name": "return-policy-all",
    "startDateTime": {
        "nominalValue": "2020-05-14T00:00:00"
    },
    "endDateTime": {
        "nominalValue": "2020-05-14T00:00:00"
    },
    "isSubmitted": true,
    "priceVerificationRequired": false,
    "receiptLookupPeriod": 2,
    "enterpriseUnitsIds": [
        "00000000000000000000000brooklyn1",
        "enterprise-units-id-2"
    ],
    "isBestForGuest": false,
    "returnRules": {
        "expressionRules": [
            {
                "name": "return-rule-1",
                "sequence": 1,
                "condition": {},
                "action": {
                    "denyAction": {
                        "actionStrategy": "deny-action-strategy-1",
                        "messageId": "deny-action-message-id-1"
                    },
                    "managerApprovalAction": {
                        "roles": [
                            "forced-exchange-override-threshold-#1-role-name-1"
                        ],
                        "scope": "Request",
                        "actionStrategy": "manager-approval-action-strategy-1",
                        "messageId": "manager-approval-message-id-1"
                    },
                    "confirmationAction": {
                        "actionStrategy": "Confirmation-action-strategy-1",
                        "messageId": "Confirmation-message-id-1"
                    }
                }
            }
        ],
        "behaviorRules": [
            {
                "name": "Behavior-rule-1",
                "sequence": 1,
                "condition": {},
                "action": {
                    "denyAction": {
                        "actionStrategy": "deny-action-strategy-1",
                        "messageId": "deny-action-message-id-1"
                    },
                    "managerApprovalAction": {
                        "roles": [
                            "forced-exchange-override-threshold-#1-role-name-1"
                        ],
                        "scope": "Request",
                        "actionStrategy": "manager-approval-action-strategy-1",
                        "messageId": "manager-approval-message-id-1"
                    },
                    "confirmationAction": {
                        "actionStrategy": "Confirmation-action-strategy-1",
                        "messageId": "Confirmation-message-id-1"
                    }
                },
                "type": "SWITCH_TENDER"
            }
        ],
        "thresholdRules": [
            {
                "name": "return-threshold-rule-1",
                "sequence": 1,
                "isOffline": true,
                "action": {
                    "denyAction": null,
                    "managerApprovalAction": null,
                    "confirmationAction": null
                }
            }
        ]
    },
    "reimbursement": {
        "refundByPayments": [
            {
                "priority": 1,
                "paidTenderId": "refund-by-payment-paid-tender-id-1",
                "refundByAmounts": [
                    {
                        "refundTenderId": "refund-by-payment-refund-tender-id-1",
                        "upToAmount": 10.0
                    }
                ]
            }
        ],
        "refundByAmounts": null
    },
    "reasonConfiguration": {
        "reasonCodePromtingMethod": "PerTransaction",
        "reasonAssociations": [
            {
                "reasonCodeId": "reason-configuration-associations-code-id 1",
                "disposalMethodDescription": [
                    {
                        "culture": "reason-associations-description-Culture-1",
                        "value": "reason-associations-description-value-1"
                    }
                ],
                "productIds": [
                    "reason-associations-product-id-1"
                ],
                "categoryIds": [
                    "reason-associations-category-id-1"
                ]
            }
        ]
    },
    "requiredCustomerDetails": {
        "customerDetailsRequired": true,
        "firstNameRequired": true,
        "lastNameRequired": true,
        "addressRequired": true,
        "cityRequired ": true,
        "provinceRequired": true,
        "postalCodeRequired": true
    }
}
```

Response 200 OK

### Get an NRR Return Policy

**HTTP Method:**

GET

/emerald/selling-service/c1/selling-configuration/return-policy-settings/return-policy/returnpolicy1

Response

```json
{
    "lastPage": true,
    "pageNumber": 0,
    "totalPages": 1,
    "totalResults": 1,
    "pageContent": [
        {
            "returnPolicyId": "NRR1",
            "state": "NRR",
            "name": "return-policy-NRR",
            "startDateTime": {
                "nominalValue": "2022-02-15T10:01:20.4735731"
            },
            "endDateTime": {
                "nominalValue": "2032-02-16T00:00:00"
            },
            "isSubmitted": true,
            "priceVerificationRequired": false,
            "receiptLookupPeriod": 2,
            "enterpriseUnitsIds": [
                "00000000000000000000000000035295"
            ],
            "isBestForGuest": false,
            "returnRules": null,
            "reimbursement": null,
            "reasonConfiguration": null,
            "requiredCustomerDetails": null
        }
    ]
}
```

## POST Effective Return Policies

**HTTP Method:**

POST

/emerald/selling-service/c1/selling-configuration/return-policy-settings/return-policy/effective-return-policies

Request

```json
{
    "returnPolicyIds": [
        "returnpolicy3",
        "returnpolicy4"
    ]
}
```

Response 200 OK

## Get Effective Return Policies

**HTTP Method:**

POST

/emerald/selling-service/c1/selling-configuration/return-policy-settings/return-policy/effective-return-policy?returnPolicyType=1&dateTimeTicks=637809485506473549

Response

```json
{
    "state": "NRR",
    "name": "return-policy-NRR",
    "startDateTime": {
        "nominalValue": "2022-02-15T10:01:20.4735731"
    },
    "endDateTime": {
        "nominalValue": "2032-02-16T00:00:00"
    },
    "isSubmitted": true,
    "priceVerificationRequired": false,
    "receiptLookupPeriod": 2,
    "enterpriseUnitsIds": [
        "00000000000000000000000000035295"
    ],
    "isBestForGuest": false,
    "returnRules": null,
    "reimbursement": null,
    "reasonConfiguration": null,
    "requiredCustomerDetails": null
}
```

## Get All Return Policies.

**HTTP Method:**

GET

/emerald/selling-service/c1/selling-configuration/return-policy-settings/return-policy

Response

```json
{
    "lastPage": true,
    "pageNumber": 0,
    "totalPages": 1,
    "totalResults": 1,
    "pageContent": [
        {
            "returnPolicyId": "NRR1",
            "state": "NRR",
            "name": "return-policy-NRR",
            "startDateTime": {
                "nominalValue": "2022-02-15T10:01:20.4735731"
            },
            "endDateTime": {
                "nominalValue": "2032-02-16T00:00:00"
            },
            "isSubmitted": true,
            "priceVerificationRequired": false,
            "receiptLookupPeriod": 2,
            "enterpriseUnitsIds": [
                "00000000000000000000000000035295"
            ],
            "isBestForGuest": false,
            "returnRules": null,
            "reimbursement": null,
            "reasonConfiguration": null,
            "requiredCustomerDetails": null
        }
    ]
}
```

Response 200 OK

## BDR Return Policy

The Out of Box configuration for the Bottle Deposit Return Policy includes the following:

* Best for Retailer – The retailer is favored when a bottle deposit is returned. (There is no business for best for customer/retailer in BDR)
* Receipt lookup period: - 0.

There is no Reason Code or Restriction configuration.

### Add a Bottle Deposit Return (BDR) Policy

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
    "nominalValue": "2031-06-20T00:00:00"
  },
  "isSubmitted": true,
  "priceVerificationRequired": false,
  "receiptLookupPeriod": 0,
  "enterpriseUnitsIds": [
    "00000000000000000000000000035295"
  ],
  "isBestForGuest": true,
  "returnRules": null,
  "reimbursement": null,
  "reasonConfiguration": null,
  "requiredCustomerDetails": null
}
```

Response 200 OK
