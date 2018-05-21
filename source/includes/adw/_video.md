# ADW: Video

```curl
curl -H "Application-Name: racechamp3_ios" \
  -H "Authorization: Bearer abc1234" \
  -H "Content-Type: application/json" \
  https://api.derbygames.com/api/tracks/101/video?stream_format=rtsp
```

## Get the live video for the current track
Field | Description
----- | -----------
track_id| the id of the track for the race you're currently betting on (`track_id` in the race node)
stream_format| the format of the video - options are either "flash" or "rtsp" (rtsp recommended for mobile devices)
