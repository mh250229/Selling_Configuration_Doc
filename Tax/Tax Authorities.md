# Tax Authorities

A Tax Authority is a government entity authorized by law to assess, levy, and collect taxes. The Tax Authority determines the tax rates that need to be imposed.

## Configuring Tax Authorities

Used to configure Tax Authorities.

Tax Authority configuration is not part of the Base Configuration.

The following shows an example of Tax  Configuration required for the flows in the Selling Services.

### Tax Authority - USA

**HTTP Method:**

PUT

PUT /emerald/selling-service/selling-configuration/v1/tax-settings/authorities/USA

Request

```json
{
  "descriptions": [
    {
      "culture": "en-US",
      "value": "USA"
    }
  ]
}
```

Response  200 OK
