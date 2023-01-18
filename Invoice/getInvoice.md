* [Back to contents](../Readme.md#contents)

# Get invoice info


* [Endpoint description](#endpoint-description)
* [Request example](#request-example)
* [Successful response example](#successful-response-example)
* [Error response examples](#error-response-examples)
* [Invoice statuses](#invoice-statuses)

## Endpoint description


![Endpoint](https://img.shields.io/badge/-Endpoint-darkblue?style=for-the-badge)


```
GET https://paydo.com/v1/invoices/{{invoiceId}}
```


![HEADERS](https://img.shields.io/badge/-Headers-darkviolet?style=for-the-badge)


```
Content-Type: application/json
```


Parameters


|Parameter|Type|Required|
|--- |--- |--- |
|invoiceId|string|*|




## Request example


```
curl -X GET \
    https://paydo.com/v1/invoices/81972ed0-a85c-4d1a-851b-b3dbf0750399 \
    -H 'Content-Type: application/json'
```



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
    "data": {
        "identifier": "81972ed0-a85c-4d1a-851b-b3dbf0750399",
        "status": 0,
        "type": 1,
        "applicationIdentifier": "3b60feb1-eeb8-4215-a494-2382427ffe88",
        "amount": 3,
        "currency": "EUR",
        "orderIdentifier": "test",
        "items": [
            {
                "id": "487",
                "name": "Item 1",
                "price": "0.8999999999999999"
            },
            {
                "id": "358",
                "name": "Item 2",
                "price": "2.0999999999999996"
            }
        ],
        "description": "",
        "resultUrl": "https://your.site/result",
        "failUrl": "https://your.site/fail",
        "productUrl": null,
        "language": "en",
        "payer": {
            "email": "test.user@paydo.com",
            "name": "",
            "phone": "",
            "address": "", 
            "companyName": "", 
            "site": "",
            "extraFields": []
        },
        "paymentMethod": {
            "identifier": 204,
            "fields": [
                {
                    "name": "email",
                    "type": "email",
                    "required": true
                },
                {
                    "name": "phone",
                    "type": "string",
                    "title": "PayDo e-wallet",
                    "regexp": "\\+\\d{1,15}",
                    "required": true
                }
            ],
            "formType": "standard"
        },
        "isSeen": true,
        "customization": [],
        "createdAt": 1567754398,
        "updatedAt": null,
        "transactionIdentifier": "3333feb1-eeb8-4215-a494-238242788888",
        "isTopUp": false
        "isOverdue": false
    },
    "status": 1
}
```



## Error response examples

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
   "message": "Invoice not found"
}
```



## Invoice statuses


|Status|Type|Description|
|--- |--- |--- |
|0|new|Invoice can be paid|
|1|paid|Invoice already paid|




## [→ Checkout - Create checkout transaction](../Checkout/createCheckoutTransaction.md)
