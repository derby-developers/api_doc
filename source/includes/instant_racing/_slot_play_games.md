# InstantRacing: Slot Play Games

## Slot Play Game Object

```json
{
  "id": 123,
  "name": "unicorn-slots",
  "paylines":
    [[0, 0, 0, 0, 0],
    [1, 1, 1, 1, 1],
    [2, 2, 2, 2, 2],
    [3, 3, 3, 3, 3]],
  "multipliers": 
    [{"symbol": "F", "count": 5, "multiplier": 1},
     {"symbol": "E", "count": 5, "multiplier": 1},
     {"symbol": "D", "count": 5, "multiplier": 1},
     {"symbol": "C", "count": 5, "multiplier": 1},
     {"symbol": "A", "count": 5, "multiplier": 0.75},
     {"symbol": "K", "count": 5, "multiplier": 0.75},
     {"symbol": "Q", "count": 5, "multiplier": 0.75},
     {"symbol": "J", "count": 5, "multiplier": 0.75},
     {"symbol": "T", "count": 5, "multiplier": 0.75},
     {"symbol": "F", "count": 4, "multiplier": 0.25},
     {"symbol": "E", "count": 4, "multiplier": 0.25},
     {"symbol": "D", "count": 4, "multiplier": 0.25},
     {"symbol": "C", "count": 4, "multiplier": 0.25},
     {"symbol": "A", "count": 4, "multiplier": 0.15},
     {"symbol": "K", "count": 4, "multiplier": 0.15},
     {"symbol": "Q", "count": 4, "multiplier": 0.15},
     {"symbol": "J", "count": 4, "multiplier": 0.15},
     {"symbol": "T", "count": 4, "multiplier": 0.15},
     {"symbol": "F", "count": 3, "multiplier": 0.2},
     {"symbol": "E", "count": 3, "multiplier": 0.2},
     {"symbol": "D", "count": 3, "multiplier": 0.1},
     {"symbol": "C", "count": 3, "multiplier": 0.1},
     {"symbol": "A", "count": 3, "multiplier": 0.05},
     {"symbol": "K", "count": 3, "multiplier": 0.05},
     {"symbol": "Q", "count": 3, "multiplier": 0.05},
     {"symbol": "J", "count": 3, "multiplier": 0.05},
     {"symbol": "T", "count": 3, "multiplier": 0.05}],
  "wild_multipliers": 
    [{"symbol": "W", "count": 5, "multiplier": 5},
     {"symbol": "W", "count": 4, "multiplier": 1},
     {"symbol": "W", "count": 3, "multiplier": 0.2}],
  "bonus_multipliers": 
    [{"symbol": "S", "count": 5, "multiplier": 0, "free_spin_count": 0, "bonus_game": true},
     {"symbol": "S", "count": 4, "multiplier": 0, "free_spin_count": 0, "bonus_game": true},
     {"symbol": "S", "count": 3, "multiplier": 0, "free_spin_count": 0, "bonus_game": true}],
  "symbols": ["S", "T", "J", "Q", "K", "A", "C", "D", "E", "F", "W"],
  "wild_symbols": ["W"],
  "bonus_symbols": ["S"],
  "free_spin_multiplier": 2.0,
  "reel_count": 5,
  "requires_consecutive_symbols": true,
  "sticky_wilds": true,
  "bonus_game_rules": 
    {"symbols": 
      ["M",
       "M",
       "M",
       "S",
       "S",
       "S",
       "C",
       "C",
       "C",
       "C",
       "C",
       "C",
       "C",
       "C",
       "C",
       "C"],
   "multiplier_symbol": "M",
   "free_spin_symbol": "S",
   "coin_symbol": "C",
   "free_spin_count": 10,
   "multipliers": [1, 2, 3],
   "coin_values_and_weights": 
    {"25": 5,
     "50": 6,
     "75": 10,
     "100": 10,
     "125": 10,
     "150": 10,
     "175": 5,
     "200": 5,
     "225": 3,
     "250": 3,
     "300": 2,
     "500": 1,
     "1000": 1}
  },
  "sticky_wild_free_spin_count": 3,
  "reel_row_count": 4,
  "jackpot_symbols": [],
  "jackpot_multipliers": {}
}
```

Field | Description
----- | -----------
id | the id of the slot play game
name | the name of the game
paylines | a list of the paylines for the game
multipliers | the multpliers given for a symbol and count of matching symbols
wild_multipliers | the multipliers given for matches of only wild symbols
bonus_multipliers | the reward for getting a given number of scatter wild symbols
symbols | a list of the symbols used on the reels
wild_symbols | a list of the wild symbols
bonus_symbols | a list of bonus symbols
free_spin_multiplier | a static multiplier added to spins in the free spin mode
reel_count | the number of reels
requires_consecutive_symbols | true if the game requires that symbols much start in the leftmost reel in order to be counted as winning
sticky_wilds | true if the game supports sticky wilds
bonus_game_rules | the rules of the bonus game
sticky_wild_free_spin_count | the number of free spins awarded when the full stacked wild appears in the leftmost reel
reel_row_count | the number of rows in the slot machine,
jackpot_symbols | the symbols for jackpots
jackpot_multipliers | (deprecated, ignore)
