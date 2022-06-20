# Hierarchy Culture

A Culture represents the language, currency, date format and weights and measures used in a region or country. Hierarchy Cultures are applied to enterprise units.

**HTTP Methods:**

* PUT
* GET
* DELETE

## Add a Culture

Used to add a culture to an enterprise unit.

PUT

/emerald/selling-service/c1/selling-configuration/hierarchy-culture/culture-settings/{enterpriseUnit}

Request

```json
{
    "cultureName": "en-US",
    "isoCurrencySymbol": "USD",
    "shortDateFormat": "MM/ddd/yyyy",
    "shortTimeFormat": "hh:mm tt",
    "currencyPositivePattern": "$n",
    "currencyNegativePattern": "($n)",
    "currencyDecimalSeparator": ".",
    "currencyGroupSeparator": ",",
    "volumeUnitOfMeasure": "0",
    "volumeUnitOfMeasurePrecision": 0,
    "volumePricePrecision": 0,
    "temperatureUnitOfMeasure": "CEL",
    "lengthUnitOfMeasure": "CMT",
    "dimensionsPrecision": "2",
    "pricePrecision": "2",
    "weightPrecision": "2",
    "quantityPrecision": "2"
}
```

Response 200 OK

## Get Hierarchy Cultures

Used to retrieve the cultures defined in the system.

GET

/emerald/selling-service/c1/selling-configuration/hierarchy-culture/culture-settings

Response

```json
{
    "lastPage": true,
    "pageNumber": 0,
    "totalPages": 1,
    "totalResults": 1,
    "pageContent": [
        {
            "enterpriseUnitId": "{enterpriseUnit}",
            "cultureName": "en-US",
            "isoCurrencySymbol": "USD",
            "shortDateFormat": "MM/ddd/yyyy",
            "shortTimeFormat": "hh:mm tt",
            "currencyPositivePattern": "$n",
            "currencyNegativePattern": "($n)",
            "currencyDecimalSeparator": ".",
            "currencyGroupSeparator": ",",
            "volumeUnitOfMeasure": "0",
            "volumeUnitOfMeasurePrecision": 0,
            "volumePricePrecision": 0,
            "temperatureUnitOfMeasure": "CEL",
            "lengthUnitOfMeasure": "CMT",
            "dimensionsPrecision": 2,
            "pricePrecision": 2,
            "weightPrecision": 2,
            "quantityPrecision": 2
        }
    ]
}
```
