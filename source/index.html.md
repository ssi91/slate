---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell

toc_footers:
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Authentication

> To authorize, use this code:

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: Bearer <access token>"
```

> Make sure to replace `<access token>` with your Access Token.

`Authorization: Bearer <access token>`

<aside class="notice">
You must replace <code>&lt;access token&gt;</code> with your personal Access Token.
</aside>

# Users

## Create A New User

```shell
curl -X POST http://127.0.0.1/api/v1/users/ -H 'content-type: multipart/form-data' -F email=ssi@ssi.com -F password=1234
```

> The above command returns json structured like this:

```json
{
    "uuid": "4484e07e-df0e-4a40-85fb-f2b17ffb080f",
    "refresh": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ0b2tlbl90eXBlIjoicmVmcmVzaCIsImV4cCI6MTU1MTg0OTc1NywianRpIjoiMDY5YzJkOGI3ZDIzNDgyZjgwYTlmZTA1MGZhMGFlNTMiLCJ1c2VyX2lkIjoiNDQ4NGUwN2UtZGYwZS00YTQwLTg1ZmItZjJiMTdmZmIwODBmIn0.FHa3X4VSQLSA5qf6sJyqynY5sOAmRIikiHLIIWl7ljI",
    "access": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ0b2tlbl90eXBlIjoiYWNjZXNzIiwiZXhwIjoxNTUxNzYzNjU3LCJqdGkiOiI1ZGI3M2QxNmE5MzM0YTZhOWZhNDNlZTZmMzA4YmM1OCIsInVzZXJfaWQiOiI0NDg0ZTA3ZS1kZjBlLTRhNDAtODVmYi1mMmIxN2ZmYjA4MGYifQ.UzzrzHPwh65jVTjDEDa2B3RQq0JhTOsK3YY0LxRAm0Y"
}
```

This endpoint creates a new user

### HTTP Request

`POST /api/v1/users/`

### Query Parameters

Parameter | Default | Required | Description
--------- | ------- | -------- |-----------
email | | true | Must be unique.
password | | true | Must contain at least four chars.


## Get All Users

> The above command returns json structured like this:

```json
[
    {
        "uuid": "ab8fa607-15f5-4dcc-a0e2-fb12dcea88ac",
        "email": "ssi1@ssi.com",
        "is_staff": false,
        "is_active": true,
        "is_admin": false,
        "date_created": "2019-03-05T04:26:02.828464Z"
    },
    {
        "uuid": "4484e07e-df0e-4a40-85fb-f2b17ffb080f",
        "email": "ssi111@ssi.com",
        "is_staff": false,
        "is_active": true,
        "is_admin": false,
        "date_created": "2019-03-05T05:22:37.020382Z"
    }
]
```

This endpoint retrieves all users.

### HTTP Request

`GET /api/v1/users/`

## Get a Specific User

> The above command returns JSON structured like this:

```json
{
    "uuid": "4484e07e-df0e-4a40-85fb-f2b17ffb080f",
    "email": "ssi111@ssi.com",
    "is_staff": false,
    "is_active": true,
    "is_admin": false,
    "date_created": "2019-03-05T05:22:37.020382Z"
}
```

This endpoint retrieves a specific user.

### HTTP Request

`GET /api/v1/users/<UUID>/`

### URL Parameters

Parameter | Description
--------- | -----------
UUID | The UUID of the user to retrieve


# User's Profile

## Create A User's Profile

```shell
curl -X PUT http://127.0.0.1:8000/api/v1/users/f8bf245e-7b5c-48f1-a178-fab9177155db/profile/ -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
    "user_id": "f8bf245e-7b5c-48f1-a178-fab9177155db",
    "username": null,
    "email": "ssi@mail.com",
    "birth_date": null,
    "avatar": "http://127.0.0.1:8000/media/avatar.png",
    "position": null,
    "city": null,
    "country": null,
    "gender": null,
    "orientation": null,
    "interests": [],
    "description": ""
}
```

This endpoint creates profile of the user.

### HTTP Request

`PUT /api/v1/users/<UUID>/profile/`

## Edit A User's Profile

```shell
curl -X PATCH \
  http://127.0.0.1:8000/api/v1/users/f8bf245e-7b5c-48f1-a178-fab9177155db/profile/ \
  -H 'Content-Type: application/json' \
  -d '{"username": "test"}'
```

> The above command returns JSON structured like this:

```json
{
    "user_id": "f8bf245e-7b5c-48f1-a178-fab9177155db",
    "username": "test",
    "email": "ssi@mail.com",
    "birth_date": null,
    "avatar": "http://127.0.0.1:8000/media/avatar.png",
    "position": null,
    "city": null,
    "country": null,
    "gender": null,
    "orientation": null,
    "interests": [],
    "description": ""
}
```

This endpoint edit profile of the user.

### HTTP Request

`PATCH /api/v1/users/<UUID>/profile/`

## Get Profile of the Specific User

```shell
curl -X GET http://127.0.0.1:8000/api/v1/users/f8bf245e-7b5c-48f1-a178-fab9177155db/profile/
```

> The above command returns JSON structured like this:

```json
{
    "user_id": "f8bf245e-7b5c-48f1-a178-fab9177155db",
    "username": "test",
    "email": "ssi@mail.com",
    "birth_date": null,
    "avatar": "http://127.0.0.1:8000/media/avatar.png",
    "position": null,
    "city": null,
    "country": null,
    "gender": null,
    "orientation": null,
    "interests": [],
    "description": ""
}
```

This endpoint retrieves profile of the specific user.

### HTTP Request

`GET /api/v1/users/<UUID>/profile/`
