# Projects


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

This endpoint create a new project.
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

## Get a Specific Project

```shell
curl "http://cognation.io/api/projects/<project-ID>"
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
