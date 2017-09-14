# Bonuses

## Available Bonuses

> Example

```curl
curl -H "Application-Name: super-fun-game" \
  -H "Authorization: Bearer ABC123" \
  -H "Content-Type: application/json" \
  https://api.derbygames.com/api/available_bonuses
```

`GET /api/available_bonuses`

```json
[
  {
    "name":"default",
    "display_name":"Welcome Bonus",
    "tiers":[ 
      {"minimum":75.0,"match_rate":0.67}, {"minimum":50.0,"match_rate":0.2}, {"minimum":100.0,"match_rate":0.25},{"minimum":250.0,"match_rate":0.4}, {"minimum":500.0,"match_rate":0.5}
    ]
  },
  {
    "name":"racechamp_mobile_app_visits",
    "display_name":null,
    "amount":2500.0,
    "base_amount":500,
    "day":6,
    "multiplier":5,
    "days":[ 
      {"day":6,"multiplier":5}, {"day":7,"multiplier":5}, {"day":8,"multiplier":5}, {"day":9,"multiplier":5}, {"day":10,"multiplier":5}
    ]
  },
  {
    "name": "racechamp_mobile_app_refill",
    "display_name": "",
    "amount": null,
    "next_available_at":"2017-06-18T15:19:17.395-08:00",
    "current_time": "2017-06-18T16:19:17.395-08:00",
    "payment_methods": []
  },
  {
    "name": "racechamp3_daily_race_bonus",
    "display_name": "",
    "amount": null
  }
]
```

Field | Description
----- | -----------
name | internal name of the bonus, used when redeeming
display_name | human fiendly name
amount | amount of the bonus (null = amount is not yet known and will be shown when redeemed)
next_available_at | time when the next bonus is available, if applicable
current_time | current system time (used with next_avaiabe_at for a countdown)

List of available bonuses for this user. Bonus properies returned will differ based on the bonus type.

The `next_available_at` and `current_time` fields will show up if the bonus will be available in the future, but currently is not available.

### Returns

An array of `AwardedBonus` objects or an empty array.

## Bonus History

> Example

```curl
curl -H "Application-Name: super-fun-game" \
  -H "Authorization: Bearer ABC123" \
  -H "Content-Type: application/json" \
  https://api.derbygames.com/api/awarded_bonuses?bonus_name=racechamp_mobile_app_refill
```

`GET /api/awarded_bonuses?bonus_name=racechamp_mobile_app_refill`

### Returns

An array of `AwardedBonus` objects that have been awarded to this user, or an empty array.

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
bonus_name | yes | name of the bonus to award

### Returns

An `AwardedBonus` object.
