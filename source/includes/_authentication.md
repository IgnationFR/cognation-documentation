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
