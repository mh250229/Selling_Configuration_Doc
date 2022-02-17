# Tender Exchange

Tender exchange enables customers to purchase a tender and pay for it with another tender, e.g. paying with visa and get cash.  There are various business motivations for Tender Exchange.
For example: In a Cash withdrawal service, the Customer pays with an EFT card and gets a refund with cash.
In a Tender correction, the customers pay with Visa for Goods and requests to swap the payment method with a different payment mean.
A Tender Exchange entity is identified by an ID and a Name.
Each Tender exchange entity reflects a function/command that can be executed at the POS in no-sale mode. It should be defined in the command menu.
Tender Exchange configuration is strictly performed in the CCM.
The definition includes the following attributes:

* Minimum amount for the exchange
* Maximum amount for the exchange
* Exchange amount must be 'Multiples of'
* Refund tenders – a list of tenders from which the cashier will select the refund tender
* Pays with tenders – a list of tenders from which cashier will select the paying tender

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

The {tenderExchangeId} represents the ID number but is not mandatory.
You can replace the {tenderExchangeId} with an ID number, e.g., specify that the CashWithdrawal has ID 2.

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

## Get All Tender Exchange Configuration

**HTTP Method:**

GET
/emerald/selling-service/selling-configuration/v1/tender-settings/tender-exchange

The following example shows a Get All. The system retrieves all the Tender Exchange configurations set up in the system.
If there is no Tender Exchange ID number assigned to the Tender Exchange, the field shows {tenderExchangeId}.

Response:

```json
{
    "lastPage": true,
    "pageNumber": 0,
    "totalPages": 1,
    "totalResults": 4,
    "pageContent": [
        {
            "tenderExchangeId": "{tenderExchangeId}",
            "name": "CoinstarToCash",
            "multiplesOf": 0,
            "minAmount": 0.0,
            "maxAmount": 0.0,
            "payableTendersIds": [
                "81"
            ],
            "receivableTendersIds": [
                "1"
            ],
            "isCashout": false
        },
        {
            "tenderExchangeId": "1",
            "name": "TenderCorrection",
            "multiplesOf": 0,
            "minAmount": 0.0,
            "maxAmount": 0.0,
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
        },
        {
            "tenderExchangeId": "2",
            "name": "CashWithdrawal",
            "multiplesOf": 0,
            "minAmount": 0.0,
            "maxAmount": 0.0,
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
        },
        {
            "tenderExchangeId": "3",
            "name": "test",
            "multiplesOf": 1,
            "minAmount": 1.0,
            "maxAmount": 4.0,
            "payableTendersIds": [
                "string"
            ],
            "receivableTendersIds": [
                "string"
            ],
            "isCashout": true
        }
    ]
}

```

## Get a Tender Exchange Configuration by the Given ID

**HTTP Method:**

GET
/emerald/selling-service/selling-configuration/v1/tender-settings/tender-exchange/1

The following example shows how to retrieve a Tender Exchange configuration by the Tender Exchange ID. In this example, TenderCorrection is {tenderExchangeId}, which is defined a 1.

Response:

```json
{
    "tenderExchangeId": "1",
    "name": "TenderCorrection",
    "multiplesOf": 0,
    "minAmount": 0.0,
    "maxAmount": 0.0,
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

## Get a Tender Exchange Configuration by the Effective Tender Exchange

**HTTP Method:**

GET
/emerald/selling-service/selling-configuration/v1/tender-settings/tender-exchange/effective/{tenderExchangeId}

The following example shows how to retrieve a Tender Exchange configuration by the Effective Tender Exchange ID.

Response:

```json
{
    "tenderExchangeId": "{tenderExchangeId}",
    "name": "CoinstarToCash",
    "multiplesOf": 0,
    "minAmount": 0.0,
    "maxAmount": 0.0,
    "payableTendersIds": [
        "81"
    ],
    "receivableTendersIds": [
        "1"
    ],
    "isCashout": false
}
```

## Delete a Tender Exchange Configuration

**HTTP Method:**

DELETE
/emerald/selling-service/selling-configuration/v1/tender-settings/tender-exchange/{tenderExchangeId}

Replace the field {tenderExchangeId} with the ID of the Tender Exchange you are deleting, e.g., 1

Response:

200 OK
