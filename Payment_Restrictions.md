# Payment Restrictions

The Selling Services supports Tender Item Restrictions for vouchers.
Tender Item Restrictions are defined in the CCM and used to define an item eligibility policy, which enables retailers to prohibit or allow the payment of selected items using a specific tender. For example, voucher cannot be used to purchase cigarettes and alcohol.

Tenders prohibited to pay for specific items, or items in specific item groups cannot be added to the cart if the tender amount covers the restricted items.
If the tender is restricted to pay only for specific items or items in specific item groups, the tender can be added to the cart only for the amount that covers the restricted items.

**HTTP Methods:**

* PUT - Save or update a Card Payment Restriction
* GET -  Get all Card Payment Restrictions
* GET -  Get a Single Card Payment Restriction by Given Restriction ID
* DELETE - Delete Single Card Payment Restrictions by Restriction ID
* GET - Get all Product Payment restrictions
* GET -  Get a Product Card Payment Restriction by Given Restriction ID
* PUT - Save or update Product Payment Restrictions
* DELETE - Delete Single Product Payment Restrictions by Restriction ID

## Add a product payment restriction - Prohibit

Add a product payment restriction to prohibit the payment of vouchers on specific products/categories, groups.

The {restrictionId} is the ID of the product payment restriction, e.g., 1 or Prohibit, etc.

**HTTP Method:**

PUT

/emerald/selling-service/selling-configuration/v1/payment-restriction-settings/product-payment-restrictions/{restrictionId}

Request

```json
{
  "restrictedProducts": {
    "products": [
      {
        "value": "101"
      }
    ]
  },
  "eligibilityPolicyRelation": "ProhibitTenderFor",
  "allowReverseEligibility": false,
  "restrictedFor": [
    {
      "enterpriseUnitId": null,
      "retailSegment": null,
      "tender": {
        "tenderId": "90",
        "cardType": null
      }
    }
  ],
  "returnItemsReduceEligibility": false,
  "tenderBalanceDisplayMode": "None"
}
```

Response 200 OK

## Add a product payment restriction - allow

Add a product payment restriction to allow the payment of vouchers on specific products/categories, groups.

The {restrictionId} is the ID of the product payment restriction, e.g., 1 or Prohibit, etc.

**HTTP Method:**

PUT

/emerald/selling-service/selling-configuration/v1/

Request

```json
{
  "restrictedProducts": {
    "products": [
      {
        "value": "123"
      }
    ]
  },
  "eligibilityPolicyRelation": "AllowTendersForOnly",
  "allowReverseEligibility": false,
  "restrictedFor": [
    {
      "enterpriseUnitId": null,
      "retailSegment": null,
      "tender": {
        "tenderId": "91",
        "cardType": null
      }
    }
  ],
  "returnItemsReduceEligibility": false,
  "tenderBalanceDisplayMode": "None"
}
```

Response 200 OK

## Add a rstriction on a category

**HTTP Method:**

PUT

/emerald/selling-service/selling-configuration/v1/

Request

```json
{
  "restrictedProducts": {
    "categories": [
      "Diary"
    ]
  },
  "eligibilityPolicyRelation": "ProhibitTenderFor",
  "allowReverseEligibility": false,
  "restrictedFor": [
    {
      "enterpriseUnitId": null,
      "retailSegment": null,
      "tender": {
        "tenderId": "92",
        "cardType": null
      }
    }
  ],
  "returnItemsReduceEligibility": false,
  "tenderBalanceDisplayMode": "None"
}
```

Response 200 OK

## Add a restriction on an item group

Request

```json
{
  "restrictedProducts": {
    "groups": [
      "milk drinks"
    ]
  },
  "eligibilityPolicyRelation": "ProhibitTenderFor",
  "allowReverseEligibility": false,
  "restrictedFor": [
    {
      "enterpriseUnitId": null,
      "retailSegment": null,
      "tender": {
        "tenderId": "93",
        "cardType": null
      }
    }
  ],
  "returnItemsReduceEligibility": false,
  "tenderBalanceDisplayMode": "None"
}
```

Response 200 OK

## Get all product payment restrictions

**HTTP Method:**

GET
/emerald/selling-service/selling-configuration/v1/payment-restriction-settings/product-payment-restrictions

Response

```json
{
    "lastPage": true,
    "pageNumber": 0,
    "totalPages": 1,
    "totalResults": 4,
    "pageContent": [
        {
            "restrictionId": "11",
            "restrictedProducts": {
                "products": [
                    {
                        "value": "00000000003770"
                    }
                ]
            },
            "eligibilityPolicyRelation": "ProhibitTenderFor",
            "allowReverseEligibility": false,
            "restrictedFor": [
                {
                    "enterpriseUnitId": null,
                    "retailSegment": null,
                    "tender": {
                        "tenderId": "90",
                        "cardType": null
                    }
                }
            ],
            "returnItemsReduceEligibility": false,
            "tenderBalanceDisplayMode": "None"
        },
        {
            "restrictionId": "1",
            "restrictedProducts": {
                "products": [
                    {
                        "value": "00000000003770"
                    }
                ]
            },
            "eligibilityPolicyRelation": "ProhibitTenderFor",
            "allowReverseEligibility": false,
            "restrictedFor": [
                {
                    "enterpriseUnitId": null,
                    "retailSegment": null,
                    "tender": {
                        "tenderId": "90",
                        "cardType": null
                    }
                }
            ],
            "returnItemsReduceEligibility": false,
            "tenderBalanceDisplayMode": "None"
        },
        {
            "restrictionId": "2",
            "restrictedProducts": {
                "products": [
                    {
                        "value": "00000000333330"
                    }
                ]
            },
            "eligibilityPolicyRelation": "AllowTendersForOnly",
            "allowReverseEligibility": false,
            "restrictedFor": [
                {
                    "enterpriseUnitId": null,
                    "retailSegment": null,
                    "tender": {
                        "tenderId": "91",
                        "cardType": null
                    }
                }
            ],
            "returnItemsReduceEligibility": false,
            "tenderBalanceDisplayMode": "None"
        },
        {
            "restrictionId": "3",
            "restrictedProducts": {
                "products": [
                    {
                        "value": "00000000003770"
                    }
                ]
            },
            "eligibilityPolicyRelation": "AllowTendersForOnly",
            "allowReverseEligibility": false,
            "restrictedFor": [
                {
                    "enterpriseUnitId": null,
                    "retailSegment": null,
                    "tender": {
                        "tenderId": "92",
                        "cardType": null
                    }
                }
            ],
            "returnItemsReduceEligibility": false,
            "tenderBalanceDisplayMode": "None"
        }
    ]
}
```

## Get a single product payment restriction

**HTTP Method:**

GET

/emerald/selling-service/selling-configuration/v1/payment-restriction-settings/product-payment-restrictions/{restrictionId}

Request

```json
{
    "restrictionId": "11",
    "restrictedProducts": {
        "products": [
            {
                "value": "00000000003770"
            }
        ]
    },
    "eligibilityPolicyRelation": "ProhibitTenderFor",
    "allowReverseEligibility": false,
    "restrictedFor": [
        {
            "enterpriseUnitId": null,
            "retailSegment": null,
            "tender": {
                "tenderId": "90",
                "cardType": null
            }
        }
    ],
    "returnItemsReduceEligibility": false,
    "tenderBalanceDisplayMode": "None"
}
```