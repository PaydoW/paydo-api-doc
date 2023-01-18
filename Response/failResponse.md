* [Back to contents](../Readme.md#contents)

# Fail responses


## 
![401](https://img.shields.io/badge/401-Unauthorized-red?style=for-the-badge)
```
HTTP/1.1 401 Unauthorized
```
![HEADERS](https://img.shields.io/badge/-Headers-darkviolet?style=for-the-badge)

```
Content-Type: application/json
```
![BODY](https://img.shields.io/badge/-Body-darkblue?style=for-the-badge)

```json
{
    "message":"Full authentication is required to access this resource."
}
```


Please check you authorization \ authentication headers.


## 
![403](https://img.shields.io/badge/403-Forbidden-red?style=for-the-badge)
```
HTTP/1.1 403 HTTP Forbidden
```
![HEADERS](https://img.shields.io/badge/-Headers-darkviolet?style=for-the-badge)
```
Content-Type: application/json
```


![BODY](https://img.shields.io/badge/-Body-darkblue?style=for-the-badge)


```json
{
    "message": "Access denied."
}
```



## 
![404](https://img.shields.io/badge/404-Not%20Found-red?style=for-the-badge)
```
HTTP/1.1 404 Not Found
```
![HEADERS](https://img.shields.io/badge/-Headers-darkviolet?style=for-the-badge)

```
Content-Type: application/json
```


![BODY](https://img.shields.io/badge/-Body-darkblue?style=for-the-badge)


```json
{
    "message": "Invoice not found"
}
```



## 
![405](https://img.shields.io/badge/405-Invalid%20HTTP%20method%20used-red?style=for-the-badge)
```
HTTP/1.1 405 Method Not Allowed
```
![HEADERS](https://img.shields.io/badge/-Headers-darkviolet?style=for-the-badge)

```
Content-Type: application/json
```


![BODY](https://img.shields.io/badge/-Body-darkblue?style=for-the-badge)


```json
{
    "message": "Method Not Allowed"
}
```


Please use the correct HTTP method. (Specified in the endpoint description)


## 
![422](https://img.shields.io/badge/422-Payment%20method%20is%20not%20enabled-red?style=for-the-badge)
```
HTTP/1.1 422 Unprocessable Entity
```
![HEADERS](https://img.shields.io/badge/-Headers-darkviolet?style=for-the-badge)

```
Content-Type: application/json
```


![BODY](https://img.shields.io/badge/-Body-darkblue?style=for-the-badge)


```json
{
    "message": "Method must be enabled to use it"
}
```


Please contact [PayDo support](https://paydo.com/en/contact-us) if you want to enable additional payment methods.


## 
![422](https://img.shields.io/badge/422-Validation%20fails-red?style=for-the-badge)
```
HTTP/1.1 422 Unprocessable Entity
```
![HEADERS](https://img.shields.io/badge/-Headers-darkviolet?style=for-the-badge)
```
Content-Type: application/json
```


![BODY](https://img.shields.io/badge/-Body-darkblue?style=for-the-badge)


```json
{
    "message": {
        "email": [
            "This value should not be blank."
        ],
        "password": [
            "This value should not be blank."
        ]
    }
}
```



## 
![500](https://img.shields.io/badge/500-Server%20error-red?style=for-the-badge)
```
HTTP/1.1 500 Internal Server Error
```
![HEADERS](https://img.shields.io/badge/-Headers-darkviolet?style=for-the-badge)
```
Content-Type: application/json
```


![BODY](https://img.shields.io/badge/-Body-darkblue?style=for-the-badge)


```json
{
    "message": "Something went wrong, try again or contact support."
}
```


Please contact [PayDo support](https://paydo.com/en/contact-us) if you faced such cases.


## [→ Invoice - Create invoice](../Invoice/createInvoice.md)
