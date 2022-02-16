# Tender Exchange

Tender exchange enables customers to purchase a tender and pay for it with another tender, e.g. paying with visa and get cash.  There are various business motivations for Tender Exchange.
For example: In a Cash withdrawal service, the Customer pays with an EFT card and gets a refund with cash.
In a Tender correction, the customers pay with Visa for Goods and requests to swap the payment method with a different payment mean.

**HTTP Methods:**

* PUT- Save or Update TenderExchage
* GET - Get all Tender Exchange
* GET - Get all Tender Exchange by given ID

This method enables two options, and both enable the system to perform a Tender Exchange Lookup according to the Tender Exchange ID.
/tender-settings/tender-exchange/effective/{tenderExchangeId}
If this option is used, the API provided does not actually check the org, EU, store, and POSApplication for the "effective" tender exchange.
/tender-settings/tender-exchange/{tenderExchangeId}

* DELETE - Delete a single TenderExchange
  
## Add Configuration for a Cash Withdrawal Tender Exchange

**HTTP Method:**

PUT
/emerald/selling-service/selling-configuration/v1/tender-settings/tender-exchange/{tenderExchangeId}

Request

```json
{
    "name": "CashWithdrawal",
    "multiplesOf": 0,
    "minAmount": 0,
    "maxAmount": 0,
    "payableTendersIds": [
		"10",
		"11",
		"12",
		"13"
    ],
    "receivableTendersIds": [
        "1"
    ],
    "isCashout": false
}
```

Response:

200 OK

## Add Configuration for a Tender Correction Tender Exchange

**HTTP Method:**

PUT
/emerald/selling-service/selling-configuration/v1/tender-settings/tender-exchange/{tenderExchangeId}

Request

```json
{
    "name": "TenderCorrection",
    "multiplesOf": 0,
    "minAmount": 0,
    "maxAmount": 0,
    "payableTendersIds": [
        "1",
		"10",
		"11",
		"12"
    ],
    "receivableTendersIds": [
        "1",
		"10",
		"11",
		"12"
    ],
    "isCashout": false
}
```

Response:

200 OK

## Add Configuration for a Coinstar to Cash Tender Exchange

**HTTP Method:**

PUT
/emerald/selling-service/selling-configuration/v1/tender-settings/tender-exchange/{tenderExchangeId}

Request

```json
{
    "name": "CoinstarToCash",
    "multiplesOf": 0,
    "minAmount": 0,
    "maxAmount": 0,
    "payableTendersIds": [
        "81"
    ],
    "receivableTendersIds": [
        "1"
    ],
    "isCashout": false
}
```

Response:

200 OK