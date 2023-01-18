* [Back to contents](../Readme.md#paydo-integration-options)

# Hosted page

This is a quite simple type of integration.

It is suitable for those who do not have enough resources for development and at the same time the control over almost the entire process will be on the side of PayDo.


## Minimal Checkout Flow



1. [Create Invoice](../Invoice/createInvoice.md)
2. **Redirect the user to the invoice preprocessing page**

After getting the invoice ID you should first redirect the payer to the invoice preprocessing page. This page has built-in functionality to make decisions about the next processes.

Invoice preprocessing page URL: [https://checkout.paydo.com/{{locale}}/payment/invoice-preprocessing/{{invoiceId}}](https://checkout.paydo.com//%7B%7Blocale%7D%7D/payment/invoice-preprocessing/%7B%7BinvoiceId%7D%7D)


## Parameters


|Parameter|Type|Description|
|--- |--- |--- |
|{{locale}}|string|Invoice language|
|{{invoiceId}}|string|Invoice identifier|



If all the required fields are completed, an attempt will be made to pay by the payment method specified when creating the account.

If you missed any of the required fields specified in the properties of the payment method or did not specify a payment method, then you will be redirected to the checkout form.

Also, if you need to enter a card number or fill out a 3DS form to confirm card payment, you will be redirected to the appropriate forms.

In case of successful payment, you will be redirected to the URL specified in resultUrl when creating the invoice. In case of error or inability to make a payment you will be redirected to the failPath accordingly.



3. [Receive IPN (instant payment notification)](../Checkout/ipn.md) - in case of the transaction was successful.