# ADW: Wagers

The most notable difference between these wagers and instant racing wagers is that you pass runner ids and pool ids retrieved from the race.

> Win/Place Example

```curl
curl -H "Application-Name: racechamp3_ios" \
  -H "Authorization: Bearer abc1234" \
  -H "Content-Type: application/json" \
  -d '{"amount": "10.0", "pool": {"id": 7207631 }, "runners": [{"id": 6952547}] }' \
  https://api.derbygames.com/api/wagers
```

> Example response

```json
{
   "id":39415867,
   "success":true,
   "response":null,
   "response_status":"success",
   "amount":"10.0",
   "box":false,
   "jackpot":false,
   "serialized_runners":"6",
   "base_amount":"5.0",
   "race_id":907415,
   "pool_id":7207684,
   "user":{
      "id":32119,
      "wager_count":5767,
      "practice_wager_count":569,
      "multi_race_wager_count":744,
      "balance":99.0,
      "withdrawable_balance":99.0,
      "practice_balance":4511.0
   },
   "failure_message":null,
   "created_at":1526391558,
   "race":{
      "id":907415,
      "status":"Open",
      "finalized":false,
      "action_message":null,
      "name":"Wincanton Racecourse",
      "race_type":"Thoroughbred",
      "track_id":254,
      "number":2,
      "post_datetime":"2018-05-15T06:48:14-07:00"
   },
   "runners":[
      {
         "id":6959587,
         "number":6,
         "race_id":907415,
         "wager_position":100220071,
         "horse":{
            "id":154393,
            "name":"Ice Tres",
            "horse_type":"Thoroughbred"
         }
      }
   ]
}
```
