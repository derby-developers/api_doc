# Accounts

## Account Object

```json
{
  "type":"virtual",
  "balance":489200.0
}
```

Field | Description
------| -----------
type | type of the account (virtual, rmg, etc.)
balance | current balance

## Get Balances

> Get Accounts Example

```curl
curl -H "Application-Name: racechamp_mobile_app" \
-H "Authorization: Bearer ABC123" \
https://api.derbygames.com/api/accounts
```

`GET /accounts`

### Returns

An array of `Account` objects.
