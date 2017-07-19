---
title: API Reference

language_tabs:
  - shell

includes:
  - errors

search: true
---

# Introduction

Welcome to the Cognation API! You can use our API to access others AI APIs for image recognition, natural language processing...

We have language bindings in Shell! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

# Authentication

> To authorize, use this code:

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: <your-jwt>"
```


> Make sure to replace `<your-jwt>` with your token.


Cognation expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: Bearer <your-jwt>`

The token is a JSON Web Token (JWT) that you can generate for each project that uses Cognation. To generate it you need a key provided by the developers.


# Projects

## Get a Specific Project

```shell
curl "http://cognation.io/api/projects/f8c86f98-357d-4eff-8926-146a5b30e146"
  -H "Authorization: Bearer <your-jwt>"
```

> The above command returns JSON structured like this:

```json
{
  "id": "f8c86f98-357d-4eff-8926-146a5b30e146",
  "name": "My project",
  "token": "<hashed project's token>",
  "google_service_token": "<hashed google service account json>",
  "aws_rekognition_token": "<hashed aws secrets>",
  "google_vision_token": "<hashed google vision token>",
  "created_at": "2017-07-11T12:16:40.534422+02:00",
  "update_at": "2017-07-11T12:16:40.534422+02:00",
}
```

This endpoint retrieves a specific project.

### HTTP Request

`GET /projects/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the project to retrieve


## Create a Project

```shell
curl -POST "http://cognation.io/api/projects" \
  -H "Authorization: <your-api-key>" \
  -d '{
        "name": "my project",
        "google_service_token": "<google service account json>",
        "aws_rekognition": "<AWS Access Key ID>,<AWS Access Secret>",
        "google_vision_token":"<your google vision api key>"
      }'
```

> The above command returns JSON structured like this:

```json
{
  "id": "43f92291-b546-4424-bd58-5f80b7f00860",
  "name": "my project",
  "token": "32bb314d438f81b2f138e61e3c8e74c3",
  "google_service_token":"<hashed service account>",
  "google_vision_token": "<hashed google vision token>",
  "aws_rekognition_token": "<hashed aws rekognition token>",
  "creation_date": "2017-07-12T17:27:27.445245555+02:00",
  "update_date": "2017-07-12T17:27:28.657308446+02:00"
}
```

This endpoint retrieves a specific project.
<aside class="notice">The retrieved token should be safely stored, it will be used to authenticate your request on a project and there is no other way to get it</aside>

### HTTP Request

`POST /projects`

### Body Parameters

Parameter | Description | Required  | Type
--------- | ----------- |-----------|-----------
name | The name you want for your project | true | string
google_service_token | The json account file to authorize Cognation to create buckets| true | string
aws_rekognition_token | The AWS secrets with permissions for Rekogntion | false | string
google_vision_token | The Google Vision API key | false | string


# Requests

## Concept


## Create a Request

```shell
curl -POST "http://cognation.io/api/projects/<project-ID>/requests?token=<project-token>" \
  -H "Authorization: <your-api-key>" \
  -d '{
        "data": "https://storage.googleapis.com/cognation-testing-images/obama-macron.jpg",
        "data_type": "url",
        "services": ["AWS", "Google"],
        "feature": "LabelsDetection"
      }'
```

> The above command returns JSON structured like this:

```json
{
  "AWS": {
    "Labels": [
      {
                "Confidence": 99.29360961914062,
                "Name": "Human"
      }
    ]
  },
  "Google": {
    "labelAnnotations": [
    ]
  }
}
```

This endpoint creates a request.
<aside class="notice">The retrieved token should be safely stored, it will be used to authenticate your request on a project and there is no other way to get it</aside>

### HTTP Request

`POST /projects/<project-ID>/requests`


### Query Parameters

Parameter | Description | Required  
--------- | ----------- |-----------
token | The project related to the project you get after creating the project | true


### Body Parameters

Parameter | Description | Required  | Type
--------- | ----------- |-----------|-----------
data | The image you want to process. It could be a base64 encoded string or a url | true | string
data_type | This type of data you choose to send | true | enum(DataType)
services | List of all the AI services providers you want a response from | true | <string> array
feature | The process you want to get from the services | true | enum(ImageFeature)
