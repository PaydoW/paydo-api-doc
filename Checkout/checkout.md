1. [Checkout](#checkout)
   * [Integration types](#integration-types)
      * [Hosted page](../Integration/hostedPage.md)
      * [Server-To-Server](../Integration/serverToServer.md)
   * [IPN (instant payment notification)](#ipn)
      * [IPN Request example](#ipn-request-example)
1. [Card tokenization](createCardToken.md)
1. [Check payment status](checkTransactionStatus.md)
1. [Merchant payment methods](getAvailablePaymentMethods.md)

# Checkout

All projects created after the transition to the new system work according to the new documentation.

You can distinguish an old project from a new one by public key.

In the old project, the public key has a similar form:

**application-777**

For a new project, the public key looks like this:

**application-7cccbe4b-e448-45d3-93d0-35f1a65df87e**

## Integration types

There are currently 2 options for using the API.

* [Hosted page](../Integration/hostedPage.md) - very simple integration with showing PayDo pages
* [Server-To-Server](../Integration/serverToServer.md) - complex integration using PayDo API for users having a PCI DSS certificate


## IPN

After finish the payment and assigning a transaction
to one of the [final statuses](../Transaction/getTransaction.md#transaction-statuses),
the payment gateway sends to the Merchant's server a Instant Payment Notification (IPN).

IPN will be send only in case of successfully created transaction.
Internal Paydo transaction created only after successful request to Acquirer.
IPN request will be send to ipn url which you setup for selected project.

----
**Note:** Please note! A notification is sent to the merchant's server within 24 hours
and until the Paydo server, upon this request, receives the HTTP status code "200 OK".

----
For greater security, we highly recommend that you accept IPN only from our IP addresses:

    52.49.204.201
    54.229.170.212
----

### IPN Request example

`Content-Type: application/json`

`POST https://url from your project`

```json
{
    "invoice": {
        "id": "d024f697-ba2d-456f-910e-4d7fdfd338dd",
        "txid": "dca59ca5-be19-470d-9494-9b76944e0241"
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

**Parameters**

Parameter                       |  Type   |                 Description     |
--------------------------------|---------|---------------------------------| 
invoice.id                      | string  | Invoice identifier              |
invoice.id                      | string  | Transaction identifier          |
transaction.id                  | string  | Transaction identifier          |
transaction.state               | number  | Transaction state               |
transaction.error.message       | string  | Transaction error message       |
transaction.error.code          | string  | Always empty string             |

Using transaction id (txid) you [can get transaction](../Transaction/getTransaction.md)
find there your order id and process this order in your system.



