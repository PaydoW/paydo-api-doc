# Paydo REST-like API Reference

The Paydo API is organized around [REST](http://en.wikipedia.org/wiki/Representational_State_Transfer).

Paydo API has predictable resource-oriented URLs, accepts [JSON](http://www.json.org/) request bodies,
 returns [JSON](http://www.json.org/) responses, and uses standard HTTP response codes.

Each request to Paydo API should have **Content-Type HTTP header** with `application/json` value.

## Contents

1. [API Response examples](Response)
    * [Successful response](Response/successResponse.md)
    * [Failed responses](Response/failResponse.md)
2. [Authentication](Authentication/authentication.md)
3. [Examples](Examples)
    * [ApiCertificates](Examples/apiCertificates)
4. [Checkout](Checkout/checkout.md)
    * [Integration types](Checkout/checkout.md#integration-types)
        * [Hosted page](Integration/hostedPage.md)
        * [Server-To-Server](Integration/serverToServer.md)
    * [IPN (instant payment notification)](Checkout/checkout.md#ipn)
        * [IPN Request example](Checkout/checkout.md#ipn-request-example)
    * [Card tokenization](Checkout/createCardToken.md)
    * [Check payment status](Checkout/checkTransactionStatus.md)
    * [Merchant payment methods](Checkout/getAvailablePaymentMethods.md)
5. [Invoice](Invoice/getInvoice.md)
    * [Create invoice](Invoice/createInvoice.md)
    * [Get invoice](Invoice/getInvoice.md)
6. [Transaction](Transaction/getTransaction.md)
    * [Create checkout transaction](Transaction/createCheckoutTransaction.md)
    * [Get transaction](Transaction/getTransaction.md)
7. [Refund](Refund/getRefundList.md)
    * [Create Refund](Refund/createRefund.md)
    * [Get concrete refund details](Refund/getRefund.md)
    * [Get merchant's refunds](Refund/getRefundList.md)
8. [Wallet](Wallet)
    * [Transfer money between wallets](Wallet/moveMoneyBetweenWalletsWithdrawal.md) 
