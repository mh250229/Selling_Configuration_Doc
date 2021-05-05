# Action Types

Action Types define the action performed to handle a Business Rules and Age Restrictions.

The following Action Types are supported:

* Prohibit
* Approval Required
* Select Reason
* Enter Loyalty Card
* Prompt for Confirmation
* Input data required
* Notification

**HTTP Methods:**

* PUT
* GET

The following examples show adding an Action Type to the Void Limits BRM

## Add Prohibit Action

Used to add a Prohibit Action Type to a BRM or Age Restriction.

PUT

/emerald/selling-service/c1/selling-configuration/business-rules-settings/void-limits/{ruleId}/prohibit-action

```json
Request
{
    "scope": "Request",
    "actionType": "Prohibit",
    "MessageId": "Void is Prohibited"
}
```

```json
Response Status OK
{
   OK
}
```

## Get Prohibit Action

Used to retrieve Prohibit Action Type details.

GET

/emerald/selling-service/c1/selling-configuration/business-rules-settings/void-limits/{ruleId}/prohibit-action

```json
Response Status OK
{
    "actionType": "ProhibitAction",
    "MessageId": "Void is Prohibited",
    "scope": "Request"
}
```

## Add Approval Required Action

Used to add an Approval Required Action Type to a BRM or Age Restriction.

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
```

```json
Response Status OK
{
   OK
}
```

## Add Select Reason Action

Used to add a Select Reason Action Type to a BRM or Age Restriction.

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
```

```json
Response Status OK
{
   OK
}
```

## Add Confirmation Action

Used to add a Confirmation Action Type to a BRM or Age Restriction.

PUT

/emerald/selling-service/c1/selling-configuration/business-rules-settings/void-limits/{ruleId}/confirmation-action

```json
Request
{
    "scope": "Request",
    "actionType": "ConfirmationAction",
    "MessageId": "Confirmation Required"
}
```

```json
Response Status OK
{
   OK
}
```

## Add Input Data Required Action

Used to add an Input Data Action Type to a BRM or Age Restriction.

PUT

/emerald/selling-service/c1/selling-configuration/business-rules-settings/void-limits/{ruleId}/confirmation-action

```json
Request
{
    "inputLabel": "Birthdate",
    "inputName": "AgeRestrictionData",
    "inputType": {
        "inputType": "Date"
    },
    "scope": "Request",
    "actionType": "InputDataRequired",
    "MessageId": "AlcoholSaleRestrictedMessage"
}
```

```json
Response Status OK
{
   OK
}
```

## Add Notification

Used to add a Notification Action Type to a BRM or Age Restriction.

PUT

/emerald/selling-service/c1/selling-configuration/business-rules-settings/void-limits/{ruleId}/notification-action

```json
Request
{
    "scope": "Request",
    "actionType": "NotificationAction",
    "MessageId": "Item cannot be voided"
}
```

```json
Response Status OK
{
   OK
}
```
