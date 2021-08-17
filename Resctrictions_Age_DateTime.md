
# Restrictions for Age and Date/Time

Age Restricted policies comprise of a set of restrictions based on the customer's age and date and time items are sold. There is no relation between the different restrictions.
Age Restriction rules are configured in the CCM Office and can be configured for a specific Date and Time or Week Day.

Age and Date/Time Restrictions evaluate the customer’s age when selling products based on the date and time the items are sold. For example, prohibit selling alcoholic drinks to customers under 18 after 11.00 pm.

DateTime restrictions include a prohibit or an approval action with an appropriate message.

Age verification restrictions include another action with another appropriate message. Both types of restrictions can be added on the same rule ID. If the DateTime restriction is not met or approved by the user, the age restriction may be triggered by the system.

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

* PUT - Add or update an Age Restriction rule
* GET - Get a single Age Restriction rule by given Id
* DELETE - Delete specific Age Restriction rule by given Id

## Add an Age Restriction

Used to add an Age Restriction.
The {ruleId} is the name of the age restriction.

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

Used to retrieve Age Restriction and Date Time Restriction rule details.

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

## Add an Age Restriction / Date Time Restriction

Used to add an Age Restriction with a Date Time restriction.
The {ruleId} is the name of the Age Restriction Rule.

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
        }
    },
    "tag": "{{contextType_str}}",
    "dateTimeRestriction": {
        "condition": {
            "includedDayOfWeek": [],
            "excludedDayOfWeek": [],
           "dates": [
        {
          "startDate": "2021-05-11T11:45:56.971Z",
          "endDate": "2021-07-11T11:45:56.971Z"
        }
      ],
      "times": [
        {
          "startTime": "23:00:00",
          "endTime": "03:00:00"
        }
        ]
        },
        "action": {
            "prohibitAction": {
                "actionType": "prohibit",
                "MessageId": "AlcoholSaleRestrictedMessage",
                "scope": "Transaction"
            }
        }
    },
    "customerAgeRestriction": {
        "action": {
            "actionType": "approvalAction",
            "MessageId": "Age18VerificationMessage",
            "scope": "Transaction",
            "minimalCustomerAge": "18",
            "approveRejectRequired": "true",
            "birthDateRequired": "true",
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

## Get Age Restriction / DateTime RestrictionDetails

Used to retrieve the Age Restriction and Date and Time Restrictions rule and its details.

GET

/emerald/selling-service/c1/selling-configuration//business-rules-settings/age-restrictions/AgeRestriction_DateTime

```json
Response 200 OK
{
    "dateTimeRestriction": {
        "condition": {
            "includedDayOfWeek": [],
            "excludedDayOfWeek": [],
            "dates": [
                {
                    "startDate": "2021-05-11T11:45:56.971Z",
                    "endDate": "2021-07-11T11:45:56.971Z"
                }
            ],
            "times": [
                {
                    "startTime": "23:00:00",
                    "endTime": "03:00:00"
                }
            ]
        },
        "action": {
            "prohibitAction": {
                "actionType": "ProhibitAction",
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
            "MessageId": "Age18VerificationMessage",
            "scope": "Transaction"
        }
    },
    "ruleType": "AgeRestrictionData",
    "ruleId": "AgeRestriction_DateTime",
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
        }
    },
    "tag": "{{contextType_str}}"
}
```

## Messages for the Age Restriction and DateTime Restriction Rules

A message to prompt for age verification and a message to prohibit the sale during the defined date and time can be configured for the same Rule.

**Alcohol Sale Restricted Message for this Date/time**

PUT
/emerald/selling-service/c1 /selling-configuration/message-settings/messages/AlcoholSaleRestrictedMessage 

```json

Request

{
  "messageId": "AlcoholSaleRestrictedMessage",
  "contextType": "BRM",
  "description": null,
  "name": "AlcoholSaleRestrictedMessage",
  "parts": [
    {
      "type": "Caption",
      "culture": "en-US",
      "text": "Alcohol Sale restricted"
    },
    {
      "type": "Body",
      "culture": "en-US",
      "text": "Manager approval required at this time"
    }
  ]
}
```

```json
Response 200 OK
{
   OK
}
```

**Age Verification Message**

PUT
/emerald/selling-service/c1 /selling-configuration/message-settings/messages/Age18VerificationMessage 

```json

Request

{
  "messageId": "Age18VerificationMessage",
  "contextType": "BRM",
  "description": null,
  "name": "Age18VerificationMessage",
  "parts": [
    {
      "type": "Caption",
      "culture": "en-US",
      "text": "Age Verification"
    },
    {
      "type": "Body",
      "culture": "en-US",
      "text": "Is Customer aged 18 and up?"
    }
  ]
}
```

```json
Response 200 OK
{
   OK
}
```
