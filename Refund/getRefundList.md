* [Back to contents](../Readme.md#contents)

# Get merchant's refunds


## Endpoint description:

![Endpoint](https://img.shields.io/badge/-Endpoint-darkblue?style=for-the-badge)


```
GET https://paydo.com/v1/refunds/user-refunds
```


![HEADERS](https://img.shields.io/badge/-Headers-darkviolet?style=for-the-badge)


```
Content-Type: application/json
Authorization: Bearer YOUR_JWT_TOKEN
```


Request example:


```php
curl -X GET \
  https://paydo.com/v1/refunds/user-refunds \
    -H 'Content-Type: application/json' \
    -H 'Authorization: Bearer YOUR_JWT_TOKEN
```



## Successful response example:


```json
{
    "data": [
        {
            "identifier": "38c92c25-5555-4444-aaaa-f73d7dbbf660",
            "status": 1,
            "type": 2,
            "userIdentifier": 10043,
            "amount": 10,
            "currency": "USD",
            "createdAt": 1568105638,
            "updatedAt": null,
            "sourceTransaction": {
                "identifier": "c23b442d-dddd-2222-1111-6402cf4a8c09",
                "walletIdentifier": "1806",
                "type": 7,
                "amount": 90.26,
                "currency": "USD",
                "payAmount": 72.04,
                "payCurrency": "GBP",
                "state": 2,
                "commission": [
                  {
                    "identifier": "36363",
                    "type": 1,
                    "percent": 6,
                    "amount": 0.2414774,
                    "totalValue": 6.24,
                    "strategy": 1,
                    "merchantPercent": 100,
                    "payerPercent": 0,
                    "merchantAmount": 6.24,
                    "payerAmount": 0,
                    "transactionIdentifier": "c23b442d-dd2c-2222-1111-6402cf4a8c09",
                    "currency": "USD"
                  },
                  {
                    "identifier": "36363",
                    "type": 4,
                    "percent": 3.5,
                    "amount": 0,
                    "totalValue": 3.5,
                    "strategy": 1,
                    "merchantPercent": 100,
                    "payerPercent": 0,
                    "merchantAmount": 3.5,
                    "payerAmount": 0,
                    "transactionIdentifier":"c23b442d-1111-1111-b423-6402cf4a8c09",
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
                    "transactionIdentifier":"c23b442d-dddd-5555-4444-6402cf4a8c09",
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
                    "transactionIdentifier": "9999999-dd2c-5663-b423-6402cf4a8c09",
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
                    "transactionIdentifier": "c23b442d-1111-1111-1111-6402cf4a8c09",
                    "commissionIdentifier": "36363",
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
                    "value": "UK"
                  }
                ],
                "geoInformation": {
                  "ip": "46.219.58.90",
                  "city": {
                    "name": "city"
                  },
                  "region": {
                    "iso": "",
                    "name": "region"
                  },
                  "country": {
                    "iso": "",
                    "name": "country"
                  },
                  "continent": {
                    "code": "EU"
                  }
                },
                "resultUrl": "https://successurl.om/",
                "failUrl": "https://failurl.com",
                "pid": "9cd4439e-1111-1111-1111-1a56dfeaad79",
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
                  "identifier": "12faa1dc-1111-1111-1111-2f24eeecdcd0",
                  "name": "MyNewProject",
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


You can see the description of statuses and types by using the method from the following page [Get transaction](../Checkout/getTransaction.md)


## [→ Wallet - Transfer Between Wallets](../Wallet/moveMoneyBetweenWalletsWithdrawal.md)
