# Promo Codes

## Redeem a Promo

> Example

```curl
curl -X POST
  -H "Application-Name: super-fun-game" \
  -H "Authorization: Bearer ABC123" \
  -H "Content-Type: application/json" \
  -d '{ "promo_code": "super-fun-code" }' \
  https://api.derbygames.com/api/redeemed_promos
```

`POST /redeemed_promos`

Parameter | Required? | Description
--------- | --------- | -----------
promo_code | yes | promo to redeem

### Returns

> Success

A slim `User` object with an array of `Account` obejcts with updated balances and a slim `Promo` object with the amount of the promo.

```json
{
  "user": {
    "accounts": [
      {"type": "virtual", "balance": 2083136.67}
    ]
  },
  "promo": {"code":"name-here","amount":1000000.0}
}
```

Array of error messages if it failed.

> Failure

```json
{
  "errors": ["Promo has already been taken"]
}
```
