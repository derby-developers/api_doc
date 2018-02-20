# InstantRacing: Slot Play Games

## Slot Play Game Object

```json
{
  "id": 123,
  "position": 1,
  "unlocks_at_level": 10,
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
      [{"value":25,"weight":5},
       {"value":50,"weight":6},
       {"value":75,"weight":10},
       {"value":100,"weight":10},
       {"value":125,"weight":10},
       {"value":150,"weight":10},
       {"value":175,"weight":5},
       {"value":200,"weight":5},
       {"value":225,"weight":3},
       {"value":250,"weight":3},
       {"value":300,"weight":2},
       {"value":500,"weight":1},
       {"value":1000,"weight":1}]
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
position | the position of the slot game tile in the list
unlocks_at_level | the level at which the slot game unlocks
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
