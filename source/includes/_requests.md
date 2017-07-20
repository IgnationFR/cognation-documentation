# Requests

A request represents AI processing on data from multiple [services](#services).

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
  "Google": [
      {
        "mid": "/m/03gkb0",
        "description": "socialite",
        "score": 0.6829214
      }
    ]
}
```

### HTTP Request

`POST /projects/<project-ID>/requests`


### Query Parameters

Parameter | Description | Required  
--------- | ----------- |-----------
token | The project related to the project you get after creating the project | true


### Body Parameters

Parameter | Description | Required  | Type
--------- | ----------- |-----------|-----------
data | The image you want to process| true | string
data_type | This type of data you choose to send | true | [enum(DataType)](#data-types)
services | List of all the AI services providers you want a response from | true | [[enum(Services)](#services)]
feature | The process you want to get from the services | true | [enum(ImageFeature)](#services)
