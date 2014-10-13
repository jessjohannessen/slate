# Links

## Get links

> Example request:

```shell
curl -i -H "Content-Type: application/json" \
-H "Authorization: Bearer 6982d4986262c61e505180782eec09d452911235" \
-X GET http://api.linkfire.com/links
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
    "_links": {
        "self": {
            "href": "http://api.linkfire.dev/links?page=1"
        },
        "first": {
            "href": "http://api.linkfire.dev/links"
        },
        "last": {
            "href": "http://api.linkfire.dev/links?page=5"
        },
        "next": {
            "href": "http://api.linkfire.dev/links?page=2"
        }
    },
    "_embedded": {
        "link": [
            {
                "id": 6777,
                "shortUrl": "http://lnk.to/-sUoU",
                "code": "-sUoU",
                "originalUrl": "http://open.spotify.com/track/2fZwRlNb2wYuAyDIW6RbrZ",
                "title": "Double Plaidinum by Lagwagon",
                "description": "Preview and download Double Plaidinum on iTunes. See ratings and read customer reviews.",
                "image": "53d20b3147a23_cover326x326.jpeg",
                "video": null,
                "sound": null,
                "userId": 302,
                "boardId": null,
                "domainId": 1,
                "createdDate": "2014-07-25 09:46:27",
                "updatedDate": "2014-07-25 09:46:27",
                "_links": []
            }
        ]
    },
    "page_count": 5,
    "page_size": 25,
    "total_items": 114
}
```

This service enables the user to retrieve, create and manipulate links.

### HTTP Request

`GET /links`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
search | | Search for links containing a this text





## Get a specific link

> Example request:

```shell
curl -i -H "Content-Type: application/json" \
-H "Authorization: Bearer 6982d4986262c61e505180782eec09d452911235" \
-X GET http://api.linkfire.com/links/6777
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
    "id": 6777,
    "shortUrl": "http://lnk.to/-sUoU",
    "code": "-sUoU",
    "originalUrl": "http://open.spotify.com/track/2fZwRlNb2wYuAyDIW6RbrZ",
    "title": "Double Plaidinum by Lagwagon",
    "description": "Preview and download Double Plaidinum on iTunes. See ratings and read customer reviews.",
    "image": "53d20b3147a23_cover326x326.jpeg",
    "video": null,
    "sound": null,
    "userId": 302,
    "boardId": null,
    "domainId": 1,
    "createdDate": "2014-07-25 09:46:27",
    "updatedDate": "2014-07-25 09:46:27",
    "_links": {
        "self": {
            "href": "http://api.linkfire.dev/links/6777"
        }
    }
}
```

Returns the details of a single link.

### HTTP Request

`GET /links/[:link_id]`




## Create link

> Example request:

```shell
curl -i -H "Content-Type: application/json" \
-H "Authorization: Bearer 6982d4986262c61e505180782eec09d452911235" \
-X POST --data '
{
   "title": "Double Plaidinum by Lagwagon",
   "description": "Preview and download Double Plaidinum on iTunes. See ratings and read customer reviews.",
   "boardId": 1,
   "domainId": 1,
   "code": "-sUoU",
   "originalUrl": "http://open.spotify.com/track/2fZwRlNb2wYuAyDIW6RbrZ"
}
' http://api.linkfire.com/links
```

Creates a new link.

### Http Request

`POST /links`

### Http parameters

Parameter | Required | Description
--------- | -------- | -----------
originalUrl | Yes | The original URL of the link.
title | Yes | The title of the shortlink
description | Yes | The description of the shortlink
code | No | A shortcode affiliated with the link.
boardId | No | A valid board ID.
domainId | No | A valid domain ID.
