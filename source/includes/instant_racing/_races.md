# Instant Racing: Races

## Race Object

```json
{
  "id":"e1a0f337-f439-4eb6-849f-e3dc5b47b10d",
  "race_type": "Thoroughbred",
  "group_id": 1,
  "runners": [
    {
      "badges": ["top_trainer"],
      "color": "Chestnut",
      "jockey_rating":61,
      "number":4,
      "odds": null,
      "pedigree_rating":52,
      "place_multiplier":4.6,
      "show_multiplier":1.3,
      "speed_rating":32,
      "trophies":6,
      "win_multiplier":11.6
    }
  ],
  "payouts": [
    {
      "wager_amount": 2,
      "payoff_amount": 6.8,
      "finish": "6",
      "pool": "win"
    },
    {
      "wager_amount": 2,
      "payoff_amount": 3.8,
      "finish": "6",
      "pool": "place"
    },
    {
      "wager_amount": 2,
      "payoff_amount": 6.2,
      "finish": "7",
      "pool": "place"
    },
    {
      "wager_amount": 2,
      "payoff_amount": 2.6,
      "finish": "6",
      "pool": "show"
    },
    {
      "wager_amount": 2,
      "payoff_amount": 3.2,
      "finish": "7",
      "pool": "show"
    },
    {
      "wager_amount": 2,
      "payoff_amount": 4.6,
      "finish": "2",
      "pool": "show"
    },
    {
      "wager_amount": 2,
      "payoff_amount": 30.2,
      "finish": "6/7",
      "pool": "exacta"
    },
    {
      "wager_amount": 0.1,
      "payoff_amount": 16.61,
      "finish": "6/7/2/5",
      "pool": "superfecta"
    },
    {
      "wager_amount": 0.5,
      "payoff_amount": 28.6,
      "finish": "6/7/2",
      "pool": "trifecta"
    }
  ],
  "tasks": [
    {
      "id": 1,
      "completed": false,
      "required_wager_count": 5,
      "wager_count": 2
    }
  ],
  "position_timings": [
    {
      "offset": 10,
      "positions": [1,2,3,4]
    }
  ]
}
```

Field | Description
----- | -----------
id | unique race (per user)
group_id | the race group id of the current race
race_type | Thoroughbred, Harness
decided | whether the race is decided (true or false)
runners | array of Runner objects
payouts | array of Payout objects [*]
position_timings | array of PositionTiming objects with the order of the runners at that moment [*]
tasks | array of Task objects

* = only shown after the race is decided

There will always be 1 payout for the win pool, 2 for the place pool, 3 for show, and 1 for each exotic pool.

## Runner Object

```json
{
  "badges": ["top_trainer"],
  "color": "Chestnut",
  "jockey_rating":61,
  "number":4,
  "odds": null,
  "pedigree_rating":52,
  "place_multiplier":4.6,
  "show_multiplier":1.3,
  "speed_rating":32,
  "trophies":6,
  "win_multiplier":11.6
}
```

Field | Description
----- | -----------
badges | array of badges
jockey_rating | 0-100
number | position in field
odds | null, 'long_shot' or 'favorite' until race is decided, then the runner's odds (e.g. 9/2)
pedigree_rating | 0-100
speed_rating | 0-100
color | the color of the horse, "Bay", "Gray", "Chestnut", "Dark Bay" or "Black"
win_multiplier | approximate multiple of wager paid out if horse finishes first
place_multiplier | approximate multiple of wager paid out if horse finishes second
show_multiplier | approximate multiple of wager paid out if horse finishes third
trophies | total trophies received
name | the horse's name [*]
final_position | the horse's final position [*]

* = only shown after the race is decided

Badges     | Description
---------- | -----------
top_trainer | horse's trainer has an exceptional record
top_jockey |  horse's jockey has an exceptional record
money_bags | horse's lifetime earnings are in the top 20%
extra_classy | horse's class rating is in the top 20%
first_timer | horse's first race
star_sire | horse's father has an exceptional record
star_dam | horse's mother has an exceptional record
streak_one | won its last race
streak_two |  won its last two races
streak_three | won its last three races
long_shot | horse has long odds (less likely to win)
favorite | horse has short odds (more likely to win)

## Payout Object

```json
{
  "wager_amount": 0.5,
  "payoff_amount": 28.6,
  "multiplier": 57,
  "finish": "6/7/2",
  "pool": "trifecta"
}
```

Field | Description
----- | -----------
wager_amount |
payoff_amount | the amount paid out for a wager of `wager_amount`
finish | the finish associated with a winning payout
pool | the type of wager being paid out (win, place, show, exacta, trifecta, superfecta)

## PositionTiming Object

```json
{
  "offset": 10,
  "positions": [1,2,3,4]
}
```

Field | Description
----- | -----------
offset | seconds in the video
positions | array of runner positions (an empty array for the final stretch)

## Task Object

An object describing a given task. With the exception of `id` and `completed`, each of the groups of json attributes in the example to the rigfht are mutually exclusive from each other.

In other words, a task with the `required_wager_count` and `wager_count` attributes will not have any of the other progress attributes

`wager` attributes refer to horse racing wagers

`slot_play`, `amount_won` and `amount_played` attributes refer to slot plays

> List of all possible attributes in a task object

```json
{
  "id": 1,
  "completed": true,

  "required_wager_count": 3,
  "wager_count": 3,

  "required_win_wager_count": 3,
  "win_wager_count": 3,

  "required_place_wager_count": 3,
  "place_wager_count": 3,

  "required_show_wager_count": 3,
  "show_wager_count": 3,

  "required_exacta_wager_count": 3,
  "exacta_wager_count": 3,

  "required_trifecta_wager_count": 3,
  "trifecta_wager_count": 3,

  "required_superfecta_wager_count": 3,
  "superfecta_wager_count": 3,

  "required_slot_play_count": 3,
  "slot_play_count": 3,

  "required_trifecta_slot_play_count": 3,
  "trifecta_slot_play_count": 3,

  "required_superfecta_slot_play_count": 3,
  "superfecta_slot_play_count": 3,

  "required_slot_play_win_count": 3,
  "slot_play_win_count": 3,

  "required_trifecta_slot_play_win_count": 3,
  "trifecta_slot_play_win_count": 3,

  "required_superfecta_slot_play_win_count": 3,
  "superfecta_slot_play_win_count": 3,

  "required_amount_played": 3,
  "amount_played": 3,

  "required_amount_won": 3,
  "amount_won": 3,

  "required_symbol": "ace",
  "required_symbol_count": 3,
  "symbol_count": 3
}
```

> Example of what a specific task object actually looks like

```json
{
  "id": 1,
  "completed": false,
  "required_wager_count": 5,
  "wager_count": 2
}
```

Field | Description
----- | -----------
id | the id of the task for this user
completed | a boolean indicating whether the task is completed
required_wager_count | the required count of horse wagers to complete the task
wager_count | the number of horse wagers currently placed towards the task
required_slot_play_count | the required count of slot plays to complete the task
slot_play_count | the number of slot plays currently played towards the task
required_slot_play_win_count | the required number of winning slot plays to complete the task
slot_play_win_count | the current number of slot play wins towards completing the task
required_amount_played | the required amount played on the slot machines to complete the task
amount_played | the current amount played towards completing the task
required_amount_won | the required amount won on the slot machines to complete the task
amount_won | the current amount won towards completing the task

The remaining attributes shown in the example all work the same way but are associated with specific wager and slot play types

## Get a Race

Gets the current race for the user. The same race will be returned until the `decide` endpoint has been called.

> Example (not group specific)

```curl
curl -H "Application-Name: super-fun-game" \
  -H "Authorization: Bearer ABC123" \
  https://api.derbygames.com/api/instant_racing/races/current
```

> Example (specific race group)

```curl
curl -H "Application-Name: super-fun-game" \
  -H "Authorization: Bearer ABC123" \
  https://api.derbygames.com/api/instant_racing/races/current?group_id=1
```

`GET /instant_racing/races/current`

Parameter | Required? | Description
--------- | --------- | -----------
group_id | no | only return a race from this group

### Returns

A `Race` object.

## Decide a Race

Close the race for wagering. You can then request video and results.

`PUT /instant_racing/races/<RACE_ID>/decide`
