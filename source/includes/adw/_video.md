# ADW: Video
## Get live Video for the current track

`GET /api/tracks/<track id>/video?stream_format=<format>`


```curl
curl -H "Application-Name: racechamp3_ios" \
  -H "Authorization: Bearer abc1234" \
  -H "Content-Type: application/json" \
  https://api.derbygames.com/api/tracks/101/video?stream_format=rtsp
```

## Parameters
Parameter | Description
----- | -----------
track_id| the id of the track for the race you're currently betting on (`track_id` in the race node)
stream_format| the format of the video - options are either "flash" or "rtsp" (rtsp recommended for mobile devices)


```json
{
   "video_url":"https://stream.robertsstream.com/streammobile.php?stream=louisiana_mbr\u0026referer=XpressBet\u0026t=1526933818\u0026h=97a3c83ca96f5cc9379e88be1070b18d\u0026usr=1332350\u0026optp=siteid%3Axpres%7Coriginid%3ADJA",
   "success":true,
   "error_code":null
}
```

## Video Response
Field | Description
----- | -----------
video_url | the url of the video in question
