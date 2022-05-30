# Endorsement

Checks and vouchers can be endorsed automatically once the check is placed in the printer, or manually by the cashier.

Checks and Vouchers can be endorsed on the Front, Back, or both Front and Back. This depends on the following configuration:

- ReceiptLinesFront
- ReceiptLinesBack.

**HTTP Methods:**

- PUT - Add or update specific endorsement configuration by given Id
- GET - Get all or a single endorsement configuration by given Id
- DELETE - Delete specific endorsement configuration by given Id

## Adding endorsement configuration

PUT

/emerald/selling-service/selling-configuration/v1/receipt-settings/endorsement/xlr-8568_1

Request

```json
{
    "id": "xlr-8568_1",
    "displayName": "Check Endorsement",
    "receiptLinesFront": [
        {
            "lineDefinitionName": "FrontHeader3",
            "templateName": "FrontHeader3"
        },
        {
            "lineDefinitionName": "FrontMessage",
            "templateName": "FrontMessage"
        },
        {
            "lineDefinitionName": "FrontTender3",
            "templateName": "FrontTender3"
        }
    ],
    "receiptLinesBack": [
        {
            "lineDefinitionName": "BackHeader3",
            "templateName": "BackHeader3"
        },
        {
            "lineDefinitionName": "BackTender3",
            "templateName": "BackTender3"
        }
    ],
    "tenders": ["50","51"],
    "enterpriseUnitIds": ["0000000000000000"]
}
```

Response 200 OK

## Get all endorsement configuration

GET

/emerald/selling-service/selling-configuration/v1/receipt-settings/endorsement/

Response

```json
{
    "lastPage": true,
    "pageNumber": 0,
    "totalPages": 1,
    "totalResults": 2,
    "pageContent": [{
        "endorsementId": "CheckEndorsement",
        "id": "CheckEndorsement",
        "displayName": "CheckEndorsement Non Ecc",
        "receiptLinesFront": [{
            "lineDefinitionName": "FrontHeader1",
            "templateName": "FrontHeader1",
            "layout": null,
            "section": null
        }, {
            "lineDefinitionName": "FrontMessage",
            "templateName": "FrontMessage",
            "layout": null,
            "section": null
        }, {
            "lineDefinitionName": "FrontTender1",
            "templateName": "FrontTender1",
            "layout": null,
            "section": null
        }],
        "receiptLinesBack": [{
            "lineDefinitionName": "BackHeader1",
            "templateName": "BackHeader1",
            "layout": null,
            "section": null
        }, {
            "lineDefinitionName": "BackTender1",
            "templateName": "BackTender1",
            "layout": null,
            "section": null
        }],
        "tenders": ["50"],
        "enterpriseUnitIds": []
    }, {
        "endorsementId": "xlr-8568_1",
        "id": "xlr-8568_1",
        "displayName": "Check Endorsement",
        "receiptLinesFront": [{
            "lineDefinitionName": "FrontHeader3",
            "templateName": "FrontHeader3",
            "layout": null,
            "section": null
        }, {
            "lineDefinitionName": "FrontMessage",
            "templateName": "FrontMessage",
            "layout": null,
            "section": null
        }, {
            "lineDefinitionName": "FrontTender3",
            "templateName": "FrontTender3",
            "layout": null,
            "section": null
        }],
        "receiptLinesBack": [{
            "lineDefinitionName": "BackHeader3",
            "templateName": "BackHeader3",
            "layout": null,
            "section": null
        }, {
            "lineDefinitionName": "BackTender3",
            "templateName": "BackTender3",
            "layout": null,
            "section": null
        }],
        "tenders": ["50", "51"],
        "enterpriseUnitIds": ["0000000000000000"]
    }]
}
```

## Get endorsement configuration by specific Id

GET

/emerald/selling-service/selling-configuration/v1/receipt-settings/endorsement/xlr-8568_1

Response

```json
{
    "endorsementId": "xlr-8568_1",
    "id": "xlr-8568_1",
    "displayName": "Check Endorsement",
    "receiptLinesFront": [{
        "lineDefinitionName": "FrontHeader3",
        "templateName": "FrontHeader3",
        "layout": null,
        "section": null
    }, {
        "lineDefinitionName": "FrontMessage",
        "templateName": "FrontMessage",
        "layout": null,
        "section": null
    }, {
        "lineDefinitionName": "FrontTender3",
        "templateName": "FrontTender3",
        "layout": null,
        "section": null
    }],
    "receiptLinesBack": [{
        "lineDefinitionName": "BackHeader3",
        "templateName": "BackHeader3",
        "layout": null,
        "section": null
    }, {
        "lineDefinitionName": "BackTender3",
        "templateName": "BackTender3",
        "layout": null,
        "section": null
    }],
    "tenders": ["50", "51"],
    "enterpriseUnitIds": ["0000000000000000"]
}
```
