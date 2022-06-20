
# Price Settings

## MSU Strategies

Multiple Selling Unit (MSU) is a pricing method common in the US market, which is used as an incentive to encourage customers to buy multiple units in order to get the listed price.
The pricing method defines a price for defined quantity of units (always more than 1) vs. defining a price for a single unit of an item.

Defines how cent rounding works for MSU priced items.

The options are:

* First Strategy – Adds the cent on first item (e.g. 3 for $1 => 0.34, 0.33, 0.33)
* Last Strategy – Adds the cent on last item (e.g. 3 for $1 => 0.33, 0.33, 0.34)
* AccErr005 – the cent is added when accumulated deviation crosses 0.5 cent. (e.g. 3 for 1$ => 0.33, 0.34, 0.33)

### Define the MSU configuration

In this example, the first strategy is configured.

**HTTP Methods:**

PUT

emerald/selling-configuration/price-settings/msu-price-configuration/{enterpriseUnit}

Request

```json
{
  "MsuStrategy": "First"
}
```

Response 200 OK

### Retrieve the MSU configuration

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

Request

```json
{
    "EnableSpecialPrice": "true"
}
```

Response 200 OK