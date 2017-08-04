## Speech

```shell
curl -POST "http://cognation.io/api/projects/<project-ID>/process/speech?token=<project-token>" \
  -H "Authorization: <your-api-key>" \
  -d '{
        "data": "https://storage.googleapis.com/cloud-samples-tests/speech/brooklyn.flac",
        "data_type": "url",
        "services": [IBM"],
        "features": ["Transcription"],
        "language": "en-US"
      }'
```

> The above command returns JSON structured like this:

```json
{
  "Transcription" : {
    "IBM": {
       "results": [
          {
             "alternatives": [
                {
                   "confidence": 0.95,
                   "transcript": "how old is the Brooklyn Bridge "
                }
             ],
             "final": true
          }
       ],
       "result_index": 0
    }
  }
}
```

### HTTP Request

`POST /projects/<project-ID>/process/speech`


### Query Parameters

Parameter | Description | Required  
--------- | ----------- |-----------
token | The project related to the project you get after creating the project | true


### Body Parameters

Parameter | Description | Required  | Type
--------- | ----------- |-----------|-----------
data | The record you want to process| true | string
data_type | This type of data you choose to send | true | [enum(DataType)](#data-types)
services | List of all the AI services providers you want a response from | true | [[enum(Services)](#services)]
features | List of all the process you want to get from the services | true | [[enum(ImageFeature)](#features)]
language | The language of the record | true | [enum(Language)](#languages)
