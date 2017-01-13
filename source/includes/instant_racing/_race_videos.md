# Instant Racing: Race Videos

Field | Description
----- | -----------
filename | the video filename
position_timings | an array of objects describing the position timings

> Example

```curl
curl -H "Application-Name: super-fun-game" \
  -H "Authorization: Bearer ABC123" \
  -X PUT
  -d '{ "filename": "foo.mp4", position_timings: [{"offset": 0, "positions": [1, 2, 3, 4] }, {"offset": 10, positions: [2, 1, 3, 4]}]  }' \
  https://api.derbygames.com/api/instant_racing/race_videos
```