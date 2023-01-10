* [Back to contents](../Readme.md#contents)

# Refund

### Merchants refund transactions

**Endpoint:**

`GET https://paydo.com/v1/refunds/user-refunds`

**Headers:**
 
    Content-Type: application/json
    Authorization: Bearer eyJ0eXAiO...

**Request example:**

```shell script
curl -X GET \
  https://paydo.com/v1/refunds/user-refunds \
    -H 'Content-Type: application/json' \
    -H 'Authorization: Bearer eyJ0eXAiOiJKV...
```

**Successful response example:**

```json
{
    "data": [
        {
            "identifier": "38c92c25-33fd-4979-ac50-f73d7dbbf660",
            "status": 1,
            "type": 2,
            "userIdentifier": 10043,
            "amount": 10,
            "currency": "USD",
            "createdAt": 1568105638,
            "updatedAt": null,
            "sourceTransaction": {
                "identifier": "c23b442d-dd2c-5663-b423-6402cf4a8c09",
                "walletIdentifier": "1806",
                "type": 7,
                "amount": 90.26,
                "currency": "USD",
                "payAmount": 72.04,
                "payCurrency": "GBP",
                "state": 2,
                "commission": [
                  {
                    "identifier": "65693",
                    "type": 1,
                    "percent": 6,
                    "amount": 0.2414774,
                    "totalValue": 6.24,
                    "strategy": 1,
                    "merchantPercent": 100,
                    "payerPercent": 0,
                    "merchantAmount": 6.24,
                    "payerAmount": 0,
                    "transactionIdentifier": "c23b442d-dd2c-5663-b423-6402cf4a8c09",
                    "currency": "USD"
                  },
                  {
                    "identifier": "65694",
                    "type": 4,
                    "percent": 3.5,
                    "amount": 0,
                    "totalValue": 3.5,
                    "strategy": 1,
                    "merchantPercent": 100,
                    "payerPercent": 0,
                    "merchantAmount": 3.5,
                    "payerAmount": 0,
                    "transactionIdentifier": "c23b442d-dd2c-5663-b423-6402cf4a8c09",
                    "currency": "USD"
                  },
                  {
                    "identifier": "65695",
                    "type": 5,
                    "percent": 6,
                    "amount": 0.2414774,
                    "totalValue": 0,
                    "strategy": 1,
                    "merchantPercent": 0,
                    "payerPercent": 0,
                    "merchantAmount": 0,
                    "payerAmount": 0,
                    "transactionIdentifier": "c23b442d-dd2c-5663-b423-6402cf4a8c09",
                    "currency": "USD"
                  },
                  {
                    "identifier": "65696",
                    "type": 3,
                    "percent": 3.5,
                    "amount": 0,
                    "totalValue": 0,
                    "strategy": 1,
                    "merchantPercent": 0,
                    "payerPercent": 0,
                    "merchantAmount": 0,
                    "payerAmount": 0,
                    "transactionIdentifier": "c23b442d-dd2c-5663-b423-6402cf4a8c09",
                    "currency": "GBP"
                  }
                ],
                "exchange": [
                  {
                    "amountFrom": 100,
                    "currencyFrom": "US Dollar",
                    "amountTo": 72.04,
                    "currencyTo": "Pound Sterling",
                    "rate": 0.72044500447036,
                    "transactionIdentifier": "c23b442d-dd2c-5663-b423-6402cf4a8c09",
                    "commissionIdentifier": "65696",
                    "accountFrom": "0",
                    "accountTo": "0"
                  }
                ],
                "createdAt": 1619616025,
                "updatedAt": 1619616027,
                "orderId": "5645643653463",
                "description": "",
                "productAmount": 100,
                "productCurrency": "USD",
                "pageDetails": [],
                "language": "en",
                "paymentMethodIdentifier": "300",
                "payerInformation": [
                  {
                    "type": 8,
                    "value": "46.229.58.90"
                  },
                  {
                    "type": 9,
                    "value": "UA"
                  }
                ],
                "geoInformation": {
                  "ip": "46.229.58.90",
                  "city": {
                    "name": "Kyiv"
                  },
                  "region": {
                    "iso": "UA-30",
                    "name": "Kyiv"
                  },
                  "country": {
                    "iso": "UA",
                    "name": "Ukraine"
                  },
                  "continent": {
                    "code": "EU"
                  }
                },
                "resultUrl": "https://successurl.om/",
                "failUrl": "https://failurl.com",
                "pid": "9cd4439e-fefc-4b83-a330-1a56dfeaad79",
                "error": "",
                "cardMetadata": {
                  "bin": "411111",
                  "lastDigits": "1111",
                  "paymentSystem": "visa",
                  "country": "US",
                  "holderName": "name"
                },
                "strategy": 11,
                "chosenAmount": 100,
                "chosenCurrency": "USD",
                "castedAmount": 65.03,
                "castedCurrency": "GBP",
                "application": {
                  "identifier": "12faa1dc-37cb-4889-9e0e-2f24eeecdcd0",
                  "name": "MyNewProject 7_32_22",
                  "info": "non-specialized wholesale trade",
                  "midIdentifier": 9
                }
          },
          "error": null,
          "metadata": []
        }
    ],
    "status": 1
} 
```

You can see the description of statuses and types at the page [Get transaction](../Transaction/getTransaction.md)
