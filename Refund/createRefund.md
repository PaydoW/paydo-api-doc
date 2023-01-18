* [Back to contents](../Readme.md#contents)

# Create refund



* [Endpoint description](#endpoint-description)
  * [Refund type](#refund-type)
* [Request example](#request-example)
* [Successful response example](#successful-response-example)
* [Error response examples](#error-response-examples)

## Endpoint description


**Important!** To create a refund request, you must first [receive a token for your user](../Authentication/authentication.md), as described in the login section. When creating a request for a refund, you must transfer a personal token in the header of the HTTP request. 


### Create Refund Request

![Endpoint](https://img.shields.io/badge/-Endpoint-darkblue?style=for-the-badge)


```
POST https://paydo.com/v1/refunds/create
```


![HEADERS](https://img.shields.io/badge/-Headers-darkviolet?style=for-the-badge)


```
Content-Type: application/json
Authorization: Bearer YOUR_JWT_TOKEN
```


![Parameters](https://img.shields.io/badge/-Parameters-gray?style=for-the-badge)

|Parameter|Type|Description|Required|
|--- |--- |--- |--- |
|transactionIdentifier|string|Your checkout transaction identifier|*|
|refundType|number|[Refund type](#refund-type)|*|
|amount|number|Refund amount in the currency of the parent transaction|*|
|metadata|number|Arbitrary structure object to store any additional merchant data. Result JSON should be less than 800 kB|*|




## Refund type

There are 2 variants possible:


```
1 - all transaction amount
2 - partial amount
```



## Request example


```json
{
    "transactionIdentifier": "d839c714-1111-0000-1111-73592597c6e1",
    "refundType": 2,
    "amount": "10",
    "metadata": {
      "internal merchant id": "example"
    }
}
```


---
## Successful response example

In case of a successful response, you can get a refund identifier from the header `identifier`

![200](https://img.shields.io/badge/200-OK-green?style=for-the-badge)

```
HTTP/1.1 200 OK
```
![HEADERS](https://img.shields.io/badge/-Headers-darkviolet?style=for-the-badge)
```
Content-Type: application/json
Authorization: Bearer YOUR_JWT_TOKEN
```
![BODY](https://img.shields.io/badge/-Body-darkblue?style=for-the-badge)

```
{
    "data": "",
    "status": 1,
    "identifier": "81962ed0-1111-2222-3333-b3dbf9750399"
}
```


---
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



```
{
  "message": "Refund amount is bigger than transaction amount"
}
```


In case of incorrect transaction id.

![422](https://img.shields.io/badge/422-Payment%20method%20is%20not%20enabled-red?style=for-the-badge)
```
HTTP/1.1 422 Unprocessable Entity
```
![HEADERS](https://img.shields.io/badge/-Headers-darkviolet?style=for-the-badge)

```
Content-Type: application/json
```


![BODY](https://img.shields.io/badge/-Body-darkblue?style=for-the-badge)


```
{
  "message": "Transaction not found"
}
```



![401](https://img.shields.io/badge/401-Unauthorized-red?style=for-the-badge)
```
HTTP/1.1 401 Unauthorized
```
![HEADERS](https://img.shields.io/badge/-Headers-darkviolet?style=for-the-badge)

```
Content-Type: application/json
```
![BODY](https://img.shields.io/badge/-Body-darkblue?style=for-the-badge)

```
{
  "message": "Full authentication is required to access this resource."
}
```
---


## [→ Get refund details ](../Refund/getRefund.md)
