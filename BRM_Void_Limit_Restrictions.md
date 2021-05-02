# BRM Void Limit Restrictions

The Cart API supports the Void Item BRM.
The BRM evaluates the items voided in a cart.
A 'Void item' restriction is created once one of the following criteria are met:

* Voided line amount > Max allowed amount per line
* Voided ticket amount >Max allowed amount per ticket

Both criteria can be configured together.
The maximum allowed limit can be any positive value including 0.
A Void item BRM includes:

* Rule Id
* Rule type- "VoidLimitBehavior"
* Applied on :Voideditem
* Max allowed amount per line
* Max allowed amount per ticket
* Action type:

  * Restricted audit line id
  * Original line id

If the client uses the 'Enforce' flag (instead of inform), the item is not removed from the cart until the restriction is resolved.
If the ‘Enforce’ flag is not used, the item is removed and captured in the audit line and the restriction is created.
The following Action type options are supported by the Void Item BRM:

* Approval required
* Select reason
* Prompt for confirmation
* Input data required
* Notification

The Cart status cannot be updated to Tender while the cart contains restrictions. If the client attempts to update the cart status, the following error is returned.
ErrorCode "CartContainRestrictions"
Message "Cart contains restriction"

**HTTP Methods:**

* PUT Message_PUT
* GET Message_Get

## GET BusinessRules_GetAll

Used to retrieve all the business rules set up in the system.

/emerald/selling-service/c1/selling-configuration/message-settings/messages/{messageId}

```json

Request
{
  
}


Response
{
   OK
}
```
