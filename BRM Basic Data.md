# BRM Basic Data

Once all business rules are set up, you can use the following services to retrieve one or all business rules, and delete a business rule from the system

**HTTP Methods:**

- GET BusinessRules_GetAll
- DELETE BusinessRules_Delete
- GET BusinessRulesGet

## GET BusinessRules_GetAll

Used to retrieve all the business rules set up in the system.

/emerald/selling-service/c1/selling-configuration/business-rules-settings/rules

```json

Request
{
  
}


Response
{
   OK
}
```

## GET BusinessRules_Get

Used to retrieve a specific business rule set up in the system.

/emerald/selling-service/c1/selling-configuration/business-rules-settings/rules/{ruleId}

```json

Request
{
  
}


Response
{
   OK
}
```

## GET BusinessRules_Delete

Used to delete a business rule set up in the system.

/emerald/selling-service/c1/selling-configuration/business-rules-settings/rules/{ruleId}

```json

Request
{
  
}


Response
{
   OK
}
```
