* [Back to contents](../Readme.md#contents)

# Success response example
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


```json
{
    "data": {
        "id": "423131",
        "status": 1,
        "dateTime": {
            "createdAt": 1566543694,
            "updatedAt": null
        }
    },
    "status": 1
}
```

![201](https://img.shields.io/badge/200-Created-green?style=for-the-badge)

```
HTTP/1.1 201 Created
```
![HEADERS](https://img.shields.io/badge/-Headers-darkviolet?style=for-the-badge)

```
Content-Type: application/json
```
![BODY](https://img.shields.io/badge/-Body-darkblue?style=for-the-badge)
```json
{
  "data": {
    "token": "RANDOM_TOKEN",
    "expired_at": 1644301111
  },
  "status": 1
}
```


Each successful response is a JSON object - a collection of key-value pairs, surrounded by curly braces.

The key-value pairs are each put into double quotation marks when both are strings. If the value is an integer (a whole number) or Boolean (true or false value), the quotation marks around the value are omitted. Each key-value pair is separated from the next by a comma.


|Key|Type|Description|
|--- |--- |--- |
|data|JSON object(s) OR string|Response data. Arbitrary object or array of objects.|
|status|Number|Don't care about it. It's required for internal purposes.|




---

_Note: "string" type for data is not a feature, this is a bug. We are unable to change this in the current API version because some integrations rely on it. But we will fix this in the next API versions._


## [→ Fail responses](../Response/failResponse.md)
