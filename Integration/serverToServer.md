* [Back to contents](../Readme.md#paydo-integration-options)

# Server-To-Server integration

This type of integration allows to interact with PayDo API and control almost every step of the payment.

It is suitable for those who have enough resources for development and at the same time want to have more control over payments.


## Checkout Flow



1. [Create invoice](../Invoice/createInvoice.md)
2. Make a decision on the next step

Once an invoice has been created, you can decide on what to do next.

There are two cases possible, depending on the payment method, specified when creating an invoice:



* if **`paymentMethod.formType` is `cards`** - to create the transaction, the request requires Card Token. So the next step is - to show the card form, and prepare to send a request to [Card Token generation](../Checkout/createCardToken.md)
* if **`paymentMethod.formType` is not `cards`** - you can make a request to [create the transaction](../Checkout/createCheckoutTransaction.md).
3. [Check transaction status](../Checkout/checkTransactionStatus.md) and decide what to do next.
4. [Receive IPN](../Checkout/ipn.md)
