# Virtual Currency Packages

## VirtualCurrencyPackage Object

```json
  { "id":1,"price":4.99,"virtual_currency_value":240000.0}
```

Field | Description
----- | -----------
id | package id
price | purchase price
virtual_currency_value | number of credits

## Get Packages

> Example

```curl
curl -H "Application-Name: super-fun-game" \
  -H "Authorization: Bearer ABC123" \
  https://api.derbygames.com/api/virtual_currency_packages
```

`GET /virtual_currency_packages`

Authentication is not required, but recommended.

Parameter | Required? | Description
--------- | --------- | -----------
promo_code | no | a promo code to show promotional pricing

### Returns

An array of `VirtualCurrencyPackage` obejcts.
