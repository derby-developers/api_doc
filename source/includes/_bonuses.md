# Bonuses

## AwardedBonus Object

```json
{
  "id": 1585353,
  "amount": 20000,
  "claimed_at":"2016-11-28T12:19:17.395-08:00",
  "bonus": {
    "name": "instant_racing_refill",
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
claimed_at | time when claimed
bonus | Bonus Object (name and how often if can be claimed)
user | slim version of a User Object, with only an Account array

## Award a Bonus

> Example

```curl
curl -H "Application-Name: super-fun-game" \
  -H "Authorization: Bearer ABC123" \
  -H "Content-Type: application/json" \
  -d '{ "bonus_name": "instant_racing_refill" }' \
  https://api.derbygames.com/api/awarded_bonuses
```

`POST /awarded_bonuses`

Parameter | Required? | Description
--------- | --------- | -----------
name | yes | name of the bonus to award

### Returns

An `AwardedBonus` object.
