---
title: DerbyGames API V1

language_tabs:
  - curl

includes:
  - errors

search: false
---

# Introduction

Oh hai.

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

## Endpoints

Sandbox API

`https://sandbox-api.derbygames.com/api/`

<!-- Sandbox Stream

`https://sandbox-stream.derbygames.com/chat` -->

Production API

`https://api.derbygames.com/api/`

# Users

## User Object

Any field not listed in the example should not be used.

> Example User Response

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
  "wager_count":1576,
  "multi_race_wager_count":81,
  "instant_racing_wager_count":0,
  "triple_threat_spin_count":0,
  "image_url": "https://avatars.derbycdn.net/1b/ef5a60ad7811e59098a34b698f19df.jpg",
  "phone_number":"12125551212",
  "mobile_phone_number":"12125551212",
  "accounts":[
    {"type":"virtual","balance":0.5,"available_balance":null}
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

Account Object

Field | Description
------| -----------
type | type of the account (virtual, rmg, etc.)
balance | current balance
available_balance | ?


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

Coming soon.

### Returns

A user object.

## Update User

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

# User Authentication

User auth is performed using OAuth 2.

Any request consuming user specific data requires a bearer token. Both access and refresh tokens are used. You must get a new access token once it has expired (you will receive a 401). If you The token needs to be added to the header of each request:

`Authorization: Bearer f95f9cf38e829104949ae6e160957f549abab252336c3b1007a5961fda940a09`

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

A token object on success, or an error message.

> Success

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

> Failure

```json
{ 
  "error": "Invalid email or password",
  "error_description": "The authorization server encountered an unexpected condition which prevented it from fulfilling the request."
}
```



# User Account Balances

Users current balance.

`GET /balance`


# User Saved Credit Cards

All credit cards this user has saved.

`GET /credit_cards`

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

`GET /notifications`

> Example

```curl
curl --header "Authorization: Bearer ABC123" \
  https://api.derbygames.com/api/notifications
```

### Returns

Array of Notification objects.

## Mark Message as Read

`PUT /notifications/:id/read`

> Example

```curl
curl -X PUT --header "Authorization: Bearer ABC123" \
  https://api.derbygames.com/api/notifications/1/read
```

Marks a message as read.

# Player Profiles

## Profile Object

Field | Description
------| -----------
screen_name | users name
image_url | fully qualified URL of their avatar
city |
state | 
bio |
joined_at | date the user registered
player_status | highest level reached per group, see below
stats | metrics, see below

```json
{
  "screen_name": "Wally T. Dog",
  "image_url":"https://avatars.derbycdn.net/1b/ef5a60ad7811e59098a34b698f19df.jpg",
  "city": "New York", 
  "state":"NY",
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

`GET /profiles/:id`

## Update Profile

`PUT /profile`


bio only right now?

Remove Avatar

`DELETE /profile/avatar`


# Instant Racing

## Races

View a race

`GET /instant_racing/races/:uuid`

Current Users Wagers on a Race

`GET /instant_racing/races/:uuid/wagers`

Video

`GET /instant_racing/races/:uuid/video`

## Wagers

`POST /instant_racing/wagers`

`POST /instant_racing/triple_threat_spins`

`POST /instant_racing/super_slot_spins`


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