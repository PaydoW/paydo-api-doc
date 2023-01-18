* [Back to contents](../Readme.md#contents)

# Get refund details



* [Endpoint description](#endpoint-description)
* [Request example](#request-example)
* [Successful response example](#successful-response-example)
* [Error response examples](#error-response-examples)
* [Refund statuses](#refund-statuses)


## Endpoint description

**Important!** This endpoint requires authentication.

![Endpoint](https://img.shields.io/badge/-Endpoint-darkblue?style=for-the-badge)

```
GET https://paydo.com/v1/refunds/user-refunds?query[identifier]={paydoRefundId}
```

![HEADERS](https://img.shields.io/badge/-Headers-darkviolet?style=for-the-badge)


```
Content-Type: application/json
Authorization: Bearer YOUR_JWT_TOKEN
```


![Parameters](https://img.shields.io/badge/-Parameters-gray?style=for-the-badge)


```
paydoRefundId - identifier of refund.
```



## Request example:


```php
curl -X GET \
  https://paydo.com/v1/refunds/user-refunds?query[identifier]={paydoRefundId} \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer eyJ0eXAiOiJKV……...
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
  "data": [
    {
      "identifier": "8888888-1111-2222-0000-1d54382d1e46",
      "status": 2,
      "type": 2,
      "userIdentifier": 46288,
      "amount": 10,
      "currency": "USD",
      "createdAt": 1644402901,
      "updatedAt": 1644402905,
      "sourceTransaction": {
        "identifier": "999999-1111-5fcc-aa56-35cc093e434e",
        "walletIdentifier": "11111",
        "type": 7,
        "amount": 440.65,
        "currency": "USD",
        "state": 2,
        "commission": [],
        "exchange": [],
        "createdAt": 1644334067,
        "updatedAt": 1644334070,
        "orderId": "59",
        "description": "",
        "productAmount": 455,
        "productCurrency": "USD",
        "pageDetails": [],
        "language": "en",
        "paymentMethodIdentifier": "payment_method_id",
        "payerInformation": [
          {
            "type": 3,
            "value": "test"
          },
          {
            "type": 1,
            "value": "test@address.com"
          },
          {
            "type": 8,
            "value": "183.106.148.26"
          },
          {
            "type": 9,
            "value": "FR"
          }
        ],
        "geoInformation": {
          "ip": "183.106.148.26",
          "city": {
            "name": "Paris"
          },
          "region": {
            "iso": "UA-30",
            "name": "Paris City"
          },
          "country": {
            "iso": "FR",
            "name": "France"
          },
          "continent": {
            "code": "EU"
          }
        },
        "resultUrl": "https://example.com/",
        "failUrl": "https://example.com/",
        "pid": "1apAa333WAS",
        "error": "",
        "errorCode": "",
        "cardMetadata": {
          "bin": "4444444444444444",
          "lastDigits": "4444",
          "paymentSystem": "visa",
          "country": "US",
          "holderName": "HOLDER NAME"
        },
        "strategy": 11,
        "chosenAmount": 483.46,
        "chosenCurrency": "USD",
        "application": {
          "identifier": "9999999-1111-4c4c-9b96-27bc463f3e69",
          "name": "TEST",
          "info": "TEST"
        }
      },
      "error": null,
      "metadata": {
        "internal merchant id": "example",
        "isAutoRefund": true
      }
    }
  ],
  "status": 1
}
```


---
## Error response examples

![422](https://img.shields.io/badge/422-Unprocessable%20Entity-red?style=for-the-badge)
```
HTTP/1.1 422 Unprocessable Entity
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

#
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

#
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
  "message": "Authorization token invalid"
}
```


Please check the following article regarding [authentication](../Authentication/authentication.md).


## Refund statuses


|Status|Type|Description|
|--- |--- |--- |
|1|new|New refund|
|2|accepted|Accepted refund|
|3, 4|rejected|Rejected refund|



## [→ Get merchant's refunds](../Refund/getRefundList.md)
