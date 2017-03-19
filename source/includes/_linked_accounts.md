# Linked Accounts

Link a user account to Facebook.

## Create a Linked Account

If the user is missing any profile data, it will be filled in as much as possible.

> Example

```curl
curl -H "Application-Name: super-fun-game" \
  -H "Authorization: Bearer ABC123" \
  -H "Content-Type: application/json" \
  -d '{ "provider": "facebook", "token": "facebookoauthtoken" }' \
  https://api.derbygames.com/api/linked_accounts
```

`POST /linked_accounts`

Parameter | Required? | Description
--------- | --------- | -----------
provider | yes | 'facebook'
token | yes | OAuth token for the provider. It will be validated.

### Returns

HTTP Code | reason | description | notes
--------- | ------ | ----------- | -----
200 | success | User object
422 | validation error | Error object | generally due to in invalid token
302 | account already linked | This Facebook account has been linked to a different user (see below)

### Handling an account that is already linked

If the Facebook account is already linked to another user, you should authenticate as that Facebook user using an OAuth assertion grant. The location header will contain the URL you need to use. The response will be a Token obect.

> Example

```curl
curl -H "Application-Name: super-fun-game" \
  [URL returned in the location header from above]
```



