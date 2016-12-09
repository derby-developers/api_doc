# Introduction

For API access, please contact eric@derbygames.com. You will be issued:

* application name
* application group name
* cliend ID / secret

# Interacting with the API

## Making Requests

All requests:

* must be over HTTPS
* must have an application name, either as a header 'Application-Name' or as a query string 'application_name'
* for POST/PUT requests: must have the content type of `application/json`

## Localization

There is limited support for localization using the `Accept-Language` header. Currently, we allow:

* `en` - English (default)
* `es` - Spanish
* `pt` - Portuguese (Brazil)

Any non supported locale will default to English.

Numbers, currency and datetime don’t rely on localization so they will be returned in standard format.

## Versioning

This document applies to V1, which is the current live version. To maintain compatibility with this version, it is recommended you add an accepts header:

`Accept: version=1`

## Objects

Any field not explicitly listed should be avoided as it is subject to change.


## Endpoints

Sandbox API

`https://sandbox-api.derbygames.com/api/`

Production API

`https://api.derbygames.com/api/`
