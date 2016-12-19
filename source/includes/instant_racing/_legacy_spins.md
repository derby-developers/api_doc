

## Spin Object

```json
{
  "race_id": "46860996-e83d-4ef8-bcd2-8486ed440dea",
  "wagers": [
    {
      "id": 1,
      "user_id": 1,
      "race_id": "46860996-e83d-4ef8-bcd2-8486ed440dea",
      "amount": 2,
      "payoff_amount": null,
      "pool": "trifecta",
      "box": null,
      "bonus_multiplier": 1,
      "runners": [
        {
          "number": 5,
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
        },
        {
          "number": 4,
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
          "position": 1
        },
        {
          "number": 1,
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
          "position": 2
        }
      ],
      "game_name": "triple-threat",
      "user": {
        "id": 1,
        "screen_name": "Joe S.",
        "image_url": "https://derbycdn.net/towelie.jpg",
        "practice_balance": 16,
        "instant_racing_wager_count": 2,
        "accounts": [
          {
            "type": "derby",
            "balance": 100,
            "available_balance": 100
          },
          {
            "type": "virtual",
            "balance": 16,
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
            "earned_bonuses": [],
            "locks": [],
            "max_bet_amount": 200
          }
        ]
      }
    },
    {
      "id": 2,
      "user_id": 1,
      "race_id": "46860996-e83d-4ef8-bcd2-8486ed440dea",
      "amount": 2,
      "payoff_amount": null,
      "pool": "trifecta",
      "box": null,
      "bonus_multiplier": 1,
      "runners": [
        {
          "number": 2,
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
        },
        {
          "number": 5,
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
          "position": 1
        },
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
          "position": 2
        }
      ],
      "game_name": "triple-threat",
      "user": {
        "id": 1,
        "screen_name": "Joe S.",
        "image_url": "https://derbycdn.net/towelie.jpg",
        "practice_balance": 16,
        "instant_racing_wager_count": 2,
        "accounts": [
          {
            "type": "derby",
            "balance": 100,
            "available_balance": 100
          },
          {
            "type": "virtual",
            "balance": 16,
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
            "earned_bonuses": [],
            "locks": [],
            "max_bet_amount": 200
          }
        ]
      }
    }
  ],
  "user": {
    "triple_threat_spin_count": 1,
    "instant_racing_wager_count": 2,
    "player_statuses": [
      {
        "id": 1,
        "application_group": "casino",
        "level": 1,
        "current_level_points": 0,
        "progress": 0,
        "earned_bonuses": [],
        "locks": [],
        "max_bet_amount": 200
      }
    ]
  }
}
```

Field | Description
----- | -----------
race_id | race id
wagers | an array of Wager objects
user | a User object


## New Triple Threat Spin

`POST /instant_racing/triple_threat_spins`

> Example

```curl
curl -H "Application-Name: super-fun-game" \
  -H "Authorization: Bearer ABC123" \
  -H "Content-Type: application/json" \
  -d '{"amount": 10, "race_id": "46860996-e83d-4ef8-bcd2-8486ed440dea", "count": 2}' \
  https://api.derbygames.com/api/instant_racing/triple_threat_spins
```

Parameter | Required? | Description
--------- | --------- | -----------
race_id | yes | the race id
amount | yes | the wager amount
count | yes | the number of wagers to include in this spin

### Returns

A `Spin` object.

## New Super Slot Spin

`POST /instant_racing/super_slot_spins`

> Example

```curl
curl -H "Application-Name: super-fun-game" \
  -H "Authorization: Bearer ABC123" \
  -H "Content-Type: application/json" \
  -d '{"amount": 10, "race_id": "46860996-e83d-4ef8-bcd2-8486ed440dea"}' \
  https://api.derbygames.com/api/instant_racing/super_slot_spins
```

Parameter | Required? | Description
--------- | --------- | -----------
race_id | yes | the race id
amount | yes | the wager amount

### Returns

A `Spin` object.
