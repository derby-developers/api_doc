# Instant Racing: Tasks

## Updating task progress example

`PUT /instant_racing/tasks/:id`

> Updating tasks

```curl
curl -X PUT \
  -H "Application-Name: super-fun-game" \
  -H "Authorization: Bearer ABC123" \
  -H "Content-Type: application/json" \
  -d '{ "amount_played": 1000.0 }' \
  https://api.racechamp.com/api/instant_racing/tasks/:id
```

### Returns
A `Task` object
