# Accounts

## Account Object

```json
{
  "type": "virtual",
  "balance": 489200.0,
  "updated_at": "2018-07-02T09:50:37-07:00"
}
```

Field | Description
------| -----------
type | type of the account (virtual, rmg, etc.)
balance | current balance
updated_at | the last time the balance was updated

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
