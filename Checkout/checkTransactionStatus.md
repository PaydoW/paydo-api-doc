* [Back to contents](../Readme.md#contents)

# Check transaction status

This API endpoint provides transaction lifecycle states at the moment of request.

We use it for the following cases:



* After creating a checkout transaction - to make a decision, on how to proceed with the payment
* When payment is finished, but the acquirer doesn't send a notification for some time (repeat request and wait while transaction status changed)
* When transaction state is changed to FINAL (accepted, failed)

## How to use data from response


Based on below responses can be chosen several ways what to do next:


---

**Note:** The list is sorted by the importance of checks.


---



1. `Response['form']` is not empty - redirect the user (GET/POST) to `Response['form']['url']`.
   Usually POST request - this is the payer bank 3DS page. So you have to send a form with enctype='application/x-www-form-urlencoded' attribute and this request should be InBrowser

   (Normal POST request: [Example](https://stackoverflow.com/a/15262442/2090853))


     
`Response['form']` can have the following structure: `['url' => url where make request, 'method' => 'http method GET|POST', 'fields' => [array with formFieldName => formFieldValue]]`

 **Example for GET:**

```
'url' => 'https://pay.skrill.com/app/?sid=9345093478', 'method' => 'GET', 'fields' => []
```


 **Example for POST:**
```
'url' => 'https://acs.anybank.com/',
'method' => 'POST',
'fields' => ['PaReq' => 'fmn3o8usfjlils', 'MD' => '8ec777d6-685d-4e06-b356-d7673acb47ba', 'TermUrl' => 'https://paydo.com/v1/url'
```


2. `Response['status']` is `pending` and `Response['url']` is empty - repeat the transaction status request after 5-10 seconds.
3. `Response['status']` is `success` - redirect to `Response['url']`
4. `Response['status']` is `fail` - redirect to `Response['url']`

**Note:** If you don't receive the final status of the transaction (Accepted or Failed), we recommend executing the request within an hour at intervals of 1 minute, 5 minutes, 10 minutes, and so on.



5. Exceptional case. Something went wrong on the PayDo side. Contact [PayDo support](https://paydo.com/en/contact-us/).

## Endpoint description


![Endpoint](https://img.shields.io/badge/-Endpoint-darkblue?style=for-the-badge)

```
GET https://paydo.com/v1/checkout/check-transaction-status/{txid}
```


![HEADERS](https://img.shields.io/badge/-Headers-darkviolet?style=for-the-badge)


```
Content-Type: application/json
```


![Parameters](https://img.shields.io/badge/-Parameters-gray?style=for-the-badge)


|Parameter|Type|Required|
|--- |--- |--- |
|txid|string|*|




## Request example


```php
curl -X GET \
  https://paydo.com/v1/checkout/check-transaction-status/{txid} \
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


* GET Redirect


```json
{
    "data": {
        "isSuccess": true,
        "status": "pending",
        "form": {
            "method": "GET",
            "url": "https://pay.skrill.com/app/?sid=468",
            "fields": []
        },
        "url": "https://pay.skrill.com/app/?sid=468",
        "txid": "TRANSACTION_IDENTIFIER"
    },
    "status": 1
}

```



* POST Redirect (send form)


```json
{
    "data": {
        "isSuccess": true,
        "status": "pending",
        "form": {
            "method": "POST",
            "url": "https://pay.skrill.com/app/?sid=468",
            "fields": {
                "PaReq": "fmn3o8usfjlils",
                "MD": "81962ed0-a65c",
                "TermUrl": "https://paydo.com/3ds-result"
            }
        },
        "url": "https://pay.skrill.com/app/?sid=468",
        "txid": "TRANSACTION_IDENTIFIER"
    },
    "status": 1
}

```



* Repeat request


```json
{
    "data": {
        "isSuccess": true,
        "status": "pending",
        "form": [],
        "url": "",
        "txid": "TRANSACTION_IDENTIFIER"
    },
    "status": 1
}

```



* Redirected to Success page


```json
   {
    "data": {
        "isSuccess": true,
        "status": "success",
        "message": "",
        "form": {
            "method": "GET",
            "url": "https://your_result_page_url/success",
            "fields": []
        },
        "url": "https://your_result_page_url/success",
        "txid": "TRANSACTION_IDENTIFIER",
        "transactionIdentifier": "TRANSACTION_IDENTIFIER"
    },
    "status": 1
}

```



* Redirected to Fail page


```json
{
    "data": {
        "isSuccess": true,
        "status": "fail",
        "message": "PayDo. Transaction rejected by security reason.", 
        "form": {
            "method": "GET",
            "url": "https://your_result_page_url/fail",
            "fields": []
        },
        "url": "https://your_result_page_url/fail",
        "txid": "TRANSACTION_IDENTIFIER",
        "transactionIdentifier": "TRANSACTION_IDENTIFIER"
    },
    "status": 1
}
```



## [→ Card tokenization](../Checkout/createCardToken.md)
