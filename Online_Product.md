# Online Product Behavior

The Online Purchase services are used to define new Online Purchase Profiles in the system. Define the communication settings, specify the receipt printed in the transaction in online, offline or decline scenarios.
Receipts must be set up prior to configuring the online product behavior. Different receipts are printed based on the response received from the provider for transactions that were authorized online, or offline or not authorized.

The "authorizationTrigger" parameter determines when an authorization request is sent to the provider:

* Item Sale - the authorization request is triggered on scanning the item
* Total - the authorization request is triggered once the cart status is updated to Total.
* Transaction Complete - the authorization request is triggered once the transaction is tendered and completed

The request sent to the provider can include specifc configuration, such as:

* "confirmationRequestRequired" - determines if confirmation is required on authorization. A pre-authorization request is sent to the provider once the item is scanned, and a confirmation authorization request is sent to the provider once the transaction is tendered and completed.
* "refundRequestRequired" - determines if a request is sent to the provider when an onine item is returned, e.g., to deactivate a Gift Card when the Gift card is returned.
* "voidRequestRequired" - determines if a request is sent to the provider when an onine item, e.g, a Gift Card, is voided. This prevents the third party provider activating items that have not been paid for. This is not relevant if the authorization request is snet to the provider when the transaction is completed.

The "authorizationExternalIdType" options:

* Second Barcode - indicates that the External Identifier is the number on the item's long barcode that holds additional information about the item. This barcode is scanned along with the main barcode (that holds the Item Code number) if the External Identifier is not embedded in the first barcode.
* In Barcode - indicates that the Item ID and External Identifier are embedded in the item long barcode. In this case, the Item Code and the External Identifier can be extracted only by scanning the long barcode of the Item.  
* Card - indicates that the External Identifier is embedded in the item’s magnetic stripe. The number is read when swiping the item after scanning the main barcode (that holds the Item Code number).
* External - indicates that the External Identifier is defined by the Online Purchase Group next to each item included in the group. When the Item Code is scanned, the system identifies the External Identifier. Currently not supported.

**HTTP Methods:**

* PUT - Add or update specific online product behavior by given Id
* GET - Get a single online product behavior by given Id
* DELETE - Delete specific online product behavior by given Id

## Add Online Product Behavior

The following request example shows an authorization request triggered on item sale. The {groupId} is the name of the Online Product Behavior profile. Replace the {groupId} with the relevant name.

PUT
/emerald/selling-service/c1/selling-configuration/selling_behavior/online-accounts/{groupId}

```json
Request

{
    "behaviorType": "OnlineProduct",
    "providerKey": "RGP",
    "authorizationTrigger": "ItemSale",
    "confirmationRequestRequired": "false",
    "refundRequestRequired": "false",
    "voidRequestRequired": "false",
    "authorizationExternalIdType": "card",
    "onlineAuthorizationReceiptName": "String",
    "onlineAuthorizationSaparateSlip": "false",
    "messageIdOnReceipt": "String",
    "offlineAuthorizationReceiptName": "String",
    "offlineAuthorizationSaparateSlip": "false",
    "declineAuthorizationReceiptName": "String",
    "declineAuthorizationSaparateSlip": "false",
    "businessUnits": [
        {
            "enterpriseUnitId":  "00000000000000000000000000035295"
        }
    ],
    "retailSegments": [
        "MainLane"
    ],
    "isBalanceInquiry": "false",
    "descriptions": [
        {
            "culture": "String",
            "value": "String"
        }
    ]
}
```

```json
Response Status OK
{
   OK
}
```

## Get Online Product Behaviour

Used to retrieve Online Product behavior configuration.

GET
/emerald/selling-service/c1/selling-configuration/selling_behavior/online-accounts/{groupId}

```json
Response
{
    "Id": "999",
    "behaviorType": "OnlineProduct",
    "providerKey": "RGP",
    "authorizationTrigger": "ItemSale",
    "confirmationRequestRequired": false,
    "refundRequestRequired": false,
    "voidRequestRequired": false,
    "authorizationExternalIdType": "card",
    "onlineAuthorizationReceiptName": "String",
    "onlineAuthorizationSaparateSlip": false,
    "messageIdOnReceipt": "String",
    "offlineAuthorizationReceiptName": "String",
    "offlineAuthorizationSaparateSlip": false,
    "declineAuthorizationReceiptName": "String",
    "declineAuthorizationSaparateSlip": false,
    "businessUnits": [
        {
            "enterpriseUnitId": "00000000000000000000000000035295"
        }
    ],
    "retailSegments": [
        "MainLane"
    ],
    "isBalanceInquiry": false,
    "descriptions": [
        {
            "culture": "String",
            "value": "String"
        }
    ]
}
```
