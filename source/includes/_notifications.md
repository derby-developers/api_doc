# User Notifications

## Notification Object

```json
[
  {
    "id": 1,
    "message": "Hello, player!",
    "thumbnail_image_url": null,
    "expires_at": "2016-11-03T00:00:00.000-07:00",
    "bonus": {},
    "read": false,
    "created_at": "2016-11-01T14:17:56.991-07:00",
    "expired": false,
    "claimed": true,
    "claimed_at":"2016-11-01T14:52:50.443-07:00"
  }
]

```

Field | Description
------| -----------
id |
message | text of the message
thumbnail_image_url | fully qualified thumbail URL, if provided
expires_at | expiration
bonus | Bonus Object, if applicable
read | boolean if message has been read
created_at | date of the message
expired | boolean if notification has expired
claimed | boolean if this is a bonus that has been claimed
claimed_at |

## Get Notifications

> Example

```curl
curl -H "Application-Name: super-fun-game" \
  -H "Authorization: Bearer ABC123" \
  https://api.derbygames.com/api/notifications
```

`GET /notifications`

### Returns

Array of `Notification` objects.

## Mark Message as Read

> Example

```curl
curl -X PUT \
  -H "Application-Name: super-fun-game" \
  -H "Authorization: Bearer ABC123" \
  https://api.derbygames.com/api/notifications/1/read
```

`PUT /notifications/<NOTIFICATION_ID>/read`

Marks a message as read.
