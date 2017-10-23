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
    [3, 3, 3, 3, 3]]
  "multipliers": 
    {["F", 5]: 1,
     ["E", 5]: 1,
     ["D", 5]: 1,
     ["C", 5]: 1,
     ["A", 5]: 0.75,
     ["K", 5]: 0.75,
     ["Q", 5]: 0.75,
     ["J", 5]: 0.75,
     ["T", 5]: 0.75,
     ["F", 4]: 0.25,
     ["E", 4]: 0.25,
     ["D", 4]: 0.25,
     ["C", 4]: 0.25,
     ["A", 4]: 0.15,
     ["K", 4]: 0.15,
     ["Q", 4]: 0.15,
     ["J", 4]: 0.15,
     ["T", 4]: 0.15,
     ["F", 3]: 0.2,
     ["E", 3]: 0.2,
     ["D", 3]: 0.1,
     ["C", 3]: 0.1,
     ["A", 3]: 0.05,
     ["K", 3]: 0.05,
     ["Q", 3]: 0.05,
     ["J", 3]: 0.05,
     ["T", 3]: 0.05},
  "wild_multipliers": 
    {["W", "W", "W", "W", "W"]: 5,
     ["W", "W", "W", "W"]: 1,
     ["W", "W", "W"]: 0.2},
  "bonus_multipliers": 
    {5: {"multiplier": 0, "free_spin_count": 0, "bonus_game": true},
     4: {"multiplier": 0, "free_spin_count": 0, "bonus_game": true},
     3: {"multiplier": 0, "free_spin_count": 0, "bonus_game": true}},
  "symbols": ["S", "T", "J", "Q", "K", "A", "C", "D", "E", "F", "W"],
  "wild_symbols": ["W"],
  "free_spin_multiplier": #<BigDecimal:7fa65dcdc818,'0.2E1',9(18)>,
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
    {25: 5,
     50: 6,
     75: 10,
     100: 10,
     125: 10,
     150: 10,
     175: 5,
     200: 5,
     225: 3,
     250: 3,
     300: 2,
     500: 1,
     1000: 1}
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
free_spin_multiplier | a static multiplier added to spins in the free spin mode
reel_count | the number of reels
requires_consecutive_symbols | true if the game requires that symbols much start in the leftmost reel in order to be counted as winning
sticky_wilds | true if the game supports sticky wilds
bonus_game_rules | the rules of the bonus game
sticky_wild_free_spin_count | the number of free spins awarded when the full stacked wild appears in the leftmost reel
reel_row_count | the number of rows in the slot machine,
jackpot_symbols | the symbols for jackpots
jackpot_multipliers | (deprecated, ignore)