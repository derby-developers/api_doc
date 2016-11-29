---
title: DerbyGames API V1

language_tabs:
  - curl

includes:
  - errors

search: false
---

# Introduction

For API access, please contact eric@derbygames.com. You will be issued a application name, client ID, and client secret.

# Interacting with the API

## Making Requests

All requests:

* must be over HTTPS
* must have an application name, either as a header 'Application-Name' or as a query string 'application_name'

Arguments can be passed as params, form data or JSON with correct `Content-Type` header.

## Localization

There is limited support for localization using the `Accept-Language` header. Currently, we allow:

* `en` - English (default)
* `es` - Spanish
* `pt` - Portuguese (Brazil)

Any non supported locale will default to English.

Numbers, currency and datetime don’t rely on localization so they will be returned in standard format.

## Versioning

This document applies to V1, which is the current live version. To maintain compatibility with this version, it is recommended you add an accepts header:

`Accept: version=1`

## Objects

Any field not explicitly listed should be avoided as it is subject to change.


## Endpoints

Sandbox API

`https://sandbox-api.derbygames.com/api/`

Production API

`https://api.derbygames.com/api/`

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
  "player_statues": [
    {
      "id":22,
      "current_level_points":0,
      "earned_level_up_bonus":false,
      "level":1,
      "level_up_bonus_amount":0,
      "lifetime_points":0,
      "locks":[],
      "max_bet_amount":200,
      "name":"casino",
      "progress":0
    }
  ]
}
```

Field | Description
------| -----------
id | user id
email | email address, can be blank
screen_name | name to be shown to other users
authentication_token | token for authentication to chat
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
player_statues | array of PlayerStatus objects, each one corresponding to a group of applications

## Account Object

Field | Description
------| -----------
type | type of the account (virtual, rmg, etc.)
balance | current balance

## PlayerStatus Object

Field | Description
------| -----------
id |
name | application group name
level |
current_level_points |
earned_level_up_bonus |
level_up_bonus_amount |
lifetime_points |
locks |
max_bet_amount |
progress |

## Create User

> Examples

`POST /users`

### Using an Email and Password

```curl
curl --header "Application-Name: super-fun-game" \
  --data "email=hi@example.com&password=123456" \
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

A user object.

## Update User

```curl
curl -X PUT \
  --header "Application-Name: super-fun-game" \
  --data "birth_date=2000-01-01" \
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

A user object.

## Get User

> Examples

`GET /user`

### Returns

A user object of the user specified in the Authentication header. Otherwise, a 401 will be returned.



# User Authentication

User auth is performed using OAuth 2.

Any request consuming user specific data requires a bearer token. Both access and refresh tokens are used. You must get a new access token once it has expired (you will receive a 401). If you The token needs to be added to the header of each request:

`Authorization: Bearer f95f9cf38e829104949ae6e160957f549abab252336c3b1007a5961fda940a09`

## Token Object

```json
{
  "access_token": "c07f8370d9f659fdee0dfea45af6f8b2fe37e4c5d77cf292d990a96ea403ca10",
  "token_type": "bearer",
  "expires_in": 604800,
  "refresh_token": "f95f9cf38e829104949ae6e160957f549abab252336c3b1007a5961fda940a09",
  "scope": "user",
  "created_at": 1478276432
}
```

Field | Description
------| -----------
access_token | token that is included in the Authorization header
token_type | 'bearer'
expires_in | time until expiration, in seconds
refresh_token | refresh token to get a new access token once expires_in is 0
scope | 'user'

## Generating a New Token

`POST /api/oauth/tokens`

### Via Email/Password

```curl
curl --header "Application-Name: super-fun-game" \
  --data "grant_type=password&email=user@domain.com&password=123456" \
  https://api.derbygames.com/api/oauth/token
```

Parameter | Required? | Description
--------- | --------- | -----------
grant_type | yes | 'password'
email | yes | email address of the user
password | yes | password of the user

### Token Exchange from Another OAuth Provider

Exchange another OAuth providers token for a DerbyGames token. Currently, only facebook is supported.

> Example

```curl
curl --header "Application-Name: super-fun-game" \
  --data "grant_type=assertion&assertion=FBTOKEN123456" \
  https://api.derbygames.com/api/oauth/token
```

Parameter | Required? | Description
--------- | --------- | -----------
grant_type | yes | 'assertion'
provider | yes | 'facebook'
assertion | yes | OAuth token from provider

### Guest Access (using device ID)

```curl
curl --header "Application-Name: super-fun-game" \
  --data "grant_type=guest&device_id" \
  https://api.derbygames.com/api/oauth/token
```

Parameter | Required? | Description
--------- | --------- | -----------
grant_type | yes | 'guest'
device_id | yes | GUID of the device/installation

This will create a user account for the device if the ID is not found.

### Via Refresh Token

Once the access token has expired, get a new one using the refresh token.

> Example

```curl
curl --header "Application-Name: super-fun-game" \
  --data "grant_type=refresh_token&refresh_token=f95f9cf38e829104949ae6e160957f549abab252336c3b1007a5961fda940a09" \
  https://api.derbygames.com/api/oauth/token
```

Parameter | Required? | Description
--------- | --------- | -----------
grant_type | yes | 'refresh_token'
refresh_token | yes | the refresh token

### Returns

A token object if successful, or an error message (with HTTP status 401) if not.

> Failure Example

```json
{
  "error": "Invalid email or password",
  "error_description": "The authorization server encountered an unexpected condition which prevented it from fulfilling the request."
}
```

## Token Information

`GET /api/oauth/token/info`

### Returns

A Token object.


# User Saved Credit Cards

All credit cards this user has saved.

## Get User's Saved Cards

`GET /credit_cards`

### Returns

A CreditCard object.

# User Notifications

## Notification Object

```json
[
  {
    "id": 1,
    "message": "Hello, player!",
    "thumbnail_image_url": null,
    "expires_at": "2016-11-03T00:00:00.000-07:00",
    "bonus": {},
    "read": false,
    "created_at": "2016-11-01T14:17:56.991-07:00",
    "expired": false,
    "claimed": true,
    "claimed_at":"2016-11-01T14:52:50.443-07:00"
  }
]

```

Field | Description
------| -----------
id |
message | text of the message
thumbnail_image_url | fully qualified thumbail URL, if provided
expires_at | expiration
bonus | Bonus Object, if applicable
read | boolean if message has been read
created_at | date of the message
expired | boolean if notification has expired
claimed | boolean if this is a bonus that has been claimed
claimed_at |

## Get Notifications

> Example

```curl
curl --header "Application-Name: super-fun-game" \
  --header "Authorization: Bearer ABC123" \
  https://api.derbygames.com/api/notifications
```

`GET /notifications`

### Returns

Array of Notification objects.

## Mark Message as Read

> Example

```curl
curl -X PUT \
  --header "Application-Name: super-fun-game" \
  --header "Authorization: Bearer ABC123" \
  https://api.derbygames.com/api/notifications/1/read
```

`PUT /notifications/:id/read`

Marks a message as read.

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
    {"name":"instant_racing","level":5}
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
player_statuses | array of slim PlayerStatus objects with name/level
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

> Example

```curl
curl --header "Application-Name: super-fun-game" \
  https://api.derbygames.com/api/profiles/32118
```

`GET /profiles/:id`

### Returns

A Profile object.

## Update Profile

> Example

```curl
curl -X PUT \
  --header "Application-Name: super-fun-game" \
  --header "Authorization: Bearer ABC123" \
  --data "bio=blahblahblah" \
  https://api.derbygames.com/api/profile
```

`PUT /profile`

Updatable fields

Field |
------|
bio |

### Returns

A Profile object.

## Remove Avatar

> Example

```curl
curl -X DELETE
  --header "Application-Name: super-fun-game" \
  --header "Authorization: Bearer ABC123" \
  https://api.derbygames.com/api/profile/avatar
```

`DELETE /profile/avatar`


# Leaderboards

## Leader Object

```json
  {
    "id": 248941,
    "score": 19200,
    "rank": 1,
    "screen_name": "Joe S.",
    "board": "daily",
    "image_url": "https://avatars.derbycdn.net/15/121b70929811e491181d7fc65910e6.jpg"
  }
```

Field | Description
--------- | -----------
id |
score | integer score, higher the better
rank | position in this board
screen_name | user chosen name
board | daily, weekly, or all_time
image_url | avatar of the user

## Get Leaders

`GET /leaders`

Parameter | Required? | Description
--------- | --------- | -----------
show | no | number of leaders to show (default: all)

### Returns

An array of Leaders.

## Leaders near the current user

`GET /headers/around_me`

### Returns

An array of Leaders.

# Promo Codes

## Redeem a Promo

> Example

```curl
curl -X POST
  --header "Application-Name: super-fun-game" \
  --header "Authorization: Bearer ABC123" \
  --data "promo_code=super-fun-code" \
  https://api.derbygames.com/api/redeemed_promos
```

`POST /redeemed_promos`

Parameter | Required? | Description
--------- | --------- | -----------
promo_code | yes | promo to redeem

### Returns

> Success

A slim User object with updated balances, and a slim Promo object with the amount that was added.

```json
{
  "user": {"practice_balance":2063136.67},
  "promo": {"code":"name-here","amount":1000000.0}
}
```

Array of error messages if it failed.

> Failure

```json
{
  "errors": ["Promo has already been taken"]
}
```

# Bonuses

## AwardedBonus Object

```json
{
  "id": 1585353,
  "amount": 20000,
  "claimed_at":"2016-11-28T12:19:17.395-08:00",
  "bonus": {
    "name": "instant_racing_refill",
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
claimed_at | time when claimed
bonus | Bonus Object (name and how often if can be claimed)
user | slim version of a User Object, with only an Account array

## Award a Bonus

> Example

```curl
curl --header "Application-Name: super-fun-game" \
  --header "Authorization: Bearer ABC123" \
  --data "bonus_name=instant_racing_refill" \
  https://api.derbygames.com/api/awarded_bonuses
```

`POST /awarded_bonuses`

Parameter | Required? | Description
--------- | --------- | -----------
name | yes | name of the bonus to award

### Returns

An AwardedBonus object.




# Virtual Currency Packages

## VirtualCurrencyPackage Object

```json
  { "id":1,"price":4.99,"virtual_currency_value":240000.0}
```

Field | Description
----- | -----------
id | package id
price | purchase price
virtual_currency_value | number of credits

## Get Packages

> Example

```curl
curl --header "Application-Name: super-fun-game" \
  --header "Authorization: Bearer ABC123" \
  https://api.derbygames.com/api/virtual_currency_packages
```

`GET /virtual_currency_packages`

Authentication is not required, but recommended.

Parameter | Required? | Description
--------- | --------- | -----------
promo_code | no | a promo code to show promotional pricing

### Returns

An array of VirtualCurrencyPackages.

## In-App Purchasing

## Receipt Validation

After a sucessful in-app purchase, to add the credits into the user's account, the IAP receipt must be validated.

`POST /virtual_currency_purchase_receipts`

Parameter | Required? | Description
--------- | --------- | -----------
service | yes | 'google' or 'apple'
(all others) | yes | different params depending on the service (TBD)

[This endpoint is not yet live and subject to change]

# Push Subscriptions

## Register a Device

`POST /push_subscriptions`

Parameter | Required? | Description
--------- | --------- | -----------
client_id | yes | unique device/client ID
token | yes | device token

### Returns

An empty response. 200 is successful, 422 if not.

# Instant Racing: Races

## Race Object

```json
{
  "id":"e1a0f337-f439-4eb6-849f-e3dc5b47b10d",
  "race_type": "Thoroughbred",
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
  ]
}
```

Field | Description
----- | -----------
id | unique race (per user)
race_type | Thoroughbred, Harness
decided_at | date this race was closed for wagering, null if still open
runners | array of Runner objects

## Runner Object

Field | Description
----- | -----------
badges | array of badges
jockey_rating | 0-100
number | position in field
odds | null until race is decided
pedigree_rating | 0-100
speed_rating | 0-100
place_multiplier |
show_multiplier |
win_multiplier |
trophies | total trophies received

Badges |
---------- |
top_trainer |



## Get a Race

Gets the current race for the user. The same race will be returned until the `decide` endpoint has been called.

> Example

```curl
curl --header "Application-Name: super-fun-game" \
  --header "Authorization: Bearer ABC123" \
  https://api.derbygames.com/api/instant_racing/races/current
```

`GET /instant_racing/races/current`

### Returns

A Race object.

## Decide a Race

Close the race for wagering. You can then request video and results.

`PUT /instant_racing/races/:id/decide`

# Instant Racing: Wagers

## Wager Object

```json
{

}
```

## Get Wagers on a Race

`GET /instant_racing/races/:id/wagers`

### Returns

An array of Wager objects.

## New Wager

`POST /instant_racing/wagers`

## New Triple Threat Spin

`POST /instant_racing/triple_threat_spins`

## New Super Slot Spin

`POST /instant_racing/super_slot_spins`


# Instant Racing: Video

## Video Object

```json
{
  "video_url":"https://instant-racing-video.derbycdn.net/2b/2b368e19-ad1a-44a7-835f-98790948707e/256.mp4",
  "video_duration_seconds":81
}
```

Field | Description
----- | -----------
video_url | URL of the video (link expires in 5 minutes)
video_duration_seconds | total length, in seconds

## Viewing Video

> Example

```curl
curl --header "Application-Name: super-fun-game" \
  --header "Authorization: Bearer ABC123" \
  https://api.derbygames.com/api/instant_racing/races/:id/video?quality=low
```

`GET /instant_racing/races/:id/video?quality=[low|high|hls]`

'low' and 'high' will be an MP4. HLS will return a m3u8 playlist.



# Real Money Gaming

Available to select partners.



# Chat & Realtime Data Stream

You can connect to our streaming servers for chat and realtime data. This method is recommended over polling other endpoints. Talk to the nerds for more information.

> Example Script

```html
<html>
  <script src="https://stream.derbyjackpot.com/chat.js"></script>
  <script src="https://ajax.googleapis.com/ajax/libs/jquery/2.0.3/jquery.min.js"></script>
  <script type="text/javascript">
    var client = new Faye.Client('https://stream.derbyjackpot.com/chat');

    auth_extension = {
      outgoing: function(message, callback) {
        // on every outgoing message, attach the auth token
        message['ext'] = {
          auth_token: "F7VwDj2iw089TJLcLrRO9C6Gz8uVgHUGMftCGGipbJvazZjXVh663UZTTf78Mav0QjKRxTWsgIN89PJNJ14A3IlWeAxMajdzd6iL"
        };
        return callback(message);
      }
    };

    client.addExtension(auth_extension);

    var subscription = client.subscribe('/feed/v1/touchtunes', function(message) {
      // handle message
      console.log(message);

      txt = '';
      if (message['type'] == 'wager') {
        user = message['user']['screen_name'] + "<img height=30 width=30 src='" + message['user']['image_url'] + "'>"
        txt = user + " just wagered " + message['amount'];
      }

      if (message['type' == 'win']) {
        txt = user + " won " + message['net_payoff_amount'];
      }

      if (message['type'] == 'race') {
        txt = "Race " + message['name'] + " " + message['race_number'] + " changed.";
      }

      $("#content").append("<div>" + txt + "</div>");
    });
  </script>

  <body>
    <div id="content"></div>
  </body>
</html>
```