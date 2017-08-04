## Text

```shell
curl -POST "http://cognation.io/api/projects/<project-ID>/process/text?token=<project-token>" \
  -H "Authorization: <your-api-key>" \
  -d '{
        "data": "Benoit is a smart guy",
        "data_type": "text",
        "services": ["Aylien", "IBM"],
        "features": ["EntitesDetection", "SentimentAnalysis"]
      }'
```

> The above command returns JSON structured like this:

```json
{

}
```

### HTTP Request

`POST /projects/<project-ID>/process/text`


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
features | List of all the process you want to get from the services | true | [[enum(TextFeature)](#features)]
