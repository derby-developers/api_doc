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

# Application and User Authentication

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

## Live Video

Genereates a URL to stream the live video.

`GET /races/<ID>/video`

<aside class="notice">Requires a bearer token</aside>

### Parameters
Parameter | Required? | Description
--------- | --------- | -----------
format | yes | 'flash' OR 'rtsp'

# Horses

## Specific Horse

`GET /horses/<ID>`

## Favorite a Horse

`POST /horses/<ID>/favorites`

<aside class="notice">Requires a bearer token</aside>

## Unfavorite a Horse

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

`GET /tracks`

## Live Video

`GET /tracks/<ID>/video`

<aside class="notice">Requires a bearer token</aside>

### Parameters
Parameter | Required? | Description
--------- | --------- | -----------
format | yes | 'flash' OR 'rtsp'

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