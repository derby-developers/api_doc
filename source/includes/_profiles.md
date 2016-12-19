# Player Profiles

## Profile Object

```json
{
  "screen_name": "Wally T. Dog",
  "image_url":"https://avatars.derbycdn.net/1b/ef5a60ad7811e59098a34b698f19df.jpg",
  "city": "New York",
  "state_code":"NY",
  "country_code": "US",
  "bio": "games are fun" ,
  "joined_at": "2013-04-04T11:21:03-07:00",
  "player_statuses": [
    {"application_group":"instant_racing","level":5}
  ],
  "stats":{
    "jackpot": [],
    "instant_racing": [
      {"key":"wager_count","description":"Wager Count","value":16},
      {"key":"biggest_win_amount","description":"Biggest Win Amount","value":3600.0},
      {"key":"races_played","description":"Races Played","value":4},
      {"key":"favorite_game","description":"Favorite Game","value":"triple-threat"}
    ],
    "casino": []
  }
}
```

Field | Description
------| -----------
screen_name | users name
image_url | fully qualified URL of their avatar
city | city
state | 2 letter code of the state/province
country_code | 2 letter code of the country
bio | text blob about the user
joined_at | date the user registered
player_statuses | array of slim PlayerStatus objects with application_group/level
stats | metrics, see below

`stats` and `player_statues` are split into groups:

Group Name | Description
-----------| -----------
jackpot | real money gaming
instant_racing | virtual instant racing games
casino | virtual casino games

### `stats`

jackpot

key | description
--- | -----------
public_vip_score | integer of users VIP level
favorite_count | number of horses favorited
comment_count | number of comments on horses
wager_count | total wagers placed
biggest_win_amount | largest payout
biggest_win_date | date of the above win
instant_racing

key | description
--- | -----------
wager_count | number of wagers placed
biggest_win_amount | largest win
races_played | races that user bet on
favorite|game | game name of most used game

casino

key | description
--- | -----------
N/A |

## Get Profile

> Get Example

```curl
curl -H "Application-Name: super-fun-game" \
  https://api.derbygames.com/api/profiles/32118
```

`GET /profiles/<USER_ID>`

### Returns

A `Profile` object.

## Update Profile

> Update Example

```curl
curl -X PUT \
  -H "Application-Name: super-fun-game" \
  -H "Authorization: Bearer ABC123" \
  -H "Content-Type: application/json" \
  -d '{ "bio": "blahblahblah" }' \
  https://api.derbygames.com/api/profile
```

`PUT /profile`

Updatable fields

Field |
------|
bio |

### Returns

A `Profile` object.

## Remove Avatar

> Avatar Removal Example

```curl
curl -X DELETE
  -H "Application-Name: super-fun-game" \
  -H "Authorization: Bearer ABC123" \
  https://api.derbygames.com/api/profile/avatar
```

`DELETE /profile/avatar`
