* [Back to contents](../Readme.md#contents)

# Сreate checkout transaction


* [Endpoint description](#endpoint-description)
* [Request example](#request-example)
* [Successful response example](#successful-response-example)
* [Error response examples](#error-response-examples)
* [Code info](#code-info)

# Intro


**Transaction** - An entity that reflects the money transfer.


---

**Note:** Checkout transactions can be created only in case of a successful request to the acquirer. This means that trying to pay an invoice is not limited if the invoice doesn't have a transaction and the invoice is not overdue.


---

**Note:** The longest period between creating an invoice and making a checkout is 24 hours. After that, the invoice will expire.


---


## Endpoint description

![Endpoint](https://img.shields.io/badge/-Endpoint-darkblue?style=for-the-badge)


```
POST https://paydo.com/v1/checkout/create
```


![HEADERS](https://img.shields.io/badge/-Headers-darkviolet?style=for-the-badge)


```
Content-Type: application/json
```


Parameters


|Parameter|Type|Description|Required|
|--- |--- |--- |--- |
|invoiceIdentifier&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|string|Invoice identifier|*|
|**customer**|**JSONobject**|Payer/Customer info|*|
|&emsp;customer.name|string|Name|*|
|&emsp;customer.email|string|Email|*|
|&emsp;customer.ip|string|IP address. We highly recommend adding this parameter to the request for more complete identification of the customer|*|
|&emsp;...|string|Any data related to the payer/customer||
|checkStatusUrl|string|[URL to check transaction status](../Checkout/checkTransactionStatus.md)|*|
|payCurrency|string|Currency code. Should be passed in case of the payment currency is different from the order currency||
|paymentMethod|string|Payment method id. Required if the invoice doesn't have payment method||
|cardToken|string|[Bank card token.](../Checkout/createCardToken.md) Required if paymentMethod.formType equals "cards" (bank card payment method)||




## Request example

1. If `paymentMethod.form`Type is cards:


```php
curl -X POST \
  https://paydo.com/v1/checkout/create \
  -H 'Content-Type: application/json' \
  -d '{
	"invoiceIdentifier": "INVOICE_IDENTIFIER",
	"customer": {"email": "test@email.com", "name": "CUSTOMER_NAME"},
	"checkStatusUrl": "https://your.site/check-status/{{txid}}",
	"payCurrency": "EUR",
	"paymentMethod": method_ID,
	"cardToken": "CARD_TOKEN"
}'
```


2. If `paymentMethod.form`Type is not cards:


```php
curl -X POST \
  https://paydo.com/v1/checkout/create \
  -H 'Content-Type: application/json' \
  -d '{
	"invoiceIdentifier": "INVOICE_IDENTIFIER",
	"customer": {"email": "test@email.com", "name": "CUSTOMER_NAME"},
	"checkStatusUrl": "https://your.site/check-status/{{txid}}",
	"payCurrency": "EUR",
	"paymentMethod": method_ID
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
![BODY](https://img.shields.io/badge/-Body-darkblue?style=for-the-badge)
```json
{
    "data": {
        "isSuccess": true,
        "message": "",
        "txid": "e6c8ba69-b961-4e93-a083-2097f30dfbd9",
        "code": 1000
    },
    "status": 1
}
```


Add the generated transaction ID to the waiting page and redirect the user to that page. You can then use the check transaction status query to track the transaction's progress.

---

## Error response examples

![415](https://img.shields.io/badge/415-Unsupported%20Media%20Type-red?style=for-the-badge)

```
{
  "message": "Unsupported media type. Only json allowed"
}
```

![404](https://img.shields.io/badge/404-Not%20Found-red?style=for-the-badge)

```
{
    "message": "Invoice not found"
}
```


![422](https://img.shields.io/badge/422-Unprocessable%20Entity-red?style=for-the-badge)

Error from acquirer
```
{
    "message": {
        "isSuccess": false,
        "message": "Invalid amount, less than allowed minimum"
    }
}
```

![422](https://img.shields.io/badge/422-Unprocessable%20Entity-red?style=for-the-badge)

Validation error
```
{
    "message": {
        "checkStatusUrl": [
            "This value should not be blank."
        ]
    }
}
```
---


## Code info

What do the codes in the answer mean:


|Code|Description|
|--- |--- |
|1000|Transaction was created successfully.|
|1001|The transaction was not created.|
|1002|Authentication required. If you receive this error, then you cannot create a transaction instead of a user. In order for the payment to be successful, you need to redirect the user to the page: https://paydo.com/payment/{InvoiceId}. You can see how to create an invoice in "[How to create an invoice](../Invoice/createInvoice.md)".|
|100001|Authentication and verification required. If you receive this error, then you cannot create a transaction instead of a user. In order for the payment to be successful, you need to redirect the user to the page: https://paydo.com/payment/{InvoiceId}. You can see how to create an invoice in "[How to create an invoice](../Invoice/createInvoice.md)".|
|100002|User registered. Required verification. If you receive this error, then you cannot create a transaction instead of a user. In order for the payment to be successful, you need to redirect the user to the page: https://paydo.com/payment/{InvoiceId}. You can see how to create an invoice in "[How to create an invoice](../Invoice/createInvoice.md)".|
|100003|Required authentications. If you receive this error, then you cannot create a transaction instead of a user. In order for the payment to be successful, you need to redirect the user to the page: https://paydo.com/payment/{InvoiceId}. You can see how to create an invoice in "[How to create an invoice](../Invoice/createInvoice.md)".|




## [→ Check transaction status](../Checkout/checkTransactionStatus.md)
