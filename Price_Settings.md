
# Price Settings

## MSU Strategies

Multiple Selling Unit (MSU) is a pricing method common in the US market, which is used as an incentive to encourage customers to buy multiple units in order to get the listed price.
The pricing method defines a price for defined quantity of units (always more than 1) vs. defining a price for a single unit of an item.

Defines how cent rounding works for MSU priced items.
The options are:

* First – Added cent on first item (e.g. 3 for 1$ => 0.34, 0.33, 0.33)
* Last – Added Cent on last Item (e.g. 3 for 1$ => 0.33, 0.33, 0.34)
* AccErr005 – Cent is added when accumulated deviation crosses 0.5 cent. (e.g. 3 for 1$ => 0.33, 0.34, 0.33)

**HTTP Methods:**

  PUT

emerald/selling-configuration/price-settings/msu-price-configuration/{enterpriseUnit}

```json
Example: First Strategy
The cent is added on the first item (e.g. 3 for 1$ => 0.34, 0.33, 0.33)

Request
{
  "MsuStrategy": "First"
}


Response
{
   OK
}
```

GET
/emerald/selling-service/c1/selling-configuration/price-settings/msu-price-configuration

Response

```json

{
    "lastPage": true,
    "pageNumber": 0,
    "totalPages": 1,
    "totalResults": 2,
    "pageContent": [
        {
            "enterpriseUnit": "00000000000000000000000000000000",
            "configuration": {
                "MsuStrategy": "First"
            }
        },
        {
            "enterpriseUnit": "{enterpriseUnit}",
            "configuration": {
                "MsuStrategy": "First"
            }
        }
    ]
}
```

## Special Pricing

Indicates a discounted item price when, for example, the item is on promotion (TPR). The Special Price always overrides the item's regular price.

**HTTP Methods:**

  PUT

/emerald/selling-service/c1/selling-configuration/price-settings/special-price-configuration/{enterpriseUnit}

```json

Request
{
    "EnableSpecialPrice": "true"
}


Response
{
   OK
}
```
