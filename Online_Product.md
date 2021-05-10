# Online Product Behavior

The Online Purchase services are used to define new Online Purchase Profiles in the system. Define the communication settings, specify the receipt printed in the transaction in online, offline or decline scenarios.
Receipts must be set up prior to configuring the online product behavior.

**HTTP Methods:**

- PUT Add or update specific online product behavior by given Id
- GET Get a single online product behavior by given Id
- DELETE Delete specific online product behavior by given Id

## Add Online Product - Activation triggered upon Item Sale

When an online item is added to a cart, the selling service verifies if the item is associated to an Online Purchase Group.
The item is added to the cart with the Readytotender parameter set to False.
The following restrictions are created separately (one by one):

**External ID Required** - The restriction is created with the Online Purchase Group ID. The client retrieves the ExternalUniqueIdentifier, for example, Card, InBarcode, Second Barcode from the Online Purchase Group configuration.

**Note:**
If the ExternalId is InBarcode, an ExternalUniqueIdentifier data pattern is required to extract the External id.

**For example:**
Restriction ID -External Id Required
Restriction Description - Online Item External Id Required
Online product behavior group ID
Restricted lines
The restriction is removed once the item is updated with External ID or item is voided.

**Online Item Authorization Required** – This restriction is created once the restriction above is solved. The restriction is created with the Online Purchase Group ID. The client retrieves all the online item details from the Online Purchase Group configurations. group id, so the client is able to approach the online purchase group configuration and get all the relevant online item configurations. 
For example
Restriction ID - Online Item Authorization Required
Restriction Description - Online Item Authorization Required
Online product behavior group ID
Restricted lines
The restriction must be resolved before the cart status is updated to 'tender', and is removed once the item is voided or activated successfully.
Once the online item is activated successfully, the item authorization is updated. 
The Online Authorization Required restriction is removed.
The ‘ready to tender’ parameter is updated to True.
Online items can be voided.
The cart status cannot be updated to Void or Suspend if the cart contains activated online items. If the cart status is updated, an error message is returned.

PUT
/emerald/selling-service/c1/selling-configuration/selling_behavior/online-accounts/{groupId}

The following example shows a request to add the online product behavior activated on item sale.

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
        "String"
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
