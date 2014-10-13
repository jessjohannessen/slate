# Users

## Create

> Example request

```shell
curl -i -H "Content-Type: application/json" -X POST --data '
{
   "firstName": "John",
   "lastName": "Appleseed",
   "email": "john@apple.com",
   "password": "qwerty123",
   "invitationCode": ""
}
' http://api.linkfire.com/create-user
```

> Example response

This service enables the creation of a user. When a user is created, an e-mail containing an activation is sent to the specified e-mail address. The user must use this code to activate before logging in.

### Http request

`POST /create-user`

### Http parameters

Parameter | Required | Description
--------- | -------- | -----------
firstName | Yes | First name
lastName | Yes | Last name
email | Yes | The e-mail of the user
password | Yes | The password for login
invitationCode | No | If the user is invited to a board, put the invitation code in this field



## Activate

> Example request

```shell
curl -i -H "Content-Type: application/json" -X POST --data '
{
   "hash": "3f3d7e2eae2465d6ebcafbe610f4bb77f68130c2"
}
' http://api.linkfire.com/activation
```

> Example response

This service can activate a user not previously activated.

### Http Request

`POST /activation`

### Http parameters

Parameter | Required | Description
--------- | -------- | -----------
hash | Yes | The activation hash

