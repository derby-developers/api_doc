# Instant Racing: Slot Plays


## Slot Play Object

```json
{
  "id": 123,
  "user": {
    "id": 1,
    "screen_name": "Joe S.",
    "image_url": "https://derbycdn.net/towelie.jpg",
    "accounts": [
      {
        "type": "virtual",
        "balance": 30,
        "available_balance": null
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
  },
  "race": {
    "id": "55e41a9b-f592-4543-9d6c-6cb1ef98e5b9",
    "tasks": [
      {
        "id": 1,
        "completed": true,
        "required_slot_play_count": 3,
        "slot_play_count": 1,
        "current_points": 10,
        "current_units": 1.75
      }
    ]
  },
  "game_name": "trifecta-gold",
  "amount": 10,
  "slot_amount": 5,
  "wager_amount": 5,
  "slot_payoff_amount": 100,
  "wagers": [
    {
      "id": 1,
      "user_id": 1,
      "race_id": "55e41a9b-f592-4543-9d6c-6cb1ef98e5b9",
      "amount": 5,
      "payoff_amount": null,
      "pool": "trifecta",
      "box": null,
      "bonus_multiplier": 1,
      "runners": [
        {
          "number": 1,
          "color": "Bay",
          "odds": "1/9",
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
          "win_probability": 0.81,
          "position": 0
        },
        {
          "number": 2,
          "color": "Bay",
          "odds": "1/9",
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
          "win_probability": 0.81,
          "position": 1
        },
        {
          "number": 5,
          "color": "Bay",
          "odds": "1/9",
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
          "win_probability": 0.81,
          "position": 2
        }
      ],
      "game_name": "trifecta-gold"
    }
  ],
  "spins": [
    {
      "reel_results": [
        {
          "number": 0,
          "reel_id": 1,
          "stop_index": 0
        },
        {
          "number": 1,
          "reel_id": 2,
          "stop_index": 5
        },
        {
          "number": 2,
          "reel_id": 3,
          "stop_index": 2
        }
      ],
      "payline_results": [
        {
          "number": 2,
          "multiplier": 5,
          "payoff_amount": 25
        },
        {
          "number": 5,
          "multiplier": 5,
          "payoff_amount": 25
        }
      ],
      "bonus_game": {
        "payoff_amount": 1000,
        "symbols": ["M", 25, 50, "S", "M", 25, "S", "S"],
        "free_spins": true,
        "multiplier": 2
      }
    },
    {
      "reels": [
        {
          "number": 0,
          "reel_id": 4,
          "stop_index": 4
        },
        {
          "number": 1,
          "reel_id": 5,
          "stop_index": 3
        },
        {
          "number": 2,
          "reel_id": 6,
          "stop_index": 5
        }
      ],
      "paylines": [
        {
          "number": 3,
          "multiplier": 10,
          "payoff_amount": 50
        }
      ]
    }
  ]
}
```

Field | Description
----- | -----------
id | slot play id
race | a race object
amount | total slot play amount
slot_amount | amount placed towards the slot portion of the game
wager_amount | amount placed towards the trifecta wager portion of the game
slot_payoff_amount | the amount won by slot portion of the game
wagers | an array of wagers placed as part of this slot play
spins | an array of spin objects indicating what happened to the reels


## Spin Object

```json
{
  "reel_results": [
    {
      "number": 0,
      "reel_id": 1,
      "stop_index": 0
    },
    {
      "number": 1,
      "reel_id": 2,
      "stop_index": 5
    },
    {
      "number": 1,
      "reel_id": 3,
      "stop_index": 3
    },
  ],
  "payline_results": [
    {
      "number": 3,
      "multiplier": 5,
      "payoff_amount": 10
    }
  ],
  "bonus_game": {
    "payoff_amount": 1000,
    "symbols": ["M", 25, 50, "S", "M", 25, "S", "S"],
    "free_spins": true,
    "multiplier": 2
  }
}
```

Field | Description
----- | -----------
reel_results | a collection of reel_result objects
payline_results | a collection of payline_result objects
bonus_game | the attributes of a bonus game if one is awarded

<aside class="notice">
For slot games that include a bonus game, all "user selected" options are predetermined and served up in the "symbols" node of the bonus game.

The symbol "M" indicates a multiplier token is awarded and the "S" symbol indicates a free spin token is awarded.

Coin awards are represented as simply the value of the coins awarded.

It is not possible for a bonus game to have both a "free_spins" node and a "multiplier" node, both are included in the example above simply to show what they look like.
</aside>

## ReelResult Object

```json
{
  "number": 0,
  "reel_id": 1,
  "stop_index": 0
}
```

Field | Description
----- | -----------
number | the reel number (0-2)
reel_id | the id of the set of reel symbols that was used
stop_index | the index at which the reel stopped after spinning


## PaylineResult Object

```json
{
  "number": 3,
  "multiplier": 5,
  "payoff_amount": 10
}
```

Field | Description
----- | -----------
number | the payline number
multiplier | the multiplier awarded from this payline
payoff_amount | the total amount won from this payline


## New Slot Play

`POST /instant_racing/slot_plays`

> Slot Play Example

```curl
curl -H "Application-Name: super-fun-game" \
  -H "Authorization: Bearer ABC123" \
  -H "Content-Type: application/json" \
  -d '{"race_id": "55e41a9b-f592-4543-9d6c-6cb1ef98e5b9",
  "game_name": "trifecta-gold", amount: 10}' \
  https://api.derbygames.com/api/instant_racing/slot_plays
```


Parameter | Required? | Description
--------- | --------- | -----------
race_id | yes | the race id
game_name | yes | the game ("trifecta-gold", "wild-mustang", "unicorn-slots", "jackpot-slots", "saratoga-fortune", "broadway-lights", "triple-diamond")
amount | yes | the slot play amount

### Returns

A `Slot Play` object.
