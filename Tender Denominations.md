
# Tender Denominations

Denominations are set up for the cash tender for all the currencies defined in the system.

**HTTP Method:**

* PUT
* GET

## Add Cash Tender Denominations

Used to add denominations for the Cash tender. Each denomination type, e.g., note, coin, or roll is configured.

The following example shows a request to add 10 cent denomination. The currency is entered in the {currency}element in the request.

PUT

/emerald/selling-service/c1/selling-configuration/tender-settings/denomination-data/{currency}

```json
Request
{
  "denominations": [
    {
      "type": "Roll",
      "amount": 10,
      "description": "cents"
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

## Get Cash Tender Denominations

Used to retrieve the cash tender denominations.

The following example shows a request to get the denomination for the Cash USA tender.
The currency is entered in the {currency}element in the request.

GET

/emerald/selling-service/c1/selling-configuration/tender-settings/denomination-data/effective/{currency}

```json
Response Status OK
{
    "currency": "USD",
    "denominations": [
        {
            "type": "Roll",
            "amount": 10,
            "description": "cents"
        }
    ]
}
```
