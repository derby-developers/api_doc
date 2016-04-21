# Application and User Authentication

The Authorization header on a request identifies both the application and the user token that the request applies to. All requests always have a application token, and any request that acts on a user account must have a bearer token as well.

For example:

`Authorization: Application ABC123 Bearer USERTOKEN123`

<aside class="notice">
Application tokens will be issued by us. See below on how to get a bearer token for a user.
</aside>

# Bearer Tokens

## Generate a new token

> Create a new token

```curl
curl -v -H "Authorization: Application ABC123" --data "email=email&password=password&client_id=client_id" /api/tokens

```

> Header in the response

```text
Authorization: Bearer eyJpZCI6MiwidG9rZW4iOiI2T21vQzVOZXNlalwvUUhXbCtCU2JSVUxJMjBVZGZSc2sifQ==
```

> Failure:

```json
{ "error":"message here" }
```

Successfull response will have JSON representing a user in the body and the header will container the bearer token you should use.

### HTTP Request
`POST /api/tokens`

### Query Parameters
Parameter | Required? | Description
--------- | --------- | -----------
email | yes | email address of the user
password | yes | password of the user
client_id | yes | unique ID of the users device

<aside class="warning">
Keep those tokens safe!
</aside>


## Token Verification

> Verify the token

```curl
curl -v -H "Authorization: Application ABC123" /api/tokens/ABC123
```

### HTTP Request
`GET /api/tokens/<TOKEN>`

The response body will be empty. A 200 indicates the token exists and a 404 indicates it is invalid.

