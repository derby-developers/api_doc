# Level Rules

## Level Rule Object
```json
{ 
  "id": 69,
  "level": 1,
  "level_type": "experience",
  "locks": ["unicorn-slots", "triple-diamond", "jackpot-slots", "broadway-slots"],
  "points_for_next_level": 5000,
  "max_bet_amount": 1000.0,
  "periodic_bonus_amount": 10000.0,
  "level_up_bonus_amount": 750.0,
  "daily_bonus_amount": 10000.0
}
```
## Get Level Rules for an Application Group

`GET /levels/level_rules?application_group=racechamp3_mobile_app`

### Returns

An array of `LevelRule` objects.
