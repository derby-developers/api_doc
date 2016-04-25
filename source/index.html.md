---
title: DerbyGames API Reference

language_tabs:
  - curl

includes:
  - errors

search: false
---

# Introduction

Welcome to the DerbyGames API. The API supports user verification, wagering, depositing, and race data. An application key is required for access. Please contact eric@derby.com for access.

This document applies to V1, which is the current live version. To maintain compatibility with this version, it is recommended you add an accepts header:

`Accept: version=1`

## URLs

Sandbox API

`https://sandbox.derbygames.com/api`

Sandbox Stream

`https://sandbox-stream.derbygames.com/chat`

# App & User Authentication

The Authorization header on a request identifies both the application and the user token that the request applies to. All requests always have a application token, and any request that acts on a user account must have a bearer token as well.

For example:

`Authorization: Application ABC123 Bearer USERTOKEN123`

<aside class="notice">
Application tokens will be issued by us. See below on how to get a bearer token for a user.
</aside>

# Bearer Tokens

## Generate a new token

> Create a new token

```curl
curl -v -H "Authorization: Application ABC123" --data "email=email&password=password&client_id=client_id" /api/tokens

```

> Header in the response

```text
Authorization: Bearer eyJpZCI6MiwidG9rZW4iOiI2T21vQzVOZXNlalwvUUhXbCtCU2JSVUxJMjBVZGZSc2sifQ==
```

> Failure:

```json
{ "error":"message here" }
```

Successfull response will have JSON representing a user in the body and the header will container the bearer token you should use.

### HTTP Request
`POST /tokens`

<aside class="warning">Tokens must be stored in a secure manner</aside>

### Parameters
Parameter | Required? | Description
--------- | --------- | -----------
email | yes | email address of the user
password | yes | password of the user
client_id | yes | unique ID of the users device



## Token Verification

> Verify the token

```curl
curl -v -H "Authorization: Application ABC123" /tokens/ABC123
```

### HTTP Request
`GET /tokens/<TOKEN>`

The response body will be empty. A 200 indicates the token exists and a 404 indicates it is invalid.




# Users

## Create a New User

`POST /users`

### Parameters
Parameter | Required? | Description
--------- | --------- | -----------
email | yes | email address of the user (it will be validated in realtime)
password | yes | password the user wants
inviter_id | no | ID of who invited this user

## Update a User

Add additional information to user, such as address, SSN, etc. This endpoint will return a 422 once a user has opened a wagering account.

`PUT /users`

<aside class="notice">Requires a bearer token</aside>

### Parameters
Parameter | Description
--------- | ---------
first_name | users first name
last_name | users last name
birth_date | birthdate YYYY-MM-DD
address_1 | address line 1
address_2 | address line 2
postal_code | postal code
city | city (only needed if you are overriding the postal code's)
state_code | 2 letter state/province code (only needed if you are overriding the postal code's)
country_code | 2 letter ISO country code
ssn | either the full 9 digit SSN, or last 4 (US only)
national_identifier | national ID number (Brazil only)

## Wagering Account

Once you have updated the user with all the required information you can open a wagering account, provided they reside in one of our legal areas.

`POST /user/account`




# Races

Racing centric data. Contains information about the race, posttime, runners, etc. If the race is final, it will also contain information about the winners.

## Current Race

This is the race that currently appears on the main DJ site.

### HTTP Request
`GET /races/current`

## Specific Race

### HTTP Request
`GET /races/<ID>`

## Previous Races

### HTTP Request
`GET /races`

## Race Win

Retreives a specific win for a race.

### HTTP Request
`GET /races/<ID>/wins/<WIN_ID>`

## Race Replay Video

Genereates a URL to replay the race. To get live video, use the track video endpoint.

`GET /races/<ID>/video`

<aside class="notice">Requires a bearer token</aside>

### Parameters
Parameter | Required? | Description
--------- | --------- | -----------
format | yes | 'flash' OR 'rtsp'

## User Specific Race Info

Returns which horses this user has favorited in this race and any previous horses this user has won on, with amounts.

### HTTP Request
`GET /races/<ID>/profile`

<aside class="notice">Requires a bearer token</aside>



# Player Profiles

Public information about a player.

### HTTP Request
`GET /players/<SCREEN_NAME>`




# Horses

## Specific Horse

### HTTP Request
`GET /horses/<ID>`

## Favorite a Horse

### HTTP Request
`POST /horses/<ID>/favorites`

<aside class="notice">Requires a bearer token</aside>

## Unfavorite a Horse

### HTTP Request
`DELETE /horses/<ID>/favorites`

<aside class="notice">Requires a bearer token</aside>



# Pools

## Today's Pools

A list of our chosen exoctic pools for the day (pick 4,5,6).

### HTTP Request
`GET /pools`

## Specific Pool

### HTTP Request
`GET /pools/<ID>`

## Wagered on by a User

### HTTP Request
`GET /pools/wagered`

<aside class="notice">Requires a bearer token</aside>

## Next Pool

The next available pool for lotto-style wagering.

### HTTP Request
`GET /pools/quick_play`


# Tracks

## Tracks with Races Today

### HTTP Request
`GET /tracks`

## Live Video

### HTTP Request
`GET /tracks/<ID>/video`

<aside class="notice">Requires a bearer token</aside>

### Parameters
Parameter | Required? | Description
--------- | --------- | -----------
format | yes | 'flash' OR 'rtsp'




# Wagers

## View Wagers

See all wagers this user has placed.

### HTTP Request
`GET /wagers`

<aside class="notice">Requires a bearer token</aside>

## Bet

Place a wager on a pool.

### HTTP Request
`POST /wagers`

<aside class="notice">Requires a bearer token</aside>

### Parameters
Parameter | Required? | Description
--------- | --------- | -----------
amount | yes | amount in decimal format (e.g., 2.00)
pool | yes | object containing the id of the pool to wager into
box | yes | true/false if this wager should be boxed
runners | yes | array of runners with a position and ID of the runner
jackpot | no | true/flase if this wager is for the progressive jackpot


## Winners

Get the latest large winning wagers.

### HTTP Request
`GET /wagers/big_winners`


# Notifications

## Inbox

All user notifications that this user has received.

### HTTP Request
`GET /notifications`

<aside class="notice">Requires a bearer token</aside>


# Balance

## Current Balance

Users current balance.

### HTTP Request
`GET /balance`

<aside class="notice">Requires a bearer token</aside>




# Deposits

## Saved Credit Cards

All credit cards this user has saved.

### HTTP Request
`GET /credit_cards`

<aside class="notice">Requires a bearer token</aside>

## Prefered Payment Methods

The prefered payment method for this user.

### HTTP Request
`GET /user_payment_method`

## Deposit

Deposit money into the users account. These params vary greatly depending on which payment methods are offered for your integration. They will be provided separatly.

### HTTP Request
`POST /deposits`

<aside class="notice">Requires a bearer token</aside>



# Withdrawals

## Withdrawal

Withdrawal to an account. These params vary greatly depending on which payment methods are offered for your integration. They will be provided separatly.

### HTTP Request
`POST /withdrawal`

<aside class="notice">Requires a bearer token</aside>




# Supporting Endpoints

## Location of the User

Returns the current location of the user and which provider services them.

### HTTP Request
`GET /locations`

### Parameters
Parameter | Required? | Description
--------- | --------- | -----------
latitude | no | gps latitude coordinate
longitude | no | gps longitude coordinate

## Postal Codes

Returns the city/state and which provider services them.

### HTTP Request
`GET /postal_codes/<2_LETTER_COUNTRY_CODE>/<POSTAL_CODE>`




# Chat & Realtime Data Stream

You can connect to our streaming servers for chat and realtime data. This method is recommended over polling other endpoints. In real time, you can receive race changes, wagers as they are placed, and winning wagers when they are paid.

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