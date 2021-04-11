
# Data Patterns

Defines how scanned barcode data is decomposed to fields on added items.

## Add or Update a Single Data Pattern by ID

**HTTP Method:**

PUT

/emerald/selling-configuration/data-pattern-settings/patterns/{dataPatternId}

```json
Example 
Define a data pattern to extract a 6 digit item code from a GITIN14 code with specific prefix

Request
{
            "decodedDataType": "Item",
            "encodingVariants": [],
            "extractors": [
                {
                    "extractorType": "Simple",
                    "decodedKey": "Code",
                    "decoderName": "PositionLength",
                    "extractorParameters": [
                        {
                            "name": "Position",
                            "value": "8"
                        },
                        {
                            "name": "Length",
                            "value": "6"
                        }
                    ]
                }
            ],
            "recognizers": [
                {
                    "recognizerType": "PrefixLength",
                    "decoderName": null,
                    "recognizerParameters": [
                        {
                            "name": "FromPrefix",
                            "value": "450"
                        },
                        {
                            "name": "ToPrefix",
                            "value": "460"
                        },
                        {
                            "name": "Length",
                            "value": "14"
                        }
                    ]
                }
            ],
            "validators": [],
            "allowedBusinessUnits": []
        }


Response
{
   OK
}
```
