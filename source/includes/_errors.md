# Errors

<aside class="notice">
When a POST request returns an error, a common error format is returned.
</aside>

## Errors Object

```json
  {
    "errors": [
      {
        "code": "blank",
        "param": "amount",
        "message": "can't be blank"
      }
    ]
  }
```

Field | Description
--------- | -----------
errors | an array of Error objects


## Error Object

```json
  {
    "code": "blank",
    "param": "amount",
    "message": "can't be blank"
  }
```

Field | Description
--------- | -----------
code | a code indicating the type of error
param (optional) | a parameter that the error applies to, if any
message | a human-readable message describing the error
