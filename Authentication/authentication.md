* [Back to contents](../Readme.md#contents)

# Bearer Authentication

* [Bearer Authentication](#bearer-authentication)
* [Get authentication token](#get-authentication-token)

Several requests to Paydo API require authentication.

Paydo API Authentication based on JWT tokens and using [Bearer Authentication](https://swagger.io/docs/specification/authentication/bearer-authentication/).
The client must send this token in the `Authorization` header when making requests to protected resources:

HTTP-Headers
```
Content-Type: application/json
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpZCI6IjEwMDAyIiwiYWNjZXNzVG9rZW4iOm51bGwsInRpbWUiOjE1NjY5MTk4NDJ9.jebGttoGUOGQORsPyr5smSbE01fEGDjFgUkBCF342sc
``` 

----
**Note:** Authentication with `token` header to send token marked as **deprecated**. 
This functionality may be removed in next major api version.

----     

## Get authentication token

You can **create** and **view** your API keys in [your account](https://account.paydo.com/projects/jwt-token).

![Paydo JWT Tokens page](../images/paydo-jwt-page.png)

----
**Note:** After creating token you will see it only once, right after create token.
But you can create as many tokens as you need.

----

After **delete** token you can't authenticate with this token anymore.

You can set token **expiration date**. After this date you can't authenticate with this token anymore.
If expiration date is not set, the token can be used until it is deleted. 

