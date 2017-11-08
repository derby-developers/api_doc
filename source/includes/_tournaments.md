# Tournaments

## Tournament Object

```json
  {
    "id": 2,
    "prize_pool": 10000.0,
    "starts_at": "2017-11-08T09:36:46-08:00",
    "ends_at": "2017-11-08T09:41:46-08:00",
    "players": [{
      "screen_name": "Jimbo",
      "image_url": "https://example.com/giphy.gif",
      "script": {
        "duration": 300,
        "interval": 5,
        "scores": 
           [0.0, 0.0, 0.0, 0.0, 0.0, 1000.0, 1000.0, 1000.0, 2000.0]
      }
    }]
  }
```

Field | Description
--------- | -----------
id | the id of the tournament
prize_pool | the total prize pool for the tournament
starts_at | the time the tournament starts
ends_at | the time the tournament ends
players | the other players in the tournament

## Get Current Tournament

`GET /tournaments/current`

### Returns

a `Tournament` Object


<aside class="notice">
  This endpoint will always return a tournament. if a tournament is currently running for a given user, it will return that one, otherwise it will create and return a tournment that is starting now
</aside>
