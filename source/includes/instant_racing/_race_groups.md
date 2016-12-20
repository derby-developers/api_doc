# Instant Racing: RaceGroups

## RaceGroup Object

```json
{
  "id":1,
  "name": "San Francisco"
}
```

Field | Description
----- | -----------
id |
name |

## Get all Race Groups

Returns all the race groups, ordered as they should be shown to the user.

<aside class="warning">
This endpoint subject to change soon.
</aside>

> Example

```curl
curl -H "Application-Name: super-fun-game" \
  -H "Authorization: Bearer ABC123" \
  https://api.derbygames.com/api/instant_racing/race_groups
```

`GET /instant_racing/race_groups`

### Returns

An array of `RaceGroup` objects.
