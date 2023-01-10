* [Get transaction info](#get-transaction-info)
    * [URL for requests](#url-for-requests)
    * [Request example](#request-example)
    * [Successful response example](#successful-response-example)
    * [Errors and failed responses](#errors-and-failed-responses)
    * [Transaction statuses](#transaction-statuses)
    * [Transaction types](#transaction-types)
    * [Payer information types](#payer-information-types)

# Get transaction info

----
**Note:** This URL require [authentication](../Authentication/authentication.md).

----

### URL for requests

`Content-Type: application/json`
`Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpZCI6IjE...`

`GET https://paydo.com/v1/transactions/{id}`

**Parameters**

Parameter   |  Type  |  Required |
------------|--------|-----------| 
id          | string |     *     |

### Request example

```shell script
curl -X GET \
  https://paydo.com/v1/transactions/81962ed0-a65c-4d1a-851b-b3dbf9750399 \
    -H 'Content-Type: application/json' \
    -H 'Authorization: Bearer eyJ0eXAiOiJKV...
```

### Successful response example

Headers
```
HTTP/1.1 200 OK
Content-Type: application/json
token: eyJ0eXAiOiJKV...
```

Body
```json
{
    "data": {
        "identifier": "81962ed0-a65c-4d1a-851b-b3dbf9750399",
        "walletIdentifier": "1607",
        "type": 7,
        "amount": 100,
        "currency": "USD",
        "payAmount": 101.5,
        "payCurrency": "USD",
        "state": 5,
        "error": "3DS authorization error or 3DS canceled by payer",
        "cardMetadata": {
            "bin": "555555",
            "lastDigits": "4444",
            "paymentSystem": "mastercard",
            "country": "BR",
            "holderName": "Snatiago Delcaptcha"
        },
        "commission": [
            {
                "identifier": "20842",
                "type": 1,
                "percent": 1.5,
                "amount": 0,
                "totalValue": 0,
                "strategy": 1,
                "merchantPercent": 0,
                "payerPercent": 0,
                "merchantAmount": 0,
                "payerAmount": 0,
                "transactionIdentifier": "81962ed0-a65c-4d1a-851b-b3dbf9750399"
            }
        ],
        "exchange": [],
        "createdAt": 1567402240,
        "updatedAt": null,
        "orderId": "134666",
        "description": "",
        "productAmount": 100,
        "productCurrency": "USD",
        "pageDetails": [],
        "language": "en",
        "paymentMethodIdentifier": "381",
        "payerInformation": [
            {
                "type": 1,
                "value": "test.user@paydo.com"
            },
            {
                "type": 3,
                "value": "test.user"
            }
        ],
        "geoInformation": {
            "ip": "127.0.0.1",
            "city": {
                "name": "Baguio City"
            },
            "region": {
                "iso": "PH-15",
                "name": "Cordillera"
            },
            "country": {
                "iso": "PH",
                "name": "Philippines"
            },
            "continent": {
                "code": "AS"
            }
        },
        "resultUrl": "https://your.site/result",
        "failUrl": "https://your.site/fail",
        "pid": "23234523525",
        "strategy": 2,
        "chosenAmount": 100,
        "chosenCurrency": "USD",
        "castedAmount": "USD",
        "castedCurrency": "USD",
        "application": {
            "identifier": "3",
            "name": "Project name",
            "info": "For sales",
            "midIdentifier": "1023"
        }
    },
    "status": 1
}
```

### Errors and failed responses

**404 Not Found**
```json
{
   "message": "Transaction not found"
}
```


### Transaction statuses

Status      |  Type    |  Description                        |
------------|----------|-------------------------------------| 
1           | new      |  New transaction                    |
2           | accepted |  Transaction was paid successfully  |
4           | pending  |  Transaction pending                |
3, 5        | failed   |  Transaction failed                 |


### Transaction types

Type      |  Type    |  Description                        |
----------|----------|-------------------------------------| 
7         | checkout |  Checkout transaction               |

### Payer information types

Type      |  Description   |
----------|----------------| 
1         | Email          |
2         | Phone          |
3         | Name           |
4         | National id    |
5         | IBAN           |
6         | Address        |
7         | Zip code       |
8         | IP             |
9         | Country code   |
