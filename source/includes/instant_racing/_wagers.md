# Instant Racing: Wagers

## Wager Object

```json
{
  "id": 1,
  "user_id": 1,
  "race_id": "755d855c-31af-412e-989e-8a63492683bf",
  "amount": 10,
  "payoff_amount": null,
  "pool": "win",
  "box": null,
  "bonus_multiplier": 1,
  "runners": [
    {
      "number": 3,
      "color": "Bay",
      "odds": "favorite",
      "badges": [
        "favorite"
      ],
      "trophies": 0,
      "speed_rating": null,
      "pedigree_rating": 0,
      "jockey_rating": null,
      "win_multiplier": 1,
      "place_multiplier": 2,
      "show_multiplier": 1.3,
      "position": 0
    }
  ],
  "game_name": "win-place-show",
  "user": {
    "id": 1,
    "screen_name": "Joe S.",
    "image_url": "https://derbycdn.net/towelie.jpg",
    "practice_balance": 10,
    "instant_racing_wager_count": 1,
    "accounts": [
      {
        "type": "virtual",
        "balance": 10
      }
    ],
    "player_statuses": [
      {
        "id": 1,
        "application_group": "casino",
        "level": 1,
        "current_level_points": 0,
        "progress": 0,
        "max_bet_amount": 200,
        "earned_bonuses": [],
        "locks": []
      }
    ]
  }
}
```

Field | Description
----- | -----------
id | wager id
user_id | user id
race_id | race id
amount | wager amount
payoff_amount | amount the wager paid out (shown when the race has been decided)
pool | the pool ("win", "exacta", "trifecta", "superfecta", "win_place", "win_place_show")
game_name | the game that created this wager ("super-slots", "win-place-show", "triple-threat", "exotic-pro")
box | boolean; true if runners can came in any order, false if they must come in exact order
bonus_multiplier | the payout multiplier being applied to the wager
runners | an array of Runner objects
user | a User object


## Get Wagers on a Race

`GET /instant_racing/races/<RACE_ID>/wagers`

<aside class="notice">
Because the wager payoffs are calculated asynchronously after a call to `decide`, it may take a few seconds until payoff_amount is available.
</aside>

### Returns

An array of `Wager` objects.

## New Wager

`POST /instant_racing/wagers`

> Win Example

```curl
curl -H "Application-Name: super-fun-game" \
  -H "Authorization: Bearer ABC123" \
  -H "Content-Type: application/json" \
  -d '{"amount": 10, "game_name": "exotic-pro", "pool": "win", "race_id": "46860996-e83d-4ef8-bcd2-8486ed440dea", "runners": [{"number": 3}] }' \
  https://api.derbygames.com/api/instant_racing/wagers
```

> Win/Place Example

```curl
curl -H "Application-Name: super-fun-game" \
  -H "Authorization: Bearer ABC123" \
  -H "Content-Type: application/json" \
  -d '{"amount": 10, "game_name": "exotic-pro", "pool": "win_place", "race_id": "46860996-e83d-4ef8-bcd2-8486ed440dea", "runners": [{"number": 3}] }' \
  https://api.derbygames.com/api/instant_racing/wagers
```

> Win/Place/Show Example

```curl
curl -H "Application-Name: super-fun-game" \
  -H "Authorization: Bearer ABC123" \
  -H "Content-Type: application/json" \
  -d '{"amount": 10, "game_name": "win-place-show", "pool": "win_place_show", "race_id": "46860996-e83d-4ef8-bcd2-8486ed440dea", "runners": [{"number": 3}] }' \
  https://api.derbygames.com/api/instant_racing/wagers
```

> Exacta Example

```curl
curl -H "Application-Name: super-fun-game" \
  -H "Authorization: Bearer ABC123" \
  -H "Content-Type: application/json" \
  -d '{"amount": 10, "game_name": "exotic-pro", "pool": "exacta", "race_id": "46860996-e83d-4ef8-bcd2-8486ed440dea", "runners": [{"number": 3},{"number":5}] }' \
  https://api.derbygames.com/api/instant_racing/wagers
```

> Trifeca Example

```curl
curl -H "Application-Name: super-fun-game" \
  -H "Authorization: Bearer ABC123" \
  -H "Content-Type: application/json" \
  -d '{"amount": 10, "game_name": "exotic-pro", "pool": "trifecta", "race_id": "46860996-e83d-4ef8-bcd2-8486ed440dea", "runners": [{"number": 3},{"number":5},{"number":2}] }' \
  https://api.derbygames.com/api/instant_racing/wagers
```

> Superfecta Example

```curl
curl -H "Application-Name: super-fun-game" \
  -H "Authorization: Bearer ABC123" \
  -H "Content-Type: application/json" \
  -d '{"amount": 10, "game_name": "exotic-pro", "pool": "trifecta", "race_id": "46860996-e83d-4ef8-bcd2-8486ed440dea", "runners": [{"number": 3},{"number":5},{"number":2},{"number":1}] }' \
  https://api.derbygames.com/api/instant_racing/wagers
```

Parameter | Required? | Description
--------- | --------- | -----------
race_id | yes | the race id
pool | yes | the pool ("win", "exacta", "trifecta", "superfecta", "win_place", "win_place_show")
game_name | yes | the game ("super-slots", "win-place-show", "triple-threat", "exotic-pro")
amount | yes | the wager amount
runners | yes | an array of objects indicating runner numbers ex: [{number: 2}, {number: 7}]

### Returns

A `Wager` object.
