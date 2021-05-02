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

* PUT VoidLimitRules_Put

## PUT VoidLimitRules_Put

Used to add a business rule to the system.

/emerald/selling-service/c1/selling-configuration/business-rules-settings/void-limits/{ruleId}

```json

Request
{
  
}


Response
{
   
}
```
