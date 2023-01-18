# <a href="https://paydo.com/en/"> <img src="https://github.com/AnatoliyKulinich/paydo-api-doc/blob/master/images/logo.svg" alt="" style="margin-bottom:-5px;margin-right:5px"></a>**REST-like API Reference**

PayDo API is organized around [REST](http://en.wikipedia.org/wiki/Representational_State_Transfer) and has predictable resource-oriented URLs, accepts [JSON](http://www.json.org/) request bodies, returns JSON responses, and uses standard HTTPS response codes.

Each request to PayDo API should have a `Content-Type` HTTPS header with `application/JSON` value.


---
## **PayDo integration options :**



* [Hosted page](Integration/hostedPage.md) – a straightforward integration option using default PayDo checkout pages.
* [Direct integration](Integration/directIntegration.md) – bypassing the PayDo hosted page
* [Server-To-Server](Integration/serverToServer.md) – complex integration using PayDo API for users having a PCI DSS certificate

You can learn more about the difference between the above options here: [Difference description.](Integration/differenceDescription.md)


## Contents

### **1. Payment methods**

With the help of these requests, you can get the methods available for payments.



* [Get available payment methods](Methods/getAvailablePaymentMethods.md)


### **2. Authentication**

Authentication is required to get access to the protected API actions.



* [Bearer authentication](Authentication/authentication.md)


### **3. API Response examples**

Description of API's response format with examples.



* [Successful response examples](Response/successResponse.md)
* [Failed responses](Response/failResponse.md)


### **4. Invoice**

An invoice is a basic entity in each payment system, a scheduled payment a customer makes toward the balance of goods or services.

Checkout transactions can be created only after invoice creation.



* [Payment methods](Methods/getAvailablePaymentMethods.md)
* [Create invoice](Invoice/createInvoice.md)
* [Get invoice info](Invoice/getInvoice.md)


### **5. Checkout**

How to process payments.



* [Create checkout transaction](Checkout/createCheckoutTransaction.md)
* [Check transaction status](Checkout/checkTransactionStatus.md)
* [Card tokenization (*For Server-to-server integration only)](Checkout/createCardToken.md)
* [Get transaction info](Checkout/getTransaction.md)
* [IPN (instant payment notification)](Checkout/ipn.md)


### **6. Refund**

How to process refunds.



* [Create refund](Refund/createRefund.md)
* [Get merchant's refunds](Refund/getRefundList.md)
* [Get refund details](Refund/getRefund.md)


### **7. Wallet**

Wallet actions and payments.



* [Transfer money between wallets](Wallet/moveMoneyBetweenWalletsWithdrawal.md)
