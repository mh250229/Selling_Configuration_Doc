
# Taxes

Tax Exemptions are issued by Tax Authorities, and are performed at the transaction (Cart) level.

Tax Exemptions can be reversed.

**HTTP Methods:**

* PUT Tax Exemptions
* PUT Tax Parameters to capture Customer ID and Name of customers eligible for tax exemptions
* GET
* DELETE

## Add Tax Rates Exemption

Used to add Tax Exemptions.

PUT

/emerald/selling-service/c1/selling-configuration/tax-settings/exemptions/{exemptionId}

```json
Request
{
    "taxAuthority": "USA",
    "descriptions": [
        {
            "culture": "en-US",
            "value": "First Exemption"
        }
    ],
    "exemptionConditions": {
        "exemptByTender": [
            "null"
        ],
        "exemptByDiscountAuthority": false,
        "exemptByAuthority": true,
        "exemptByTaxRate": [
            "null"
        ]
    },
    "ExemptionMethod": {
        "exemptionMethodType": "FullExemption",
        "imposition": "null",
        "percentage": null
    }
}
```

```json
Response Status OK
{
   OK
}
```

## Get Tax Exemptions

Used to retrieve Tax Exemption details.

GET

/emerald/selling-service/c1/selling-configuration/tax-settings/exemptions/{exemptionId}

```json
Response Status OK
<TaxExemptionData xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">
    <TaxAuthority>USA</TaxAuthority>
    <Descriptions>
        <Description>
            <Culture>String</Culture>
            <Value>First Exemption</Value>
        </Description>
    </Descriptions>
    <ExemptionConditions>
        <ExemptByTender>
            <string>null</string>
        </ExemptByTender>
        <ExemptByDiscountAuthority>false</ExemptByDiscountAuthority>
        <ExemptByAuthority>true</ExemptByAuthority>
        <ExemptByTaxRate>
            <string>null</string>
        </ExemptByTaxRate>
    </ExemptionConditions>
    <ExemptionMethod>
        <ExemptionMethodType>Discount</ExemptionMethodType>
        <Imposition>null</Imposition>
        <Percentage>21.15</Percentage>
    </ExemptionMethod>
    <ExemptionId>{exemptionId}</ExemptionId>
</TaxExemptionData>
```

## Get All Tax Exemptions

Used to retrieve all the details of all Tax Exemptions.

GET

/emerald/selling-service/c1/selling-configuration/tax-settings/exemptions

```json
Response Status OK
<TaxExemptionResponse xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">
    <LastPage>true</LastPage>
    <PageNumber>0</PageNumber>
    <TotalPages>1</TotalPages>
    <TotalResults>3</TotalResults>
    <PageContent>
        <TaxExemptionData>
            <TaxAuthority>USA</TaxAuthority>
            <Descriptions>
                <Description>
                    <Culture>String</Culture>
                    <Value>First Exemption</Value>
                </Description>
            </Descriptions>
            <ExemptionConditions>
                <ExemptByTender>
                    <string>null</string>
                </ExemptByTender>
                <ExemptByDiscountAuthority>false</ExemptByDiscountAuthority>
                <ExemptByAuthority>true</ExemptByAuthority>
                <ExemptByTaxRate>
                    <string>null</string>
                </ExemptByTaxRate>
            </ExemptionConditions>
            <ExemptionMethod>
                <ExemptionMethodType>Discount</ExemptionMethodType>
                <Imposition>null</Imposition>
                <Percentage>21.0</Percentage>
            </ExemptionMethod>
            <ExemptionId>1</ExemptionId>
        </TaxExemptionData>
        <TaxExemptionData>
            <TaxAuthority>USA</TaxAuthority>
            <Descriptions>
                <Description>
                    <Culture>String</Culture>
                    <Value>First Exemption</Value>
                </Description>
            </Descriptions>
            <ExemptionConditions>
                <ExemptByTender>
                    <string>null</string>
                </ExemptByTender>
                <ExemptByDiscountAuthority>false</ExemptByDiscountAuthority>
                <ExemptByAuthority>true</ExemptByAuthority>
                <ExemptByTaxRate>
                    <string>null</string>
                </ExemptByTaxRate>
            </ExemptionConditions>
            <ExemptionMethod>
                <ExemptionMethodType>Discount</ExemptionMethodType>
                <Imposition>null</Imposition>
                <Percentage>21.15</Percentage>
            </ExemptionMethod>
            <ExemptionId>{exemptionId}</ExemptionId>
        </TaxExemptionData>
        <TaxExemptionData>
            <TaxAuthority>USA</TaxAuthority>
            <Descriptions>
                <Description>
                    <Culture>en-US</Culture>
                    <Value>First Exemption</Value>
                </Description>
            </Descriptions>
            <ExemptionConditions>
                <ExemptByTender>
                    <string>null</string>
                </ExemptByTender>
                <ExemptByDiscountAuthority>false</ExemptByDiscountAuthority>
                <ExemptByAuthority>true</ExemptByAuthority>
                <ExemptByTaxRate>
                    <string>null</string>
                </ExemptByTaxRate>
            </ExemptionConditions>
            <ExemptionMethod>
                <ExemptionMethodType>FullExemption</ExemptionMethodType>
                <Imposition>null</Imposition>
                <Percentage xsi:nil="true" />
            </ExemptionMethod>
            <ExemptionId>FullExemption</ExemptionId>
        </TaxExemptionData>
    </PageContent>
</TaxExemptionResponse>
```

## Add Tax Parameters

Used to add the Customer ID and Name of customers eligible for Tax Exemptions.

The Customer details are recorded for Tax Exemptions at both the item and transaction level.

When configured to capture on or both of the customer details, and a Tax Exemption is added without customer details, an exception is thrown and the Tax Exemption is not added to the cart.

PUT

/emerald/selling-service/c1/selling-configuration/tax-settings/tax-parameters/{enterpriseUnit}

```json
Request
{
  "enterpriseUnit": "00000000000000000000000000035295",
  "customerExemptionIdRequired": true,
  "exemptionCustomerNameRequired": true
}
}
```

```json
Response Status OK
{
   OK
}
```

## Get All Tax Parameters

Used to retrieve all the Tax Parameter details.

GET

/emerald/selling-service/c1/selling-configuration/tax-settings/tax-parameters

```json
Response Status OK
{
    "lastPage": true,
    "pageNumber": 0,
    "totalPages": 1,
    "totalResults": 1,
    "pageContent": [
        {
            "enterpriseUnit": "{enterpriseUnit}",
            "configuration": {
                "enterpriseUnit": "00000000000000000000000000035295",
                "customerExemptionIdRequired": true,
                "exemptionCustomerNameRequired": true
            }
        }
    ]
}
```
