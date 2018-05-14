# ADW: Races

## 1. Get the Current Race

One race at a time is specified as the current race.

A new current race is selected approximately 30 seconds before the race is scheduled to start, so make sure to use the id (as specified below) to keep track of the race that you currently have rendered onscreen


> Example

```curl
curl -H "Authorization: Bearer ABC123" \
  -H "Application-Name: racechamp_mobile_app" \
  https://api.derbygames.com/api/races/current
```

## 2. Poll the race that was acquired with the above endpoint

Once you have the currently selected race - you should poll that race by using the returned id from the current endpoint. This endpoint will always return the same race for a given id.

> Example

```curl
curl -H "Authorization: Bearer ABC123" \
  -H "Application-Name: racechamp_mobile_app" \
  https://api.derbygames.com/api/races/905096
```


> Example ADW Race Object

```
{
   "id":905096,
   "race_number":2,
   "action_message":null,
   "race_type":"Harness",
   "distance":1609.344,
   "distance_in_meters":"1609.344 m",
   "distance_in_yards":"1609 yds",
   "status":"Open",
   "not_yet_open":false,
   "finalized":false,
   "track_id":56,
   "name":"Harrington Raceway",
   "city":"Harrington",
   "state":"DE",
   "country":null,
   "country_code":"US",
   "equibase_id":"HAR",
   "video_enabled":true,
   "weather":"clear-day",
   "selected":true,
   "excluded":false,
   "score":8.0,
   "selected_at":"2018-05-14T14:15:42-07:00",
   "race_class":"N/A",
   "post_datetime":"2018-05-14T14:20:01-07:00",
   "runners":[
      {
         "id":6938036,
         "number":1,
         "scratched":false,
         "odds":"16/1",
         "final_position":null,
         "jockey":"Russell Foster",
         "trainer":"Arty Foster Jr",
         "owner":"Arty L Foster III,Cordova,MD;Wanda May Saulsbury,Cordova,MD",
         "multi_entry_flag":null,
         "horse":{
            "id":303315,
            "name":"I'll Call U Later",
            "horse_type":"Harness",
            "favorite_count":0,
            "description":null,
            "history":[
               {
                  "odds":"3/5",
                  "scratched":false,
                  "final_position":2,
                  "race_date":"2018-05-07"
               },
               {
                  "odds":"11/1",
                  "scratched":false,
                  "final_position":null,
                  "race_date":"2018-04-26"
               },
               {
                  "odds":"9/1",
                  "scratched":false,
                  "final_position":null,
                  "race_date":"2018-04-15"
               },
               {
                  "odds":"9/1",
                  "scratched":false,
                  "final_position":null,
                  "race_date":"2018-03-29"
               },
               {
                  "odds":"9/1",
                  "scratched":false,
                  "final_position":4,
                  "race_date":"2018-03-22"
               }
            ]
         }
      },
      {
         "id":6938038,
         "number":2,
         "scratched":false,
         "odds":"12/1",
         "final_position":null,
         "jockey":"Montrell Teague",
         "trainer":"Tim Crissman",
         "owner":"Crissman Inc,Dover,DE",
         "multi_entry_flag":null,
         "horse":{
            "id":13980,
            "name":"Fancy Colt",
            "horse_type":"Harness",
            "favorite_count":4,
            "description":null,
            "history":[
               {
                  "odds":"1/9",
                  "scratched":false,
                  "final_position":null,
                  "race_date":"2018-05-07"
               },
               {
                  "odds":"1/1",
                  "scratched":false,
                  "final_position":1,
                  "race_date":"2018-04-30"
               },
               {
                  "odds":"20/1",
                  "scratched":false,
                  "final_position":null,
                  "race_date":"2018-04-23"
               },
               {
                  "odds":"15/1",
                  "scratched":false,
                  "final_position":null,
                  "race_date":"2018-04-16"
               },
               {
                  "odds":"7/5",
                  "scratched":false,
                  "final_position":null,
                  "race_date":"2018-04-09"
               }
            ]
         }
      },
      {
         "id":6938039,
         "number":3,
         "scratched":false,
         "odds":"40/1",
         "final_position":null,
         "jockey":"Cody Poliseno",
         "trainer":"Carlo Poliseno",
         "owner":"Louis W Tomczak Jr,Dover,DE",
         "multi_entry_flag":null,
         "horse":{
            "id":383467,
            "name":"Proper One",
            "horse_type":"Harness",
            "favorite_count":1,
            "description":null,
            "history":[
               {
                  "odds":"3/1",
                  "scratched":false,
                  "final_position":1,
                  "race_date":"2018-05-07"
               },
               {
                  "odds":"50/1",
                  "scratched":false,
                  "final_position":null,
                  "race_date":"2018-04-29"
               },
               {
                  "odds":"90/1",
                  "scratched":false,
                  "final_position":null,
                  "race_date":"2018-04-16"
               },
               {
                  "odds":"30/1",
                  "scratched":false,
                  "final_position":null,
                  "race_date":"2018-04-09"
               },
               {
                  "odds":"1/1",
                  "scratched":false,
                  "final_position":2,
                  "race_date":"2018-03-29"
               }
            ]
         }
      },
      {
         "id":6938041,
         "number":4,
         "scratched":false,
         "odds":"8/5",
         "final_position":null,
         "jockey":"Anthony Morgan",
         "trainer":"Gary Ewing",
         "owner":"Gary E Ewing,Easton,MD",
         "multi_entry_flag":null,
         "horse":{
            "id":113843,
            "name":"Rangers Sureshot",
            "horse_type":"Harness",
            "favorite_count":2,
            "description":null,
            "history":[
               {
                  "odds":"25/1",
                  "scratched":false,
                  "final_position":null,
                  "race_date":"2018-05-07"
               },
               {
                  "odds":"5/2",
                  "scratched":false,
                  "final_position":4,
                  "race_date":"2018-04-23"
               },
               {
                  "odds":"2/1",
                  "scratched":false,
                  "final_position":4,
                  "race_date":"2018-04-16"
               },
               {
                  "odds":"1/5",
                  "scratched":false,
                  "final_position":1,
                  "race_date":"2018-04-09"
               },
               {
                  "odds":"2/1",
                  "scratched":false,
                  "final_position":3,
                  "race_date":"2018-03-26"
               }
            ]
         }
      },
      {
         "id":6938042,
         "number":5,
         "scratched":false,
         "odds":"8/5",
         "final_position":null,
         "jockey":"Mike Cole",
         "trainer":"Joseph Columbo",
         "owner":"George\u0026 Tina Dennis Racing,Wyoming,DE",
         "multi_entry_flag":null,
         "horse":{
            "id":290735,
            "name":"Safensound Hanover",
            "horse_type":"Harness",
            "favorite_count":0,
            "description":null,
            "history":[
               {
                  "odds":"1/1",
                  "scratched":false,
                  "final_position":1,
                  "race_date":"2018-05-07"
               },
               {
                  "odds":"30/1",
                  "scratched":false,
                  "final_position":null,
                  "race_date":"2018-04-26"
               },
               {
                  "odds":"13/1",
                  "scratched":false,
                  "final_position":null,
                  "race_date":"2018-04-19"
               },
               {
                  "odds":"35/1",
                  "scratched":false,
                  "final_position":4,
                  "race_date":"2018-04-07"
               },
               {
                  "odds":"7/2",
                  "scratched":false,
                  "final_position":3,
                  "race_date":"2018-03-29"
               }
            ]
         }
      },
      {
         "id":6938043,
         "number":6,
         "scratched":false,
         "odds":"2/1",
         "final_position":null,
         "jockey":"Victor Kirby",
         "trainer":"Wayne Givens",
         "owner":"Legacy Racing Of De Inc,Seaford,DE;Reginald A Hazzard II,Millsboro,DE",
         "multi_entry_flag":null,
         "horse":{
            "id":70554,
            "name":"Papa Ray",
            "horse_type":"Harness",
            "favorite_count":2,
            "description":null,
            "history":[
               {
                  "odds":"6/5",
                  "scratched":false,
                  "final_position":null,
                  "race_date":"2018-05-07"
               },
               {
                  "odds":"50/1",
                  "scratched":false,
                  "final_position":null,
                  "race_date":"2018-04-30"
               },
               {
                  "odds":"21/1",
                  "scratched":false,
                  "final_position":null,
                  "race_date":"2018-04-23"
               },
               {
                  "odds":"12/1",
                  "scratched":false,
                  "final_position":3,
                  "race_date":"2018-04-16"
               },
               {
                  "odds":"8/5",
                  "scratched":false,
                  "final_position":3,
                  "race_date":"2018-04-09"
               }
            ]
         }
      },
      {
         "id":6938044,
         "number":7,
         "scratched":false,
         "odds":"30/1",
         "final_position":null,
         "jockey":"Ross Wolfenden",
         "trainer":"Robert W Clark",
         "owner":"Kovach Stables LLC,Milford,DE",
         "multi_entry_flag":null,
         "horse":{
            "id":7033,
            "name":"Feel Like a Fool",
            "horse_type":"Harness",
            "favorite_count":4,
            "description":null,
            "history":[
               {
                  "odds":"2/1",
                  "scratched":false,
                  "final_position":null,
                  "race_date":"2018-05-02"
               },
               {
                  "odds":"1/2",
                  "scratched":false,
                  "final_position":1,
                  "race_date":"2018-04-18"
               },
               {
                  "odds":"4/5",
                  "scratched":false,
                  "final_position":1,
                  "race_date":"2018-04-11"
               },
               {
                  "odds":"17/1",
                  "scratched":false,
                  "final_position":null,
                  "race_date":"2018-03-26"
               },
               {
                  "odds":"3/1",
                  "scratched":false,
                  "final_position":null,
                  "race_date":"2018-03-19"
               }
            ]
         }
      },
      {
         "id":6938045,
         "number":8,
         "scratched":false,
         "odds":"50/1",
         "final_position":null,
         "jockey":"Jason Green",
         "trainer":"Frank Kryskowiak",
         "owner":"Frank C Kryskowiak,Felton,DE",
         "multi_entry_flag":null,
         "horse":{
            "id":5418,
            "name":"Bettoriffic",
            "horse_type":"Harness",
            "favorite_count":0,
            "description":null,
            "history":[
               {
                  "odds":"35/1",
                  "scratched":false,
                  "final_position":4,
                  "race_date":"2018-05-07"
               },
               {
                  "odds":"50/1",
                  "scratched":false,
                  "final_position":null,
                  "race_date":"2018-04-30"
               },
               {
                  "odds":"40/1",
                  "scratched":false,
                  "final_position":null,
                  "race_date":"2018-04-18"
               },
               {
                  "odds":"12/1",
                  "scratched":false,
                  "final_position":4,
                  "race_date":"2018-04-09"
               },
               {
                  "odds":"80/1",
                  "scratched":false,
                  "final_position":2,
                  "race_date":"2018-03-26"
               }
            ]
         }
      }
   ],
   "pools":[
      {
         "id":7205451,
         "track_name":"Harrington Raceway",
         "track_city":"Harrington",
         "track_state":"DE",
         "name":"superfecta",
         "multiplicity":1,
         "track_id":56,
         "description":null,
         "position_count":4,
         "featured":false,
         "wager_amount":0.0,
         "payoff_amount":0.0,
         "wager_payoff":0.0,
         "wager_minimum":0.1,
         "wager_minimums":[
            {
               "provider_name":"practice",
               "provider_id":5,
               "single_bet_minimum":1.0,
               "multiple_bet_minimum":1.0
            },
            {
               "provider_name":"derby",
               "provider_id":1,
               "single_bet_minimum":0.1,
               "multiple_bet_minimum":0.1
            },
            {
               "provider_name":"xpressbet",
               "provider_id":3,
               "single_bet_minimum":0.1,
               "multiple_bet_minimum":0.1
            }
         ],
         "expected_post_time":"2018-05-14T14:20:00-07:00",
         "size":4203.0,
         "multi_race":false,
         "races":[
            {
               "id":905096,
               "final":false,
               "race_number":2,
               "post_datetime":"2018-05-14T14:20:01-07:00",
               "live_wager_count":null,
               "live_user_count":null
            }
         ]
      },
      {
         "id":7205442,
         "track_name":"Harrington Raceway",
         "track_city":"Harrington",
         "track_state":"DE",
         "name":"trifecta",
         "multiplicity":1,
         "track_id":56,
         "description":null,
         "position_count":3,
         "featured":false,
         "wager_amount":0.0,
         "payoff_amount":0.0,
         "wager_payoff":0.0,
         "wager_minimum":1.0,
         "wager_minimums":[
            {
               "provider_name":"practice",
               "provider_id":5,
               "single_bet_minimum":5.0,
               "multiple_bet_minimum":5.0
            },
            {
               "provider_name":"derby",
               "provider_id":1,
               "single_bet_minimum":1.0,
               "multiple_bet_minimum":1.0
            },
            {
               "provider_name":"xpressbet",
               "provider_id":3,
               "single_bet_minimum":1.0,
               "multiple_bet_minimum":1.0
            }
         ],
         "expected_post_time":"2018-05-14T14:20:00-07:00",
         "size":7138.0,
         "multi_race":false,
         "races":[
            {
               "id":905096,
               "final":false,
               "race_number":2,
               "post_datetime":"2018-05-14T14:20:01-07:00",
               "live_wager_count":null,
               "live_user_count":null
            }
         ]
      },
      {
         "id":7205436,
         "track_name":"Harrington Raceway",
         "track_city":"Harrington",
         "track_state":"DE",
         "name":"exacta",
         "multiplicity":1,
         "track_id":56,
         "description":null,
         "position_count":2,
         "featured":false,
         "wager_amount":0.0,
         "payoff_amount":0.0,
         "wager_payoff":0.0,
         "wager_minimum":1.0,
         "wager_minimums":[
            {
               "provider_name":"practice",
               "provider_id":5,
               "single_bet_minimum":10.0,
               "multiple_bet_minimum":10.0
            },
            {
               "provider_name":"derby",
               "provider_id":1,
               "single_bet_minimum":1.0,
               "multiple_bet_minimum":1.0
            },
            {
               "provider_name":"xpressbet",
               "provider_id":3,
               "single_bet_minimum":1.0,
               "multiple_bet_minimum":1.0
            }
         ],
         "expected_post_time":"2018-05-14T14:20:00-07:00",
         "size":6540.0,
         "multi_race":false,
         "races":[
            {
               "id":905096,
               "final":false,
               "race_number":2,
               "post_datetime":"2018-05-14T14:20:01-07:00",
               "live_wager_count":null,
               "live_user_count":null
            }
         ]
      },
      {
         "id":7205411,
         "track_name":"Harrington Raceway",
         "track_city":"Harrington",
         "track_state":"DE",
         "name":"win_place",
         "multiplicity":2,
         "track_id":56,
         "description":null,
         "position_count":1,
         "featured":false,
         "wager_amount":0.0,
         "payoff_amount":0.0,
         "wager_payoff":0.0,
         "wager_minimum":1.0,
         "wager_minimums":[
            {
               "provider_name":"practice",
               "provider_id":5,
               "single_bet_minimum":10.0,
               "multiple_bet_minimum":10.0
            },
            {
               "provider_name":"derby",
               "provider_id":1,
               "single_bet_minimum":1.0,
               "multiple_bet_minimum":1.0
            },
            {
               "provider_name":"xpressbet",
               "provider_id":3,
               "single_bet_minimum":1.0,
               "multiple_bet_minimum":1.0
            }
         ],
         "expected_post_time":"2018-05-14T14:20:00-07:00",
         "size":5000.0,
         "multi_race":false,
         "races":[
            {
               "id":905096,
               "final":false,
               "race_number":2,
               "post_datetime":"2018-05-14T14:20:01-07:00",
               "live_wager_count":null,
               "live_user_count":null
            }
         ]
      },
      {
         "id":7205404,
         "track_name":"Harrington Raceway",
         "track_city":"Harrington",
         "track_state":"DE",
         "name":"win_place_show",
         "multiplicity":3,
         "track_id":56,
         "description":null,
         "position_count":1,
         "featured":false,
         "wager_amount":0.0,
         "payoff_amount":0.0,
         "wager_payoff":0.0,
         "wager_minimum":1.0,
         "wager_minimums":[
            {
               "provider_name":"practice",
               "provider_id":5,
               "single_bet_minimum":10.0,
               "multiple_bet_minimum":10.0
            },
            {
               "provider_name":"derby",
               "provider_id":1,
               "single_bet_minimum":1.0,
               "multiple_bet_minimum":1.0
            },
            {
               "provider_name":"xpressbet",
               "provider_id":3,
               "single_bet_minimum":1.0,
               "multiple_bet_minimum":1.0
            }
         ],
         "expected_post_time":"2018-05-14T14:20:00-07:00",
         "size":5000.0,
         "multi_race":false,
         "races":[
            {
               "id":905096,
               "final":false,
               "race_number":2,
               "post_datetime":"2018-05-14T14:20:01-07:00",
               "live_wager_count":null,
               "live_user_count":null
            }
         ]
      },
      {
         "id":7205398,
         "track_name":"Harrington Raceway",
         "track_city":"Harrington",
         "track_state":"DE",
         "name":"show",
         "multiplicity":1,
         "track_id":56,
         "description":null,
         "position_count":1,
         "featured":false,
         "wager_amount":0.0,
         "payoff_amount":0.0,
         "wager_payoff":0.0,
         "wager_minimum":1.0,
         "wager_minimums":[
            {
               "provider_name":"practice",
               "provider_id":5,
               "single_bet_minimum":10.0,
               "multiple_bet_minimum":10.0
            },
            {
               "provider_name":"derby",
               "provider_id":1,
               "single_bet_minimum":1.0,
               "multiple_bet_minimum":1.0
            },
            {
               "provider_name":"xpressbet",
               "provider_id":3,
               "single_bet_minimum":1.0,
               "multiple_bet_minimum":1.0
            }
         ],
         "expected_post_time":"2018-05-14T14:20:00-07:00",
         "size":1113.0,
         "multi_race":false,
         "races":[
            {
               "id":905096,
               "final":false,
               "race_number":2,
               "post_datetime":"2018-05-14T14:20:01-07:00",
               "live_wager_count":null,
               "live_user_count":null
            }
         ]
      },
      {
         "id":7205390,
         "track_name":"Harrington Raceway",
         "track_city":"Harrington",
         "track_state":"DE",
         "name":"place",
         "multiplicity":1,
         "track_id":56,
         "description":null,
         "position_count":1,
         "featured":false,
         "wager_amount":0.0,
         "payoff_amount":0.0,
         "wager_payoff":0.0,
         "wager_minimum":1.0,
         "wager_minimums":[
            {
               "provider_name":"practice",
               "provider_id":5,
               "single_bet_minimum":10.0,
               "multiple_bet_minimum":10.0
            },
            {
               "provider_name":"derby",
               "provider_id":1,
               "single_bet_minimum":1.0,
               "multiple_bet_minimum":1.0
            },
            {
               "provider_name":"xpressbet",
               "provider_id":3,
               "single_bet_minimum":1.0,
               "multiple_bet_minimum":1.0
            }
         ],
         "expected_post_time":"2018-05-14T14:20:00-07:00",
         "size":1562.0,
         "multi_race":false,
         "races":[
            {
               "id":905096,
               "final":false,
               "race_number":2,
               "post_datetime":"2018-05-14T14:20:01-07:00",
               "live_wager_count":null,
               "live_user_count":null
            }
         ]
      },
      {
         "id":7205383,
         "track_name":"Harrington Raceway",
         "track_city":"Harrington",
         "track_state":"DE",
         "name":"win",
         "multiplicity":1,
         "track_id":56,
         "description":null,
         "position_count":1,
         "featured":false,
         "wager_amount":0.0,
         "payoff_amount":0.0,
         "wager_payoff":0.0,
         "wager_minimum":1.0,
         "wager_minimums":[
            {
               "provider_name":"practice",
               "provider_id":5,
               "single_bet_minimum":10.0,
               "multiple_bet_minimum":10.0
            },
            {
               "provider_name":"derby",
               "provider_id":1,
               "single_bet_minimum":1.0,
               "multiple_bet_minimum":1.0
            },
            {
               "provider_name":"xpressbet",
               "provider_id":3,
               "single_bet_minimum":1.0,
               "multiple_bet_minimum":1.0
            }
         ],
         "expected_post_time":"2018-05-14T14:20:00-07:00",
         "size":4022.0,
         "multi_race":false,
         "races":[
            {
               "id":905096,
               "final":false,
               "race_number":2,
               "post_datetime":"2018-05-14T14:20:01-07:00",
               "live_wager_count":null,
               "live_user_count":null
            }
         ]
      }
   ],
   "wins":[

   ],
   "winning_tickets":[

   ],
   "type":"race",
   "action":"changed",
   "map_url":"https://dj1.derbycdn.net/assets/maps/har.png"
}
```


Field | Description
----- | -----------
id | the integer id of the race
race_number | the number of the race for a given track/day
race_type | Thoroughbred, Harness, Quarterhorse
finalized | whether the race is finalized (true or false). A finalized race has finished and all wagers paid out
post_datetime | the time that the race is scheduled to begin (a string formatted datetime). This value can and does change frequently! A polling process will be necessary to ensure the estimated post datetime (and associated countdowns) are working
status | "Open", "Closed" or "Final" - only a race with a status of "Open" can accept wagers
runners | array of ADW Runner objects
pools | array of ADW Pool objects


# ADW Runners

```
  {
     "id":6938045,
     "number":8,
     "scratched":false,
     "odds":"50/1",
     "final_position":null,
     "jockey":"Jason Green",
     "trainer":"Frank Kryskowiak",
     "owner":"Frank C Kryskowiak,Felton,DE",
     "multi_entry_flag":null,
     "horse":{
        "id":5418,
        "name":"Bettoriffic",
        "horse_type":"Harness",
        "favorite_count":0,
        "description":null,
        "history":[
           {
              "odds":"35/1",
              "scratched":false,
              "final_position":4,
              "race_date":"2018-05-07"
           },
           {
              "odds":"50/1",
              "scratched":false,
              "final_position":null,
              "race_date":"2018-04-30"
           },
           {
              "odds":"40/1",
              "scratched":false,
              "final_position":null,
              "race_date":"2018-04-18"
           },
           {
              "odds":"12/1",
              "scratched":false,
              "final_position":4,
              "race_date":"2018-04-09"
           },
           {
              "odds":"80/1",
              "scratched":false,
              "final_position":2,
              "race_date":"2018-03-26"
           }
        ]
     }
  }
```

Field | Description
----- | -----------
id | the integer id of the runner
number | the number of the runner in the race - like instant racing - this is the number used to determine which horse you're betting on. Note: this number is an integer and there can occasionally be duplicate numbers in a race. when two horses share a number - if you choose that number and either horse wins, you win
scratched | whether or not a horse has been "scratched" or taken out of a race - you cannot bet on scratched runners. In the case where there is, for example, two #1 horses in a race, one with scratched: true and one with scratched: false - you can still bet on the #1 horse
odds | the current odds of the horse. these change even more frequently than post_datetime and should be updated in the race polling
final_position | the position the horse finished the race. will be null until a short period of time after the race has finished. for most races - only final positions 1 through 4 are served up in the race. it is possible for horses to tie in a race, so a given race could for example have runners with the final positions 1, 2, 2 and 4, indicating a tie for second
horse | a description of the horse racing, the last ~5 races that a given horse has raced


# ADW: Pools

```
  {
     "id":7205411,
     "track_name":"Harrington Raceway",
     "track_city":"Harrington",
     "track_state":"DE",
     "name":"win_place",
     "multiplicity":2,
     "track_id":56,
     "description":null,
     "position_count":1,
     "featured":false,
     "wager_amount":0.0,
     "payoff_amount":0.0,
     "wager_payoff":0.0,
     "wager_minimum":1.0,
     "wager_minimums":[
        {
           "provider_name":"practice",
           "provider_id":5,
           "single_bet_minimum":10.0,
           "multiple_bet_minimum":10.0
        },
        {
           "provider_name":"derby",
           "provider_id":1,
           "single_bet_minimum":1.0,
           "multiple_bet_minimum":1.0
        },
        {
           "provider_name":"xpressbet",
           "provider_id":3,
           "single_bet_minimum":1.0,
           "multiple_bet_minimum":1.0
        }
     ],
     "expected_post_time":"2018-05-14T14:20:00-07:00",
     "size":5000.0,
     "multi_race":false,
     "races":[
        {
           "id":905096,
           "final":false,
           "race_number":2,
           "post_datetime":"2018-05-14T14:20:01-07:00",
           "live_wager_count":null,
           "live_user_count":null
        }
     ]
  }
```

Field | Description
----- | -----------
id | the integer id of the pool
name | the name of the pool
multiplicity | the number of pools that this pool represents - most pools are `multiplicity=1`, however the win_place and win_place_show have multiplicity of 2 and 3 respectively. This means that, for example, when you place a win_place bet, you are making two bets,  one in the win and and one in the place pool, so a $2 win_place bet will actually cost $4 ($2 in the win pool and $2 in the place pool)
wager_minimums | the minimum required wager for the pool, by provider.
races | the races involved in a pool

# ADW: Wagers

