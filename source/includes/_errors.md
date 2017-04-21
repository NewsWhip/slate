# Errors

The NewsWhip API uses the following error codes:

Error Code | Meaning
---------- | -------
400 | Bad Request -- Your request could not be parsed.
403 | Forbidden -- Your API key is not allowed to access this resource. Your API key is expired or invalid.
429 | Too Many Requests -- Enhance your calm! or contact us for higher limits!
500 | Internal Server Error -- We had a problem with our server. Please try again later.
503 | Service Unavailable -- We're temporarily offline for maintenance. Please try again later.

# More Information

## Server-side Caching

* `GET` queries are cached (per API Key) for a small amount of time. Usually about 3 minutes. Check the HTTP headers sent by our servers for an exact value.
* `POST` queries are never cached.

## Cross-Origin Resource Sharing

* `GET` endpoints support 1 `Cross-origin resource sharing` per API key. Contact api@newswhip.com to set this up.
* `POST` endpoints are server-side only.

## JSONP

We don't currently support JSONP.

# Changelog

### Version 1.0.8 (2017-04-21)

- Added /v1/fbPost endpoint
- Added default_fields to all POST requests
- Other minor related updates

### Version 1.0.7 (2016-11-22)

- Updated examples of POST /v1/articles

### Version 1.0.6 (2016-08-04)

- Added option to sort by `fb_total_engagement` in POST /v1/articles
- Restricted option to sort by `fb_likes`, `fb_shares`, `fb_comments`, `fb_loves`, `fb_wows`, `fb_hahas`, `fb_sads`, `fb_angrys` only for `content_type` `fb_posts`  in POST /v1/articles
- Removed `fb_likes`, `fb_shares`, `fb_comments` from `sort_by` in POST /v1/stats

### Version 1.0.5 (2016-06-20)

- Added `content_type` field in POST /v1/articles
- Updated examples of POST /v1/articles

### Version 1.0.4 (2015-12-03)

- Fixed typo in GET /v1/search example

### Version 1.0.3 (2015-07-09)

- Added `region_code` and `domain` to available fields for filtering
- Added `keywords` field to Article entity

### Version 1.0.2 (2015-03-03)

- Added `has_video` field to Article entity

### Version 1.0.1 (2015-02-11)

- Added a new `sort_by` method: `created_at` to sort by most recent
- The filtering field `country` is deprecated, use `country_code` instead
- In Entities, Article. The field `country_code` replaces `country`. The contents of `country` will be set to 'World'


### Version 1.0.0 (2014-11-21)

- First public version
