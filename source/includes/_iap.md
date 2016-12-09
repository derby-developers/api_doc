## IAP Receipt Validation

After a sucessful in-app purchase, to add the credits into the user's account, the IAP receipt must be validated.

`POST /virtual_currency_purchase_receipts`

Parameter | Required? | Description
--------- | --------- | -----------
service | yes | 'google' or 'apple'
receipt | yes | receipt blob

[This endpoint is not yet live and subject to change]
