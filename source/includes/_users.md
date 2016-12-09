# Users

## User Object

```json
{
  "id":32118,
  "email":"gambler@derby.com",
  "created_at":"2013-04-04T11:21:03.439-07:00",
  "screen_name":"Wally The Dog",
  "authentication_token":"3434fUYT5zTBzJBUxygx",
  "first_name":"Wally",
  "last_name":"Dog",
  "birth_date":"1976-06-18",
  "address_1":"902 Broadway",
  "address_2":null,
  "state_code":"NY",
  "city":"New York",
  "state_code":"NY",
  "country_code":"US",
  "postal_code":"10011",
  "instant_racing_wager_count":0,
  "triple_threat_spin_count":0,
  "image_url": "https://avatars.derbycdn.net/1b/ef5a60ad7811e59098a34b698f19df.jpg",
  "phone_number":"12125551212",
  "mobile_phone_number":"12125551212",
  "accounts":[
    { "type":"virtual","balance":0.5 }
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
```

Field | Description
------| -----------
id | user id
email | email address, can be blank
screen_name | name to be shown to other users
authentication_token | token for authentication to chat ONLY
first_name |
last_name |
birth_date | format: YYYY-MM-DD
address_1 | main address line
address_2 | apartment info
state_code | 2 letter state/province code
city | name of city
country_code | 2 letter ISO country code
postal_code | postal/zip code
wager_count | total number of real money wagers
multi_race_wager_count | total number of multi race wagers placed
instant_racing_wager_count | total instant (virtual) racing wagers placed
triple_threat_spin_count | total number of TT spins
image_url | full URL of the users avatar
phone_number | phone number
mobile_phone_number | mobile phone
accounts | array of Account objects (real money gaming, virtual, etc.)
player_statuses | array of PlayerStatus objects, each one corresponding to a group of applications

## PlayerStatus Object

```json
{
  "id": 1,
  "application_group": "casino",
  "level": 1,
  "current_level_points": 0,
  "progress": 0,
  "earned_bonuses": [],
  "locks": ["exotic-pro", "super-slots"],
  "max_bet_amount": 200
}
```

Field | Description
------| -----------
id |
application_group | application group name
level | numeric level, starting at 1
progress | progress towards the next level, represented as a number between 0 and 1
current_level_points | points earned at this level
earned_bonuses | array of bonus names that are available due to leveling up
locks | an array of strings indicating locked games, ex. ["exotic-pro", "super-slots", "double-down", "jackpot", "red-zone", "place", "show"]
max_bet_amount | a suggested max bet amount

<aside class="notice">
Users will periodically gain enough points to level-up. When this happens, check the earned_bonuses array for any unlocked level-up bonuses. To award any bonuses, post to the /api/awarded_bonuses endpoint, setting bonus_name to a string in the earned_bonuses array.
</aside>

<aside class="notice">
Leveling-up can also change the locks array. Game names will be removed from this array as they become unlocked to the user.
</aside>

## Create User

> Examples

`POST /users`

### Using an Email and Password

```curl
curl -H "Application-Name: super-fun-game" \
  -H "Content-Type: application/json" \
  -d '{ "email": "hi@example.com&password=123456" }' \
  https://api.derbygames.com/api/users
```

Parameter | Required? | Description
--------- | --------- | -----------
email | yes | email address
password | yes | password
inviter_id | no | ID of who invited this user


### Using an Installation/Device ID

See 'Guest Access' under 'Generating a New Token'.

### Returns

A `User` object.

## Update User

```curl
curl -X PUT \
  -H "Application-Name: super-fun-game" \
  -H "Content-Type: application/json" \
  -d '{"first_name": "Larry" }' \
  https://api.derbygames.com/api/users
```

Add additional information to user, such as address, etc.

`PUT /users`

The follow fields are updatable.

Field | Notes
----- | -----
first_name |
last_name |
birth_date | format: YYYY-MM-DD
address_1 |
address_2 |
postal_code | format validated based on country code
city | only if you are overriding the postal code
state_code | only if you are overriding the postal code)
country_code |

### Returns

A `User` object.

## Get User

> Examples

`GET /user`

### Returns

A `User` object of the user specified in the Authentication header. Otherwise, a 401 will be returned.
