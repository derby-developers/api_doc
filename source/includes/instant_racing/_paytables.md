# Instant Racing: Paytables


## Paytable Object

```json
{
  "game_name": "trifeca-gold",
  "paylines": [
    {
      "symbols": ["S","S","S"],
      "multiplier": 200
    },
    {
      "symbols": ["F","F","F"],
      "multiplier": 100
    },
    {
      "symbols": ["E","E","E"],
      "multiplier": 100
    }
  ]
}
```


Field | Description
----- | -----------
game_name | the name of the game
paylines | array of symbols and their multipliers


## Get Paytables

> Example

```curl
curl -H "Application-Name: super-fun-game" \
  -H "Authorization: Bearer ABC123" \
  https://api.derbygames.com/api/instant_racing/paytables
```

`GET /instant_racing/paytables`

### Returns

An array of `Paytable` objects.
