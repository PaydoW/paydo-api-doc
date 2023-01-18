* [Back to contents](../Readme.md#contents)

# Card tokenization

* [Endpoint description](#endpoint-description)
* [Request example](#request-example)
* [Successful response example](#successful-response-example)
* [Error response examples](#error-response-examples)

## Intro


PayDo provides you with the opportunity to independently initiate a money debit from payers’ payment cards and takes care of certification and compliance with the  PCI-DSS standards. The standard declares a ban on the processing and storage of cardholder data (DDC) on the merchant's side.


---

**Note:** Access to card token generation is available only upon request. Please contact [PayDo support](https://paydo.com/en/contact-us/) if want to use card tokenization.


---


## Endpoint description

![Endpoint](https://img.shields.io/badge/-Endpoint-darkblue?style=for-the-badge)


```
POST https://paydo.com/v1/payment-tools/card-token/create
```


![HEADERS](https://img.shields.io/badge/-Headers-darkviolet?style=for-the-badge)


```
Content-Type: application/json
```

![Parameters](https://img.shields.io/badge/-Parameters-gray?style=for-the-badge)


|Parameter|Type|Description|Required|
|--- |--- |--- |--- |
|invoiceIdentifier|string|Invoice identifier|*|
|pan|string|Bank card number|*|
|expirationDate|string|Expiration date. Format mm/yy (12/20)|*|
|cvv|string|CVV|*|
|holderName|string|Cardholder name|*|




## Request example


```php
curl -X POST \
  https://paydo.com/v1/payment-tools/card-token/create \
  -H 'Content-Type: application/json' \
  -d '{
	"invoiceIdentifier": "e61dfa44-4987-400a-b58e-cd550aae9613",
    "pan":"5555555555554444",
    "expirationDate":"12/20",
    "cvv":"123",
    "holderName":"HOLDER_NAME"
}'
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
```


![Body](https://img.shields.io/badge/-Body-darkblue?style=for-the-badge)



```json
{
    "data":{
        "token":"1ay4YEZXF75BTraFw\/sPJ9iMJVOr\/bR\/UeEPp",
        "expired_at":1567765561
    },
    "status":1
}
```

---

## Error response examples

![415](https://img.shields.io/badge/415-Unsupported%20Media%20Type-red?style=for-the-badge)

```
HTTP/1.1 415 Unsupported media type.
```

![HEADERS](https://img.shields.io/badge/-Headers-darkviolet?style=for-the-badge)

```
Content-Type: application/json
```

![BODY](https://img.shields.io/badge/-Body-darkblue?style=for-the-badge)


```
{
  "message": "Unsupported media type. Only json allowed"
}
```
#
![503](https://img.shields.io/badge/503-Service%20Unavailable-red?style=for-the-badge)

```
HTTP/1.1 503 Service Unavailable
```
![HEADERS](https://img.shields.io/badge/-Headers-darkviolet?style=for-the-badge)

```
Content-Type: application/json
```


![BODY](https://img.shields.io/badge/-Body-darkblue?style=for-the-badge)


```
{
    "message": "Card tokenization is temporarily unavailable. Please contact support"
}
```
#

![403](https://img.shields.io/badge/403-Forbidden-red?style=for-the-badge)
```
HTTP/1.1 403 HTTP Forbidden
```
![HEADERS](https://img.shields.io/badge/-Headers-darkviolet?style=for-the-badge)
```
Content-Type: application/json
```


![BODY](https://img.shields.io/badge/-Body-darkblue?style=for-the-badge)


```
{
    "message": "Card tokenization is not available for your application. Please contact support"
}
```


In case you get this error, you should contact [PayDo support](https://paydo.com/en/contact-us/).
#
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
    "message": "Invoice not found"
}
```

#
![422](https://img.shields.io/badge/422-Payment%20method%20is%20not%20enabled-red?style=for-the-badge)
```
HTTP/1.1 422 Unprocessable Entity
```
![HEADERS](https://img.shields.io/badge/-Headers-darkviolet?style=for-the-badge)

```
Content-Type: application/json
```


![BODY](https://img.shields.io/badge/-Body-darkblue?style=for-the-badge)


```json
{
    "message": {
        "pan": [
            "Invalid card number."
        ],
        "cvv": [
            "This value is too long. It should have 4 characters or less."
        ]
    }
}
```
#


## [→ Get transaction info](../Checkout/getTransaction.md)
