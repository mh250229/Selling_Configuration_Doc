
# Tax Authorities

Tax Authorities are government entities authorized by law to assess, levy, and collect taxes.

The Tax Authority determines the tax rates that need to be imposed.

**HTTP Methods:**

* PUT
* GET
* DELETE

## Add Tax Authorities

Used to add Tax Authorities.

PUT

/emerald/selling-service/c1/selling-configuration/tax-settings/authorities/effective-authorities

```json
Request
{
  "descriptions": [
    {
      "culture": "en-US",
      "value": "USA"
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

## Get Tax Authorities

Used to retrieve Tax Authorities details.

GET

/emerald/selling-service/c1/selling-configuration/tax-settings/authorities/effective-authorities

```json
Response Status OK
{
    "authorityId": "1",
    "descriptions": [
        {
            "culture": "en-US",
            "value": "USA"
        }
    ]
}
```
