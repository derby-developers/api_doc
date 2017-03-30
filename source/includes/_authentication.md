# User Authentication

User auth is performed using OAuth 2.

Any request consuming user specific data requires a bearer token. Both access and refresh tokens are used. You must get a new access token once it has expired (you will receive a 401). The token needs to be added to the header of each request:

`Authorization: Bearer f95f9cf38e829104949ae6e160957f549abab252336c3b1007a5961fda940a09`

## Token Object

```json
{
  "access_token": "c07f8370d9f659fdee0dfea45af6f8b2fe37e4c5d77cf292d990a96ea403ca10",
  "token_type": "bearer",
  "expires_in": 604800,
  "refresh_token": "f95f9cf38e829104949ae6e160957f549abab252336c3b1007a5961fda940a09",
  "scope": "user",
  "created_at": 1478276432
}
```

Field | Description
------| -----------
access_token | token that is included in the Authorization header
token_type | 'bearer'
expires_in | time until expiration, in seconds
refresh_token | refresh token to get a new access token once expires_in is 0
scope | 'user'

## Generating a New Token

`POST /api/oauth/tokens`

### Via Email/Password

> email/password Example

```curl
curl -H "Application-Name: super-fun-game" \
  -H "Content-Type: application/json" \
  -d '{ "grant_type": "password", "email": "user@domain.com", "password": "123456" }' \
  https://api.derbygames.com/api/oauth/token
```

Parameter | Required? | Description
--------- | --------- | -----------
grant_type | yes | 'password'
email | yes | email address of the user
password | yes | password of the user


### Guest Access (using device ID)

> Guest Access Example

```curl
curl -H "Application-Name: super-fun-game" \
  -H "Content-Type: application/json" \
  -d '{ "grant_type": "guest", "device_id": "random123" }' \
  https://api.derbygames.com/api/oauth/token
```

Parameter | Required? | Description
--------- | --------- | -----------
grant_type | yes | 'guest'
device_id | yes | GUID of the device/installation

This will create a user account for the device if the ID is not found.

### Via Refresh Token

Once the access token has expired, get a new one using the refresh token.

> Token Refresh Example

```curl
curl -H "Application-Name: super-fun-game" \
  -H "Content-Type: application/json" \
  -d '{ "grant_type": "refresh_token", "refresh_token": "f95f9cf38e829104949ae6e160957f549abab252336c3b1007a5961fda940a09" }' \
  https://api.derbygames.com/api/oauth/token
```

Parameter | Required? | Description
--------- | --------- | -----------
grant_type | yes | 'refresh_token'
refresh_token | yes | the refresh token

### With Client Credentials

> API ID/secret example (this is the method needed for uploading race video positions)

```curl
curl -H "Application-Name: super-fun-game" \
  -H "Content-Type: application/json" \
  -d '{ "grant_type": "client_credentials", "client_id": "bab252336c3b1007a5961fda940a09", "client_secret": "90a049adf1695a7001b3c633252bab", "scope": "import_instant_racing_race_video_positions" }' \
  https://api.derbygames.com/api/oauth/token
```

### Using a Facebook Token

> Assertion Grant Example

```curl
curl -H "Application-Name: super-fun-game" \
  -H "Content-Type: application/json" \
  -d '{ "grant_type": "assertion", "assertion": "ABC123" }' \
  https://api.derbygames.com/api/oauth/token
```

If the user has linked their Facebook account, you can login using their Facebook token with an assertion grant.

Parameter | Required? | Description
--------- | --------- | -----------
grant_type | yes | 'assertion'
assertion | yes | Facebook token

### Returns

A `Token` object if successful, or an error message (with HTTP status 401) if not.

> Failure Example

```json
{
  "error": "Invalid email or password",
  "error_description": "The authorization server encountered an unexpected condition which prevented it from fulfilling the request."
}
```

## Token Information

`GET /api/oauth/token/info`

### Returns

A `Token` object.

## Revoking a Token (Logging Out)

> Example

```curl
curl -X POST \
  -H "Application-Name: super-fun-game" \
  -H "Authorization: Bearer ABC123" \
  https://api.derbygames.com/api/oauth/revoke
```
The token specified in the authorization header will be revoked.

### Returns

```json
{ }
```

With a 200 status code
