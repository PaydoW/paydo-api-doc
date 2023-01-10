* [Create transaction](#create-transaction)
    * [URL for requests](#url-for-requests)
    * [Request example](#request-example)
    * [Successful response example](#successful-response-example)
    * [Errors and failed responses](#errors-and-failed-responses)
    * [Code info](#code-info)

# Intro

**Transaction** - An entity that reflects the money transferring.

----
**Note:** Checkout transaction can be created only in case of successful request to acquirer. 
This mean that tries to pay invoice is not limited, if invoice doesn't have transaction and invoice is not overdue.

----

## Create transaction

### URL for requests

`Content-Type: application/json`

`POST https://paydo.com/v1/checkout/create`

**Parameters**

Parameter             |        Type      |                 Description                                                                             |  Required |
----------------------|------------------|---------------------------------------------------------------------------------------------------------|-----------| 
invoiceIdentifier     | string           | Invoice identifier                                                                                      |     *     |
**customer**          | **JSON object**  | Payer/Customer info                                                                                     |     *     |
&emsp;customer.email  | string           | Email                                                                                                   |     *     |
&emsp; ...            | string           | Any data related to the payer/customer                                                                  |           |
checkStatusUrl        | string           | [URL to check payment status][status]                                                                   |     *     |
payCurrency           | string           | Currency code. Should be passed in case of the payment currency is different from the order currency    |           |
paymentMethod         | string           | Payment method id. Required if invoice doesn't have payment method                                      |           |
cardToken             | string           | [Bank card token][token]. Required if paymentMethod.formType equal "cards" (bank card payment method)   |           |

[token]: ../Checkout/createCardToken.md
[status]: ../Checkout/checkTransactionStatus.md


### Request example

```shell script
curl -X POST \
  https://paydo.com/v1/checkout/create \
  -H 'Content-Type: application/json' \
  -d '{
	"invoiceIdentifier": "e61dfa44-4987-400a-b58e-cd550aae9613",
	"customer": {"email": "test@email.com", "ip": "127.0.0.1"},
	"checkStatusUrl": "https://your.site/check-status/{{txid}}",
	"payCurrency": "EUR",
	"paymentMethod": 381,
	"cardToken": "sdffsdfsdf"
}'
```


### Successful response example
Headers
```
HTTP/1.1 200 OK
Content-Type: application/json
identifier: 81962ed0-a65c-4d1a-851b-b3dbf9750399
```

Body
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

### Errors and failed responses

**415 Unsupported Media Type**
```json
{
  "message": "Unsupported media type. Only json allowed"
}
```

**404 Not Found**
```json
{
    "message": "Invoice not found"
}
```

**422 Unprocessable Entity**

Error from acquirer
```json
{
    "message": {
        "isSuccess": false,
        "message": "Invalid amount, less than allowed minumum"
    }
}
```

Validation error
```json
{
    "message": {
        "checkStatusUrl": [
            "This value should not be blank."
        ]
    }
}
```

## Code info
**What do the codes in the answer mean:**

Code    | Description
--------|---------------------------------
1000    | Transaction was created successfully.
1001    | The transaction was not created.
1002    | Authentication required. If you receive this error, then you cannot create a transaction instead of a user. In order for the payment to be successful, you need to redirect the user to the page: https://paydo.com/payment/{InvoiceId}. You can see how to create an invoice in "[How create invoice](../Invoice/createInvoice.md)".
100001  | Authentication and verification required. If you receive this error, then you cannot create a transaction instead of a user. In order for the payment to be successful, you need to redirect the user to the page: https://paydo.com/payment/{InvoiceId}. You can see how to create an invoice in "[How create invoice](../Invoice/createInvoice.md)".
100002  | User registered. Required verification. If you receive this error, then you cannot create a transaction instead of a user. In order for the payment to be successful, you need to redirect the user to the page: https://paydo.com/payment/{InvoiceId}. You can see how to create an invoice in "[How create invoice](../Invoice/createInvoice.md)".
100003  | Required authentication. If you receive this error, then you cannot create a transaction instead of a user. In order for the payment to be successful, you need to redirect the user to the page: https://paydo.com/payment/{InvoiceId}. You can see how to create an invoice in "[How create invoice](../Invoice/createInvoice.md)".
