# Virtual Currency Packages

## VirtualCurrencyPackage Object

```json
  { 
  	"id":1,
  	"price":4.99,
  	"virtual_currency_value":240000.0,
  	"app_store_id": "virtual_currency_package_4.99"
  }
```

Field | Description
----- | -----------
id | package id
price | purchase price
virtual_currency_value | number of credits
app_store_id | ID for in-app-purchasing, applies to both Apple and Google

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

An array of `VirtualCurrencyPackage` objects.

## IAP Receipt Validation

After a sucessful in-app purchase, the IAP receipt must be validated in order to place the tokens into the users account.

> Example

```curl
curl -X POST
  -H "Application-Name: super-fun-game" \
  -H "Authorization: Bearer ABC123" \
  -H "Content-Type: application/json" \
  -d '{ "virtual_currency_package_id": 1, "payment": { "transaction_type": "in_app", "service": "apple", receipt: "" } }' \
  https://api.derbygames.com/api/virtual_currency_purchases
```

`POST /virtual_currency_purchases`

Paramater | Required? | Description
--------- | --------- | -----------
virtual_currency_package_id | yes | id of the package
virtual_currency_offer_id | no | optional ID of an offer the user is claiming
payment | yes | a Payment object

### Payment Object

Paramater | Required? | Description
------| --------- | -----------
transaction_type | yes | 'in_app'
service | yes | 'google' or 'apple'
receipt | yes | receipt blob

### Returns

An object with the purchase information and a slim User object with new balances.

```json
{
  "payment_amount": 100.0,
  "virtual_currency_amount": 200.0,
  "user": {
    "accounts": [
      {"type": "virtual", "balance": 2083136.67}
    ]
  }
}
```
