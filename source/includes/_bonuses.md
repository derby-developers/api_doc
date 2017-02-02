# Bonuses

## Check if a Bonus is Available

> Example

```curl
curl -H "Application-Name: super-fun-game" \
  -H "Authorization: Bearer ABC123" \
  -H "Content-Type: application/json" \
  https://api.derbygames.com/api/awarded_bonuses?bonus_name=racechamp_mobile_app_refill
```

`GET /api/awarded_bonuses?bonus_name=racechamp_mobile_app_refill`

### Returns

An array of `AwardedBonus` Objects OR an empty array. If no awarded bonuses are returned, then the requested bonus *is* available

## AwardedBonus Object

```json
{
  "id": 1585353,
  "amount": 20000,
  "created_at":"2016-11-28T12:19:17.395-08:00",
  "next_available_at":"2016-11-28T15:19:17.395-08:00",
  "bonus": {
    "name": "racechamp_mobile_app_refill",
    "award_interval_minutes": 180
  },
  "user": {
    "accounts": [
      {"type": "virtual", "balance": 2083136.67}
    ]
  }
}
```

Field | Description
----- | -----------
id | unique ID of this awarded bonus
amount | amount awarded
created_at | time when claimed
next_available_at | time when the next bonus is available (null if not)
bonus | Bonus Object (name and how often if can be claimed)
user | slim version of a User Object, with only an Account array

## Award a Bonus

> Example

```curl
curl -H "Application-Name: super-fun-game" \
  -H "Authorization: Bearer ABC123" \
  -H "Content-Type: application/json" \
  -d '{ "bonus_name": "racechamp_mobile_app_refill" }' \
  https://api.derbygames.com/api/awarded_bonuses
```

`POST /awarded_bonuses`

Parameter | Required? | Description
--------- | --------- | -----------
name | yes | name of the bonus to award

### Returns

An `AwardedBonus` object.
