* [Back to contents](../Readme.md#contents)

# IPN - Checkout

After finishing the payment and assigning a transaction to one of the [final statuses](../Checkout/getTransaction.md#transaction-statuses), the payment gateway sends to the Merchant's server an Instant Payment Notification (IPN).

IPN will be sent only in case of a successfully created transaction. Internal PayDo transactions are created only after successful request to the Acquirer. IPN request will be sent to the IPN URL set up for the selected project.



---
**Note:** Sometimes IPNs related to a particular order may be sent multiple times. If you are receiving multiple IPNs with the same status and data (order ID, transaction ID, etc.) that refer to the order, please make sure the payment has been credited only once. Otherwise, just accept the first notification only and ignore all others.

Still, several IPN notifications should be accepted for a particular transaction if they carry different statuses. In this case, proceed with updating the current transaction state.

## For instance:

 **CASE 1.** You received several IPNs with the same data and the `success` state for the order ID 1111;

 **CASE 2.** You received an IPN for the order ID 1111 with the `failed` status; later on, you received another IPN notification with the same transaction data for the order ID 1111 but with the `success` state.

## Solution:

 **CASE 1.** You only need to accept the first notification and ignore the others;

 **CASE 2.** You shouldn't ignore notifications with a different state to let the transaction status become updated.


---

**Note:** A notification is sent to the merchant's server within 24 hours and until the PayDo server, upon this request, receives the HTTP status code "200 OK".

---

**For greater security, we highly recommend that you accept IPN only from our IP addresses:**

```
52.49.204.201
54.229.170.212
```



## IPN Request example

![Endpoint](https://img.shields.io/badge/-Endpoint-darkblue?style=for-the-badge)
```
POST https://url from your project
```

![HEADERS](https://img.shields.io/badge/-Headers-darkviolet?style=for-the-badge)
```
Content-Type: application/json
```
![BODY](https://img.shields.io/badge/-Body-darkblue?style=for-the-badge)
```json
{
  "invoice": {
    "id": "d024f697-ba2d-456f-910e-4d7fdfd338dd",
    "txid": "dca59ca5-be19-470d-9494-9b76944e0241",
    "metadata": {
      "internal merchant id": "example",
      "any other merchant data which were passed to invoice on create it": {
        "orderId": "test",
        "amount": 3,
        "customerId": 15487
      }
    }
  },
  "transaction": {
    "id": "dca59ca5-be19-470d-9494-9b76944e0241",
    "state": 2,
    "order": {
      "id": "ANY_ORDER_ID"
    },
    "error": {
      "message": "3DS authorization error or 3DS canceled by payer",
      "code": ""
    }
  }
}
```
---
**Note:** You can pass the data you want in the "metadata" parameter when [requesting to create an invoice](https://github.com/PaydoW/paydo-api-doc/blob/main/Invoice/createInvoice.md#endpoint-description) and the data will come to you in the Instant Payment Notification (IPN)

---
![Parameters](https://img.shields.io/badge/-Parameters-gray?style=for-the-badge)


|Parameter|Type|Description|
|--- |--- |--- |
|invoice.id|string|Invoice identifier|
|invoice.txid|string|Transaction identifier|
|transaction.id|string|Transaction identifier|
|transaction.state|number|Transaction state|
|transaction.error.message|string|Transaction error message|
|transaction.error.code|string|Always empty string|



Using transaction id (txid) you [can get the transaction](../Checkout/getTransaction.md) to find there your order id and process this order in your system.


## [→ Refund - Create refund](../Refund/createRefund.md)
