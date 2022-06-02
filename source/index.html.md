---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - python
  
includes:
  - errors

search: true

code_clipboard: true

meta:
  - name: description
    content: Documentation for the Serpbot API
---

# Introduction

Welcome to the Serpbot API! You can use our API to access Serpbot API endpoints, which are used to add websites to monitor as well as provide statistics on their ranking in Google and Bing.

We have language bindings in Shell, and Python! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

# Authentication

> To authorize, use this code:

```python
import requests

r = requests.get("api_endpoint_here", headers={"Authorization": "Bearer abcd"})
```

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here" \
  -H "Authorization: Bearer abcd"
```

> Make sure to replace `abcd` with your API key.

Serpbot makes use of bearer tokens to authenticate and validate incoming requests. The token can be generated upon calling the login endpoint with valid credentials.

Serpbot expects for this token be included in all API requests to the server in a header that looks like the following:

`Authorization: Bearer abcd`

<aside class="notice">
You must replace <code>abcd</code> with your token.
</aside>

# User

## Login

```python
import requests

r = requests.post("https://serpbot.co/api/login", data={"username":"test","password":"test"})
```

```shell
curl "https://serpbot.co/api/login" \
  -X "POST" \
  -H "Content-Type: application/json" \
  -d '{
        "password": "test",
        "username": "test"
      }'
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "token": "eyJraWQiOiJHTUdNVnFJZ3Q1WEpwY0xnbHBBWVQ5aDExdnNtQVdmOFRLeDFKRWpncGVjPSIsImFsZyI6IlJTMjU2In0.eyJzdWIiOiI4NGJkYjQxYS1iNWI4LTQ1NjItOGQ5NS1kNWM0ZjcxNzk0ZGUiLCJlbWFpbF92ZXJpZmllZCI6ZmFsc2UsImlzcyI6Imh0dHBzOlwvXC9jb2duaXRvLWlkcC51cy13ZXN0LTIuYW1hem9uYXdzLmNvbVwvdXMtd2VzdC0yX1luaEVsZG4zMCIsImNvZ25pdG86dXNlcm5hbWUiOiJuaWNvbGFzIiwib3JpZ2luX2p0aSI6ImE4NTFiYTllLTZkOTItNGRmZi04MDc0LTU4NjQzOTIzODRmNSIsImF1ZCI6IjU1aGduYXQ1aHNhOGgyYjlhOW44bWU2Zm9sIiwiZXZlbnRfaWQiOiIwM2JhYzhlYi0zOTZlLTRkM2ItOWY5MS1mNmQzYjYzZDM1OTgiLCJ0b2tlbl91c2UiOiJpZCIsImF1dGhfdGltZSI6MTY0ODUwOTg2MiwiZXhwIjoxNjQ4NTEzNDYyLCJpYXQiOjE2NDg1MDk4NjIsImp0aSI6IjRkNjU4N2I3LThiNjctNDQ3Yi1hODM0LTYzOTUxMTNmZmIzMSIsImVtYWlsIjoidGVtcEBvbmludGltZS5jb20ifQ.ADmuqU-NlFdhvnC_88GBX5zE7W0-nndO1oHQMn__0Fdk3tfVto9IY5pHe8ksigBDSmMjs5lrQz3iehpaRjchsa2bpTJjEWIrqgViQTzApOaSrPwgFdiCvJ8EPodVBKeg6I0_GlOAaaABopebFB0Jla3XtEqjQEd3RVIVEThlqZ4aCFslrTxA2yRjNg8w6gm2qeAjTsLRQi8Q9CYkOmG5_j2ACR6simqBbMo3Yd2GK9oo-7p7jYwsNk2fIg2k67LFowu-OuSsMbCbuDK47dbYZzMIc9Ibm5yTx3afsp9FXMQUVsnVA27YZbXFLNtiT6aeSlXI4C0MDUriWULagFWJKw"
  },
  "error": "",
  "status": "success"
}

```

This endpoint is used to login and retrieve the bearer token used for authentication on the other endpoints.

### HTTP Request

`POST https://serpbot.co/api/login`

## Signup

```python
import requests

r = requests.post("https://serpbot.co/api/signup", data={"username":"test","password":"test","email":"test@test.com"})
```

```shell
curl "https://serpbot.co/api/signup" \
  -X "POST" \
  -H "Content-Type: application/json" \
  -d '{
      "email": "test@test.com",
      "password": "test",
      "username": "test"
      }'
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "info": "Please confirm your signup, check your email for the validation URL"
  },
  "error": "",
  "status": "success"
}

```

This endpoint is used to create a user.

### HTTP Request

`POST https://serpbot.co/api/signup`

# Trend

## Get Trends by Search Engine

```python
import requests

r = requests.get("https://serpbot.co/api/trend/614403ef-c9cc-4132-bed1-ec360ea036ef/engine", headers={"Authorization": "Bearer abcd"})
```

```shell
curl "https://serpbot.co/api/trend/614403ef-c9cc-4132-bed1-ec360ea036ef/engine" \
  -X "GET" \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer abcd"
```
> Make sure to replace `abcd` with your token and `engine` with either "google" or "bing".

> The above command returns JSON structured like this:

```json
{
  "data": {
    "trend": {
      "keywords": [
        {
          "data": [
            0,
            80,
            80,
            80,
            0
          ],
          "label": "testing"
        },
        {
          "data": [
            80,
            0,
            0,
            80,
            80
          ],
          "label": "test"
        }
      ],
      "labels": [
        "2022-03-25",
        "2022-03-26",
        "2022-03-27",
        "2022-03-28",
        "2022-03-29"
      ]
    }
  },
  "error": "",
  "status": "success"
}

```

This endpoint is used to fetch the trends of all websites associated with the user for a given search engine (either bing or google).

### HTTP Request

`POST https://serpbot.co/api/trend/614403ef-c9cc-4132-bed1-ec360ea036ef/{engine}`

### URL Parameters

Parameter | Description
--------- | -----------
engine | The search engine (either google or bing)

# Website

## Get All Websites

```python
import requests

r = requests.get("https://serpbot.co/api/website", headers={"Authorization": "Bearer abcd"})
```

```shell
curl "https://serpbot.co/api/website" \
  -X "GET" \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer abcd"
```
> Make sure to replace `abcd` with your API key.

> The above command returns JSON structured like this:

```json
{
  "data": {
    "websites": [
      {
        "domain": "test.com",
        "id": "614403ef-c9cc-4132-bed1-ec360ea036ef",
        "keywords": [
          "test2",
          "test"
        ],
        "num_keywords": 2
      }
    ]
  },
  "error": "",
  "status": "success"
}
```

This endpoint retrieves all websites belonging to the authenticated user.

### HTTP Request

`GET https://serpbot.co/api/website`

## Get a Specific Website

```python
import requests

r = requests.get("https://serpbot.co/api/website/614403ef-c9cc-4132-bed1-ec360ea036ef", headers={"Authorization": "Bearer abcd"})
```

```shell
curl "http://example.com/api/website/614403ef-c9cc-4132-bed1-ec360ea036ef" \
  -X "GET" \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer abcd"
```
> Make sure to replace `abcd` with your API key.

> The above command returns JSON structured like this:

```json
{
  "data": {
    "website": {
      "domain": "test.com",
      "id": "614403ef-c9cc-4132-bed1-ec360ea036ef",
      "keywords": [
        "test2",
        "test"
      ],
      "num_keywords": 2
    }
  },
  "error": "",
  "status": "success"
}
```

This endpoint retrieves a specific website.

### HTTP Request

`GET https://serpbot.co/api/website/{id}`

### URL Parameters

Parameter | Description
--------- | -----------
id | The id of the website to retrieve

## Create a Specific Website

```python
import requests

r = requests.post("https://serpbot.co/api/website", headers={"Authorization": "Bearer abcd"}, data={"domain":"test.com","keywords":["test"]})
```

```shell
curl "https://serpbot.co/api/website" \
  -X "POST" \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer abcd" \
  -d '{
      "domain": "test.com",
      "keywords": [
        "test"
      ]
    }'
```
> Make sure to replace `abcd` with your API key.

> The above command returns JSON structured like this:

```json
{
  "data": {},
  "error": "",
  "status": "success"
}
```

This endpoint creates a specific website.

### HTTP Request

`POST https://serpbot.co/website`


## Update a Specific Website

```python
import requests

r = requests.put("https://serpbot.co/api/website/614403ef-c9cc-4132-bed1-ec360ea036ef", headers={"Authorization": "Bearer abcd"}, data={"keywords":["test"]})
```

```shell
curl "https://serpbot.co/api/website/614403ef-c9cc-4132-bed1-ec360ea036ef" \
  -X "PUT" \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer abcd" \
  -d '{
      "keywords": [
        "test"
      ]
    }'
```
> Make sure to replace `abcd` with your API key.

> The above command returns JSON structured like this:

```json
{
  "data": {},
  "error": "",
  "status": "success"
}
```

This endpoint updates a specific website.

### HTTP Request

`PUT https://serpbot.co/website/{id}`

### URL Parameters

Parameter | Description
--------- | -----------
id | The id of the website to delete

## Delete a Specific Website

```python
import requests

r = requests.delete("https://serpbot.co/api/website/614403ef-c9cc-4132-bed1-ec360ea036ef", headers={"Authorization": "Bearer abcd"})
```

```shell
curl "https://serpbot.co/api/website/614403ef-c9cc-4132-bed1-ec360ea036ef" \
  -X "DELETE" \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer abcd"
```
> Make sure to replace `abcd` with your API key.

> The above command returns JSON structured like this:

```json
{
  "data": {},
  "error": "",
  "status": "success"
}
```

This endpoint deletes a specific website.

### HTTP Request

`DELETE https://serpbot.co/api/website/{id}`

### URL Parameters

Parameter | Description
--------- | -----------
id | The id of the website to delete
