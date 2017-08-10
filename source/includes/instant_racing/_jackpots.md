## Jackpot Object

`GET /instant_racing/slot_plays?game_name=jackpot-slots`


```json
[{
  "id": 1
  "multiplier_rate": 0.05,
  "multiplier": 100.123,
  "jackpot_wild_count": 8
}]
```

Field | Description
----- | -----------
id | jackpot id
multiplier | the multiplier of the jackpot
multiplier_rate| the rate per second the jackpot multiplier is increasing
jackpot_wild_count | the number of wilds required to hit the jackpot

### Returns

A list of jackpots for the specified game