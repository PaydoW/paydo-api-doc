* [Back to contents](../Readme.md#contents)

### Get concrete refund details

**Endpoint:**

`GET https://paydo.com/v1/refunds/user-refunds?query[identifier]={paydoRefundId}`

**Headers:**

    Content-Type: application/json
    Authorization: Bearer eyJ0eXAiO...

**Request example:**

```shell script
curl -X GET \
  https://paydo.com/v1/refunds/user-refunds?query[identifier]={paydoRefundId} \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer eyJ0eXAiOiJKV...
```
