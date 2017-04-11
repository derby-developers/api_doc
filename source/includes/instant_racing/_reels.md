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
  ],
  "reel_type": "base"
  "game_name": "trifecta-gold"
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

`GET /instant_racing/reels?game_name=trifecta-gold`

Parameter | Required? | Description
--------- | --------- | -----------
game_name | yes | the name of the game for which reels are required (currently either `trifecta-gold` or `wild-mustang`)

### Returns

An array of `Reel` objects.

