# Instant Racing: Race Videos

<aside class="notice">
All endpoints for Race Videos need a token with the import_instant_racing_race_video_positions scope.
</aside>

## RaceVideo Object

```json
 {
    "id": 1,
    "post_time_seconds": 10,
    "finish_line_seconds": 100,
    "original_url": "s3://bucket/filename.mp4",
    "type": "video/mp4",
    "ocr_success": true,
    "position_timings": [{"offset": 0, "positions": [1, 2, 3, 4] }]
}
```

Field | Description
----- | -----------
id |
post_time_seconds | time, in seconds, when the race starts
finish_line_seconds | time, in seconds, when the finish line is crossed
original_url | s3 bucket URL of the original video
type | video/mp4 or video/flash
ocr_success | boolean if the OCR was a success
position_timings | array of offsets/times


## Get RaceVideos

`GET /api/instant_racing/race_videos`

> Example

```curl
curl -H "Application-Name: super-fun-game" \
  -H "Authorization: Bearer ABC123" \
  https://api.derbygames.com/api/instant_racing/race_videos?ocr_success=false
```

Paramater | Required | Description
----- | ----------- | ----------
ocr_success | no | boolean if races passed or failed OCR
track_id | no | track ID (21 = Penn, Zia = 81, Mahoning = 451)
clipped | no | boolean if race has been clipped

Examples: 

If you would like to get a list of videos to OCR, pass in the track_id and clipped = true. 
If you would like videos that have failed OCR, pass in ocr_success = false.

### Returns

An array of RaceVideo objects. Max 1,000 and ordered by race date (newest first).

## Updating RaceVideo position timings

`PUT /api/instant_racing/race_videos`

> Example

```curl
curl -H "Application-Name: super-fun-game" \
  -H "Authorization: Bearer ABC123" \
  -X PUT
  -d '{ "filename": "foo.mp4", position_timings: [{"offset": 0, "positions": [1, 2, 3, 4] }, {"offset": 10, positions: [2, 1, 3, 4]}]  }' \
  https://api.derbygames.com/api/instant_racing/race_videos
```

Field | Description
----- | -----------
filename | the video filename
ocr_success | true/false if the OCR was a success
position_timings | an array of objects describing the position timings
