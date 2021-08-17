
# Return Policy

This service allows to return items according to defined policies Non Receipt Returns (NRR), TBR (Transaction Based Returns (TBR), and Return All.
Emerald is integrated with the Business Service Platform (BSP) to support Central Returns. All retail transactions are retained in a central location in the BSP TDM application, which is accessible by all retailers.
The Return Policy determines how to handle items returned to the store by customers.
Return Policies can be managed centrally from head office. The Central Returns solution provides central management with all return transactions, and determines if items can be returned, when the items can be returned, and specific rules preventing items from being returned for different reasons. For example: Not accepting the return of an item after its return expiry date.

**Return Policy types include:**

* **Non Receipted** - to define the refund policy details to return an item without a receipt, the Cart API invokes the active NRR Policy, which is applied to return the item

* **Transaction Based** - to define refund policy details for all transactions in which items are returned with a receipt.

* **Return All** - to define refund policy details for returns in which all the items in the transaction are returned.

* **Bottle Deposit** - to define a refund policy when empty bottles are returned to refund the deposit amount.

**Note:**
Only Non Receipted Returns can be done without the BSP.

Once all Return Policies are set up, you can use the following services to retrieve one or all Return Policy, and delete a Return Policy from the system

**HTTP Methods:**

POST - Get the effective return policy for business unit
GET - Get the effective return policy for business unit
DELETE - Deletes the specific Return Policy by policy ID
GET - Get Return Policy by Given Policy ID
PUT - Puts the specified Return Policy by given ID

## TBR Return Policy

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
    "nominalValue": "2021-04-28T18:00:42.970774"
  },
  "endDateTime": {
    "nominalValue": "2031-04-29T00:00:00"
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
}```

```json
Response 200 OK
{
}
```

## BDR Return Policy

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
    "nominalValue": "2031-06-20T00:00:00"
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

```json
Response 200 OK
{
}
```
