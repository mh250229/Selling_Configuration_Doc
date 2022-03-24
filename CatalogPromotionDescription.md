# Catalog Promotion Description by Promotion Type Mapping Configuration

There are 2 basic discount prices:

* Any consumer discount, e.g. a Temporary Reduced Price (TPR), Advertisement sale, store discount, Reduced to Clear (RTC), etc.
* Card Price – discount only for club/loyalty members.

The NCR catalog can hold two prices for an item: Base or Special. A special price is always used over a regular price.
If an item has a special price, the Emerald Selling Services uses it as the item price.
Special prices can have any one of the following values:

* None/Blank
* NON_CARD_PRICE
* CARD_PRICE

There can be 2 special prices effective for different promotionpricetype values at a time.

The promotion description is configurable.

**HTTP Methods:**
**PUT** – to save or update the promotion descriptions by promotion type mapping configuration
**GET** – to retrieve relevant promotion descriptions by promotion type Mapping Configuration

When the pricing data for an Item has a promotion of type MEMBER_PRICE/'TEMP_PRICE_REDUCTION, the promotion text is printed on the receipt according to the configuration:

* If the type = 'MEMBER_PRICE', then the promotion name is presented as "loyalty Discount" .
* If the type = 'TEMP_PRICE_REDUCTION', then the promotion name is presented as "Non Loyalty Discount".
The price is displayed on the receipt according to the price presented in the cart according to the price logic in this feature.

## Add/Update Special Price Promotion Descriptions

The request contains a list of promotion types and an array of descriptions for each.
 
**HTTP Method:**

PUT
/emerald/selling-service/selling-configuration/v1/promotion-settings/promotion-type-description

Request

```json
{"promotionTypeDescriptions":[{"promotionType":"MEMBER_PRICE","descriptions":[{"culture":"en_US","value":"other member description"}]},{"promotionType":"TEMP_PRICE_REDUCTION","descriptions":[{"culture":"en_US","value":"Non Loyalty Discount"}]}]}
```

Response 200 OK

## Get the Special Price Promotion Descriptions

**HTTP Method:**

GET
/emerald/selling-service/selling-configuration/v1/promotion-settings/promotion-type-description

Request

```json
{
    "promotionTypeDescriptions": [
        {
            "promotionType": "MEMBER_PRICE",
            "descriptions": [
                {
                    "culture": "en_US",
                    "value": "other member description"
                }
            ]
        },
        {
            "promotionType": "TEMP_PRICE_REDUCTION",
            "descriptions": [
                {
                    "culture": "en_US",
                    "value": "Non Loyalty Discount"
                }
            ]
        }
    ]
}
```
