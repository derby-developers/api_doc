# Instant Racing: Reels


## Reel Object

```json
{
  "id": 1,
  "symbols": [
    "female-jockey",
    "trophy-cup",
    "10",
    "queen",
    "ace",
    "king",
    "male-jockey",
    "saddle",
    "jack",
    "horseshoe"
  ]
}
```

Field | Description
----- | -----------
id | reel id
symbols | an array of the symbols shown in this reel


## Get Reels

> Example

```curl
curl -H "Application-Name: super-fun-game" \
  -H "Authorization: Bearer ABC123" \
  https://api.derbygames.com/api/instant_racing/reels
```

`GET /instant_racing/reels`

### Returns

An array of `Reel` objects.
