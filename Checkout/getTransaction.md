* [Back to contents](../Readme.md#contents)

# Get transaction info



* [Endpoint description ](#endpoint-description)
* [Request example](#request-example)
* [Successful response example](#successful-response-example)
* [Error response examples](#error-response-examples)
* [Transaction states](#transaction-statuses)
* [Transaction types](#transaction-types)
* [Payer information types](#payer-information-types)

---


**Note:** This URL require [authentication](https://github.com/PaydoW/paydo-api-doc/blob/master/Authentication/authentication.md).


---


## Endpoint description

![Endpoint](https://img.shields.io/badge/-Endpoint-darkblue?style=for-the-badge)


```
GET https://paydo.com/v1/transactions/{id}
```


![HEADERS](https://img.shields.io/badge/-Headers-darkviolet?style=for-the-badge)

```
Content-Type: application/json
Authorization: Bearer YOUR_JWT_TOKEN
```


![Parameters](https://img.shields.io/badge/-Parameters-gray?style=for-the-badge)


|Parameter|Type|Required|
|--- |--- |--- |
|id|string|*|




## Request example


```php
curl -X GET \
  https://paydo.com/v1/transactions/{txid} \
    -H 'Content-Type: application/json' \
    -H 'Authorization: Bearer YOUR_JWT_TOKEN
```


---
## Successful response example

![200](https://img.shields.io/badge/200-OK-green?style=for-the-badge)

```
HTTP/1.1 200 OK
```
![HEADERS](https://img.shields.io/badge/-Headers-darkviolet?style=for-the-badge)
```
Content-Type: application/json
Authorization: Bearer YOUR_JWT_TOKEN
```
![BODY](https://img.shields.io/badge/-Body-darkblue?style=for-the-badge)


```json
{
    "data": {
        "identifier": "TRANSACTION_IDENTIFIER",
        "walletIdentifier": "WALLET_IDENTIFIER",
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
            "holderName": "John Doe"
        },
        "commission": [],
        "exchange": [],
        "createdAt": 1567402240,
        "updatedAt": null,
        "orderId": "134666",
        "description": "",
        "productAmount": 100,
        "productCurrency": "USD",
        "pageDetails": [],
        "language": "en",
        "paymentMethodIdentifier": "204",
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
        }
     }
   }
```


---
## Error response examples

![401](https://img.shields.io/badge/401-Unauthorized-red?style=for-the-badge)
```
HTTP/1.1 401 Unauthorized
```
![HEADERS](https://img.shields.io/badge/-Headers-darkviolet?style=for-the-badge)

```
Content-Type: application/json
```
![BODY](https://img.shields.io/badge/-Body-darkblue?style=for-the-badge)


```
{
  "message": "Full authentication is required to access this resource."
}
```



![404](https://img.shields.io/badge/404-Not%20Found-red?style=for-the-badge)
```
HTTP/1.1 404 Not Found
```
![HEADERS](https://img.shields.io/badge/-Headers-darkviolet?style=for-the-badge)

```
Content-Type: application/json
```


![BODY](https://img.shields.io/badge/-Body-darkblue?style=for-the-badge)


```
{
   "message": "Transaction not found"
}
```

---

## Transaction statuses


|Status|Type|Description|
|--- |--- |--- |
|1|new|New transaction|
|2|accepted|Transaction was paid successfully|
|4|pending|Transaction pending|
|3, 5|failed|Transaction failed|




## Transaction types


|Type|Type|Description|
|--- |--- |--- |
|7|checkout|Checkout transaction|



## Payer information types


|Type|Description|
|--- |--- |
|1|Email|
|2|Phone|
|3|Name|
|4|National id|
|5|IBAN|
|6|Address|
|7|Zip code|
|8|IP|
|9|Country code|



## [→ IPN - Checkout](../Checkout/ipn.md)
