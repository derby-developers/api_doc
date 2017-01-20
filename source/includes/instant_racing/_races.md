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
payouts | array of Payout objects (only shown after the race is decided)

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
name | the horse's name (only shown after the race is decided)
final_position | the horse's final position (only shown after the race is decided)

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
