# Authentication

<aside class="notice">
Linkfire API uses OAuth2
</aside>

Every user will need to create their own credentials after signing up to Linkfire. The credentials will enable the user to authenticate with the following grant types:

* Client credentials (client_credentials)
* User credentials (password)
* Authorization code (not implemented)
* Refresh token (refresh_token)







## Client credentials

> Example request:

```shell
curl -i -H "Content-Type: application/json" -X POST --data '
{
    "grant_type": "client_credentials",
    "client_id": "a5d1a96d462dec39",
    "client_secret": "97974671a60d1cfcefa52118dc176fcafe38b518de105203"
}
' http://api.linkfire.com/oauth
```

> Example response:

```shell
HTTP/1.1 200 OK
Server: nginx/1.6.0
Date: Fri, 25 Jul 2014 12:47:22 GMT
Content-Type: application/json
Transfer-Encoding: chunked
Connection: keep-alive
X-Powered-By: PHP/5.5.14
Cache-Control: no-store
Pragma: no-cache

{
    "access_token": "6982d4986262c61e505180782eec09d452911235",
    "expires_in": 86400,
    "token_type": "Bearer",
    "scope": "basic"
}
```

Sign in as a predefined user. Useful in applications that are using the API on behalf of a single user only.

### HTTP Request

`POST /oauth`

### HTTP Parameters

Parameter | Required | Description
--------- | -------- | -----------
grant_type | Yes | Must be: client_credentials
client_id | Yes | Your client ID
client_secret | Yes | Your client secret

### Response

Parameter | Description
--------- | -----------
access_token | The access token (use this in subsequent requests)
expires_in | Number of seconds before the token expires
token_type | Type of token (default: Bearer)
scope | Access scope (default: basic)

<aside class="notice">
You must create your own client credentials at [https://linkfire.com](https://linkfire.com).
</aside>





## User credentials

> Example request:

```shell
curl -i -H "Content-Type: application/json" -X POST --data '
{
    "grant_type": "password",
    "client_id": "a5d1a96d462dec39",
    "client_secret": "97974671a60d1cfcefa52118dc176fcafe38b518de105203",
    "username": "jj@linkfire.com",
    "password": "linkfire"
}
' http://api.linkfire.com/oauth
```

> Example response:

```shell
HTTP/1.1 200 OK
Server: nginx/1.6.0
Date: Fri, 25 Jul 2014 12:43:58 GMT
Content-Type: application/json
Transfer-Encoding: chunked
Connection: keep-alive
X-Powered-By: PHP/5.5.14
Cache-Control: no-store
Pragma: no-cache

{
    "access_token": "6982d4986262c61e505180782eec09d452911235",
    "expires_in": 86400,
    "token_type": "Bearer",
    "scope": "basic",
    "refresh_token": "f2c09a25abdd02064154c77f4510001cb0967e8c"
}
```

Sign in as any user. Useful in applications designed to accommodate any user.

### Http request

`POST /oauth`

### Http parameters

Parameter | Required | Description
--------- | -------- | -----------
grant_type | Yes | Must be: password
client_id | Yes | Your client ID
client_secret | Yes | Your client secret
username | Yes | E-mail of a Linkfire user
password | Yes | Password of a Linkfire user

### Response

Parameter | Description
--------- | -----------
access_token | The access token (use this in subsequent requests)
expires_in | Number of seconds before the token expires
token_type | Type of token (default: Bearer)
scope | Access scope (default: basic)
refresh_token | Token used to refresh access token

<aside class="notice">
You must create your own client credentials at [https://linkfire.com](https://linkfire.com).
</aside>





## Refresh token

(coming soon)





## Bearer token

> Example request

```shell
curl -i -H "Content-Type: application/json" \
-H "Authorization: Bearer 6982d4986262c61e505180782eec09d452911235" \
-X GET http://api.linkfire.com/links
```

After optaining a valid access token, one must provide the token in the header of all requests to gain access to all API endpoints:

`Authorization: [token_type] [access_token]`

Header | Value
------ | -----
Authorization: | Bearer 6982d4986262c61e505180782eec09d452911235

### Headers

Header | Value
------ | -----
Authorization: | Bearer 6982d4986262c61e505180782eec09d452911235
Content-type: | application/json


## Encryption

The credentials are values stored in the database in an encrypted/encoded state:

Table: oauth_clients

Field | Value
----- | -----
client_id | user email address (base64 encoded)
client_secret | combined string of email, user id and salt (bcrypt value of base64 encoded md5 of values)

Table: oauth_users

Field | Value
----- | -----
username | email address
password | (bcrypt value of user generated string)






## References

[http://bshaffer.github.io/oauth2-server-php-docs/](http://bshaffer.github.io/oauth2-server-php-docs/)
[http://www.zimuel.it/oauth2-apigility/](http://www.zimuel.it/oauth2-apigility/)
[https://github.com/zfcampus/zf-oauth2](https://github.com/zfcampus/zf-oauth2)