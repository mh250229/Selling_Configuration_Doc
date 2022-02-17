# Tender Exchange Gets

## Getting All Tender Exchange Configuration

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

## Getting a Tender Exchange Configuration by the Given ID

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

## Getting a Tender Exchange Configuration by the Effective Tender Exchange

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

## Deleting a Tender Exchange Configuration

**HTTP Method:**

DELETE
/emerald/selling-service/selling-configuration/v1/tender-settings/tender-exchange/{tenderExchangeId}

Replace the field {tenderExchangeId} with the ID of the Tender Exchange you are deleting, e.g., 1

Response:

200 OK
