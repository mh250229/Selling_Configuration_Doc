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

**HTTP Methods:**

* PUT VoidLimitRules_Put
* GET VoidLimitRules_Get
* PUT Put prohibit Actions for Void Limit Restrictions
* GET Put prohibit Actions for Void Limit Restrictions

## Void Item Business Rule

Create the void item business rule.

PUT
/emerald/selling-service/c1/selling-configuration/business-rules-settings/void-limits/{ruleId}

```json

Request
{
"maxAllowedAmountperLine": 50.0,
    "conditions": {
        "locationCondition": {
            "includedLocations": [{
                    "enterpriseUnitId": "{{nep-enterprise-unit}}"
                }
            ]
        },
        "productCondition": {
            "includedProducts": [{
                    "value": "{{includedItemId}}"
                }
            ]
        },
        "customerOrderCondition": {
            "{{customerOrderConditionKey}}": "{{customerOrderConditionValue}}"
        }
    },
    "tag": "{{contextType}}"
}


Response 200 OK
{
   OK
}
```

Add the relevant Action Type.

Prerequisite: Create a Message. See Messages.

PUT
/emerald/selling-service/c1/selling-configuration/business-rules-settings/void-limits/{ruleId}/prohibit-action

```json
Request
{
    "scope": "Request",
    "actionType": "Prohibit",
    "MessageId": "Void is Prohibited"
}

Response 200 OK
{
   OK
}
```

PUT
/emerald/selling-service/c1/selling-configuration/business-rules-settings/void-limits/{ruleId}/approval-action

```json
Request
{
    "authorizedRoles": [
        "Supervisor"
    ],
    "scope": "Request",
    "actionType": "ApprovalAction",
    "MessageId": "Supervisor Approval Required"
}

Response 200 OK
{
   OK
}
```

PUT
/emerald/selling-service/c1/selling-configuration/business-rules-settings/void-limits/{ruleId}/confirmation-action

```json
Request
{
    "scope": "Request",
    "actionType": "ConfirmationAction",
    "MessageId": "Confirmation Required"
}

Response 200 OK
{
   OK
}
```

PUT
/emerald/selling-service/c1/selling-configuration/business-rules-settings/void-limits/{ruleId}/notification-action

```json
Request
{
    "scope": "Request",
    "actionType": "NotificationAction",
    "MessageId": "Item cannot be voided"
}

Response 200 OK
{
   OK
}
```

PUT
/emerald/selling-service/c1/selling-configuration/business-rules-settings/void-limits/{ruleId}/input-data-action

```json
Request
{
    "inputLabel": "{{ruleId}}",
    "inputName": "{{ruleId}}",
    "inputType": {
        "inputType": "{{inputType}}"
    },
    "scope": "Request",
    "actionType": "{{actionType}}",
    "MessageId": "{{messageId}}"
}

Response 200 OK
{
   OK
}
```

PUT
/emerald/selling-service/c1/selling-configuration/business-rules-settings/void-limits/{ruleId}/reason-code-action

```json
Request
{
    "reasonCodeIds": [
        "11017",
        "11016",
        "11015"
    ],
    "scope": "Request",
    "actionType": "ReasonCodeAction",
    "MessageId": "VoidLimit_SelectReasonCode"
}

Response 200 OK
{
   OK
}
```
