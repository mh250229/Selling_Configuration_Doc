
# Age Restriction Rules

Customer Age Restrictions evaluate the customer’s age usually when selling specific products, for example, alcoholic drinks, and support the following configuration:

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

**HTTP Methods:**

* PUT
* GET
* DELETE

## Add an Age Restriction Rule

Used to add an Age Restriction rule.

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
    "customerAgeRestriction": {
        "action": {
            "actionType": "approvalAction",
            "MessageId": "Age18VerificationMessage",
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

## Get an Age Restriction Rule

Used to retrieve the Age Restriction rule details.

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
                }
            },
            "tag": "{{contextType_str}}"
        }
    ]
}
```
