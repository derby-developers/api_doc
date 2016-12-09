# Instant Racing: Video

## Video Object

```json
{
  "video_url":"https://instant-racing-video.derbycdn.net/2b/2b368e19-ad1a-44a7-835f-98790948707e/256.mp4",
  "video_duration_seconds":81
}
```

Field | Description
----- | -----------
video_url | URL of the video (link expires in 5 minutes)
video_duration_seconds | total length, in seconds

## Viewing Video

> Example

```curl
curl -H "Application-Name: super-fun-game" \
  -H "Authorization: Bearer ABC123" \
  https://api.derbygames.com/api/instant_racing/races/<RACE_ID>/video?quality=low
```

`GET /instant_racing/races/<RACE_ID>/video?quality=[low|high|hls]`

'low' and 'high' will be an MP4. HLS will return a m3u8 playlist.

<aside class="notice">
A race must be decided to get a video URL, otherwise null will be returned. Video must also be requested within 5 minutes of being decided.
</aside>
