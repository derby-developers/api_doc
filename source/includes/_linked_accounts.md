# Linked Accounts

You can link a user to an outside OAuth provider, such as Facebook. The user can then use this as their login.

<aside class="notice">Currently, only Facebook is supported.</aside>

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

A User object.
