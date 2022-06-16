# EFT Cashback

Cashback can be requested by the customer when paying with an EFT Tender.

The system supports cashback in transactions fully or partially paid for with an EFT tender, and multiple cashback requests can be added in a single transaction.

Change can be issued in transactions with Cashback that were over tendered.

Cashback requests can be voided, and declined by the EPS provider. Once an EFT tender is declined, the tender amount is not calculated in the payable/receivable amounts and a restriction is returned.

**HTTP Methods:**

* PUT - Save or update the Tender ID used for Cashback.
* GET - Retrieve the Tender ID used for Cashback for a specific Enterprise Unit or for the closest Enterprise Unit defined with the Cashback Tender ID.

## Configuring the Cashback Tender

**HTTP Methods:**

PUT

/emerald/selling-service/selling-configuration/v1/tender-settings/cash-back

Request

```json
{
  "CashbackTenders": [
    {
      "tenderId": "1",
      "enterpriseUnitId": null
    }
  ]
}
```

Response 200 OK