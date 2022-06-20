# Currency Exchange Rates

Exchange rates define the foreign exchange rate for each tender not defined as the local currency.

**HTTP Method:**

* PUT
* GET

## Add Currency Exchange Rates

Used to add foreign exchange rates.

The following example shows a request to define the exchange rate when converting USD to EUR.

PUT

/emerald/selling-service/c1/selling-configuration/tender-settings/currency-exchange-rates/{rateId}

Request

```json
{
  "PaymentCurrencySymbol": "USD",
  "PurchaseCurrencySymbol": "EUR",
  "PurchaseRate": 1.101,
  "EffectiveDate": "2021-05-06T13:52:16.037Z"
}
```

Response 200 OK

## Get Curency Exchange Rates

Used to retrieve the currecy exchange rate details.

GET

/emerald/selling-service/c1/selling-configuration/tender-settings/currency-exchange-rates/{rateId}

Response

```json
{
    "Id": "{rateId}",
    "LastUpdateDate": "2021-05-09T07:49:02.2078363Z",
    "PaymentCurrencySymbol": "USD",
    "PurchaseCurrencySymbol": "EUR",
    "PurchaseRate": 1.101,
    "EffectiveDate": "2021-05-06T13:52:16.037Z"
}
```
