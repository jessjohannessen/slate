# Boards

## Get boards

> Example request:

```shell
curl -i -H "Content-Type: application/json" \
-H "Authorization: Bearer 6982d4986262c61e505180782eec09d452911235" \
-X GET http://api.linkfire.com/boards
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
            "href": "http://api.linkfire.dev/boards?page=1"
        },
        "first": {
            "href": "http://api.linkfire.dev/boards"
        },
        "last": {
            "href": "http://api.linkfire.dev/boards?page=1"
        }
    },
    "_embedded": {
        "board": [
            {
                "id": 215,
                "name": "drakes old board",
                "creatorId": 302,
                "createdDate": "2014-07-24 15:14:03",
                "updatedDate": "2014-07-24 15:16:23",
                "imageName": null,
                "imageUrl": "",
                "youtubeUser": "DrakeVEVO",
                "instagramUser": null,
                "tags": [
                    "hansi",
                    "hinterseer"
                ],
                "membersCount": 1,
                "_embedded": {
                    "members": [
                        {
                            "id": 475,
                            "boardId": 215,
                            "userId": 302,
                            "role": 0,
                            "roleName": "Admin",
                            "_embedded": {
                                "user": {
                                    "id": 302,
                                    "firstName": "Jess",
                                    "lastName": "Johannessen",
                                    "email": "jj@linkfire.com",
                                    "password": null,
                                    "createdDate": "2014-01-21 13:43:37",
                                    "updatedDate": "2014-07-21 15:36:14",
                                    "locked": false,
                                    "lockedReason": null,
                                    "trialId": 3,
                                    "trialType": "Business",
                                    "trialExpires": "2014-08-05 13:43:37",
                                    "activationCode": null,
                                    "imageName": "",
                                    "imageUrl": "",
                                    "_links": {
                                        "self": {
                                            "href": "http://api.linkfire.dev/users/302"
                                        }
                                    }
                                }
                            },
                        }
                    ]
                },
                "_links": {
                    "self": {
                        "href": "http://api.linkfire.dev/boards/215"
                    },
                    "members": {
                        "href": "http://api.linkfire.dev/boards/215/members"
                    }
                }
            },
        ]
    },
    "page_count": 1,
    "page_size": 25,
    "total_items": 6
}
```

This service enables the user to retrieve, create and manipulate boards.

### HTTP Request

`GET /boards`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
search | | Search for boards containing a this text
tags | | Search boards with this tags (can be a comma-separated list)




## Get a specific board

> Example request:

```shell
curl -i -H "Content-Type: application/json" \
-H "Authorization: Bearer 6982d4986262c61e505180782eec09d452911235" \
-X GET http://api.linkfire.com/board/215
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
    "id": 215,
    "name": "drakes old board",
    "creatorId": 302,
    "createdDate": "2014-07-24 15:14:03",
    "updatedDate": "2014-07-24 15:16:23",
    "imageName": null,
    "imageUrl": "",
    "youtubeUser": "DrakeVEVO",
    "instagramUser": null,
    "tags": [
        "hansi",
        "hinterseer"
    ],
    "membersCount": 1,
    "_embedded": {
        "members": [
            {
                "id": 475,
                "boardId": 215,
                "userId": 302,
                "role": 0,
                "roleName": "Admin",
                "_embedded": {
                    "user": {
                        "id": 302,
                        "firstName": "Jess",
                        "lastName": "Johannessen",
                        "email": "jj@linkfire.com",
                        "password": null,
                        "createdDate": "2014-01-21 13:43:37",
                        "updatedDate": "2014-07-21 15:36:14",
                        "locked": false,
                        "lockedReason": null,
                        "trialId": 3,
                        "trialType": "Business",
                        "trialExpires": "2014-08-05 13:43:37",
                        "activationCode": null,
                        "imageName": "",
                        "imageUrl": "",
                        "_links": {
                            "self": {
                                "href": "http://api.linkfire.dev/users/302"
                            }
                        }
                    }
                },
                "_links": {
                    "self": {
                        "href": "http://api.linkfire.dev/boards/215/members/475"
                    }
                }
            }
        ]
    },
    "_links": {
        "self": {
            "href": "http://api.linkfire.dev/boards/215"
        },
        "members": {
            "href": "http://api.linkfire.dev/boards/215/members"
        }
    }
}
```

Returns the details of a single board, including members.

### HTTP Request

`GET /boards/[:board_id]`




## Create board

> Example request:

```shell
curl -i -H "Content-Type: application/json" \
-H "Authorization: Bearer 6982d4986262c61e505180782eec09d452911235" \
-X POST --data '
{
   "name": "drakes old board",
   "imageUrl": "http://rack.2.mshcdn.com/media/ZgkyMDEyLzEyLzI2LzNhL2RyYWtlLmVhNzFlLmpwZwpwCXRodW1iCTk1MHg1MzQjCmUJanBn/03ab67e5/623/drake.jpg",
   "youtubeUser": "DrakeVEVO",
   "instagramUser": "",
   "tags": "drake music rap"
}
' http://api.linkfire.com/boards
```

Creates a new board.

### Http Request

`POST /boards`

### Http parameters

Parameter | Required | Description
--------- | -------- | -----------
name | Yes | The name of the board
imageUrl | No | An image URL for board image
youtubeUser | No | A YouTube username
instagramUser | No | An Instagram username
tags | No | A collection of tags separated by a single space
