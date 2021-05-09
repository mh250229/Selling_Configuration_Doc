
# BRM Age Restriction

The Cart API supports Customer Age and Date/Time Restrictions.

Age Restriction rules are configured in the CCM Office and can be configured for a specific Date and Time or Week Day.

Age and Date/Time Restrictions evaluate the customer’s age when selling products based on the date and time the items are sold. For example, prohibit selling alcoholic drinks to customers under 20 after 12.00 am.

DateTime restrictions include a prohibit or an approval action with an appropriate message.

Age verification restrictions include another action with another appropriate message. IBoth types of restrictions can be added on the same rule ID. If the DateTime restriction is not met or approved by the user, the age restriction may be triggered by the system.

Age and Date/Time Restrictions support the following configuration:

* Location Conditions
  * Include business unit
  * Exclude business unit
* Touchpoints Groups Condition
  * Include Touchpoint Group
  * Excluded Touchpoint Groups
* Product Conditions
  * Include Products/Categories/Groups
  * Exclude Products/Categories/Groups
* Scope – Transaction

Customer Age Restrictions are set up as follows:

* Action Type (Mandatory)
* Message ID
* Scope (Mandatory)= transaction
* Minimal Customer Age (Mandatory)
* Approve\ Reject Required (Mandatory)
* Birth Date required (Mandatory)
* Reject Reason Code

DateTime restrictions are set up as follows:

* Description
* Dates
* Times
* Included Week day
* Excluded Week day
* DateTime Restriction Action (Mandatory) :
  * Prohibit or Approval action
    * Action Type
    * Message ID
    * Scope (M)
    * Authorized Roles (Mandatory for approval action only)

**HTTP Methods:**

* PUT
* GET
* DELETE

## Add an Age Restriction  with Date Time Restriction

Used to add an Age Restriction with a Date Time restriction.

PUT
/emerald/selling-service/c1/selling-configuration/business-rules-settings/age-restrictions/{ruleId}

```json

Request
{
    "conditions": {
        "locationCondition": {
            "includedLocations": [
                {
                    "enterpriseUnitId": "{{nep-enterprise-unit}}"
                }
            ]
        },
        "productCondition": {
            "includedProducts": [
                {
                    "value": "Carlsberg Beer"
                }
            ]
        },
        "customerOrderCondition": {
            "maxQuantity": "2"
        }
    },
    "tag": "{{contextType_str}}",
    "dateTimeRestriction": {
        "action": {
            "approvalAction": {
                "actionType": "ApprovalAction",
                "MessageId": "AlcoholSaleRestrictedMessage",
                "scope": "Transaction",
                "authorizedRoles": [
                    "Manager", "Supervisor"
                ]
            }
        }
    },
    "customerAgeRestriction": {
        "action": {
            "actionType": "ApprovalAction",
            "MessageId": "Supervisor Approval Required",
            "scope": "Transaction",
            "minimalCustomerAge": "18",
            "approveRejectRequired": "True",
            "birthDateRequired": "True",
            "rejectReasonCode": [
                "Under Age",
                "No ID"
            ]
        }
    }
}

```

```json
Response 200 OK
{
   OK
}
```

## Get Age Restriction Details

Used to retrieve Age Restriction rule details.

GET

/emerald/selling-service/c1/selling-configuration/business-rules-settings/age-restrictions

```json
Response 200 OK
{
    "lastPage": true,
    "pageNumber": 0,
    "totalPages": 1,
    "totalResults": 1,
    "pageContent": [
        {
            "dateTimeRestriction": {
                "action": {
                    "approvalAction": {
                        "actionType": "ApprovalAction",
                        "authorizedRoles": [
                            "Manager",
                            "Supervisor"
                        ],
                        "MessageId": "AlcoholSaleRestrictedMessage",
                        "scope": "Transaction"
                    }
                }
            },
            "customerAgeRestriction": {
                "action": {
                    "actionType": "AgeConfirmationAction",
                    "minimalCustomerAge": 18,
                    "approveRejectRequired": true,
                    "birthDateRequired": true,
                    "rejectReasonCode": [
                        "Under Age",
                        "No ID"
                    ],
                    "MessageId": "Supervisor Approval Required",
                    "scope": "Transaction"
                }
            },
            "ruleType": "AgeRestrictionData",
            "ruleId": "{ruleId}",
            "actionType": null,
            "conditions": {
                "locationCondition": {
                    "includedLocations": [
                        {
                            "enterpriseUnitId": "00000000000000000000000000035295"
                        }
                    ]
                },
                "productCondition": {
                    "includedProducts": [
                        {
                            "value": "Carlsberg Beer"
                        }
                    ]
                },
                "customerOrderCondition": {
                    "maxQuantity": 2
                }
            },
            "tag": "{{contextType_str}}"
        }
    ]
}
```
