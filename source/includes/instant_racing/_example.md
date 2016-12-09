# Instant Racing: Example Flow

Below is an example of the endpoints you need to get a race, wager on the race, view the video, then see the results.

## 1. Get a User & Credits

First, you'll need a user token that has credits. If you need to, you can generate a guest user with the example to the right.

> Token Example

```curl
curl -X POST -H "Application-Name: racechamp_mobile_app" \
  -H "Content-Type: application/json" \
  -d '{ "grant_type": "guest", "device_id": "some-unique-device-id" }' \
  https://api.derbygames.com/api/oauth/token
```

> Bonus Example

```curl
curl -H "Application-Name: super-fun-game" \
  -H "Authorization: Bearer ABC123" \
  -H "Content-Type: application/json" \
  -d '{ "bonus_name": "instant_racing_refill" }' \
  https://api.derbygames.com/api/awarded_bonuses
```

If that user does not have credits, you can award the refill bonus. You will want the _instant_racing_refill_ bonus.


## 2. Get a Race

Races are user specific and this endpoint will continue to serve the same race until the decide endpoint is called.

> Example

```curl
curl -H "Authorization: Bearer ABC123" \
  -H "Application-Name: racechamp_mobile_app" \
  https://api.derbygames.com/api/instant_racing/races/current
```

## 3. Place a Wager

> Example

```curl
curl -H "Application-Name: racechamp_mobile_app" \
  -H "Authorization: Bearer ABC123" \
  -H "Content-Type: application/json" \
  -d '{ "amount": 10, "race_id": "<RACE_ID>"}' \
  https://api.derbygames.com/api/instant_racing/super_slot_spins
```

Place a Super Slot wager.

## 4. Decide the Race

> Example

```curl
curl -X PUT -H "Application-Name: racechamp_mobile_app" \
  -H "Authorization: Bearer ABC123" \
  https://api.derbygames.com/api/instant_racing/races/<RACE_ID>/decide
```

Close wagering and enqueue a job to calculate wager payoffs.

## 5. Get the Video URL

> Example

```curl
curl -H "Application-Name: racechamp_mobile_app" \
  -H "Authorization: Bearer ABC123" \
  https://api.derbygames.com/api/instant_racing/races/<RACE_ID>/video?quality=low
```

Video must be requested within 5 minutes of hitting the decide endpoint.

## 6. Get Wager Payoffs

> Example

```curl
curl -H "Application-Name: racechamp_mobile_app" \
  -H "Authorization: Bearer ABC123" \
  https://api.derbygames.com/api/instant_racing/races/<RACE_ID>/wagers
```

Wagers will have payoff_amounts now.

## 7. Get Updated Account Balance

The balance would be updated a few seconds after the decide enpoint was called, but you should avoid changing the users balance until the video is over to avoid spoilers.

> Example

```curl
curl -H "Application-Name: racechamp_mobile_app" \
  -H "Authorization: Bearer ABC123" \
  https://api.derbygames.com/api/accounts
```
