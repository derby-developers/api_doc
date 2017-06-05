# Virtual Currency Packages

## VirtualCurrencyPackage Object

```json
  {
  	"id": 1,
  	"price": 4.99,
  	"virtual_currency_value": 240000.0,
    "original_price": 4.99,
  	"original_virtual_currency_value": 240000.0,
  	"app_store_id": "virtual_currency_package_4.99"
  }
```

Field | Description
----- | -----------
id | package id
price | purchase price
virtual_currency_value | number of credits
original_price | original price (can be null)
original_virtual_currency_value | original currency value  (can be null)
app_store_id | ID for in-app-purchasing, applies to all app stores

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

## Virtual Currency Offers ('Hot Offers')

Special, per-user offers, that are based on user behavior.

### VirtualCurrencyOffer Object

```json
[
  {
    "id": 6505,
    "expires_at": "2017-06-01T09:52:58-07:00",
    "virtual_currency_package":
      {
        "id": 15,
        "price": 2.99,
        "virtual_currency_value": 250000.0,
        "original_price": null,
        "original_virtual_currency_value": null,
        "name": "purchase-offer-1",
        "app_store_id": "virtual_currency_package_2.99"
      }
    }
]
```

Field | Description
----- | -----------
id | offer id
expires_at | expiration time when offer expires
virtual_currency_package | `VirtualCurrencyPackage` object

### Get Offers

> Example

```curl
curl -H "Application-Name: super-fun-game" \
  -H "Authorization: Bearer ABC123" \
  https://api.derbygames.com/api/virtual_currency_offers
```

`GET /virtual_currency_offers`

### Returns

An array of `VirtualCurrencyOffer` objects.

## IAP Receipt Validation

After a sucessful in-app purchase, the IAP receipt must be validated in order to place the tokens into the users account.

> Example

```curl
curl -X POST
  -H "Application-Name: super-fun-game" \
  -H "Authorization: Bearer ABC123" \
  -H "Content-Type: application/json" \
  -d '{ "payment": { "transaction_type": "in_app", "service": "apple", receipt: "" } }' \
  https://api.derbygames.com/api/virtual_currency_purchases
```

`POST /in_app_purchases`

Paramater | Required? | Description
--------- | --------- | -----------
payment | yes | a Payment object

### Payment Object

Paramater | Required? | Description
------| --------- | -----------
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
