---
title: API Reference | NewsWhip

language_tabs:
  - shell
  - php

toc_footers:
  - <a href='#getting-api-access'>Sign Up for a Developer Key</a>
  - <p>© 2016 NewsWhip Media Ltd.</p>

includes:
  - errors

search: true
---

# Overview

Welcome to the NewsWhip API documentation. The NewsWhip API provides access to real time data trends, aggregate data, statistics, and social numbers for all content we have been tracking since January 1, 2014 - hundreds of millions of stories, fully categorized and ranked.

The NewsWhip API is language agnostic. Any HTTP client or library can be used with this API.

This documentation is open source. If you've found any errors, typos or would like to improve this document, feel free to send us a pull request: [GitHub](http://github.com/NewsWhip/slate).

# Authentication

All NewsWhip API endpoints require an API key. Your API key should be passed with each `GET` or `POST` request as a Query String.

`GET /v1/region/U.S./Politics/24?key=YOUR_API_KEY`

`POST /v1/articles?key=YOUR_API_KEY`

<aside class="warning">Your API key should be treated as a password. It should be kept secret at all times.</aside>

## Getting API Access

Our API is made available to NewsWhip clients and developers who wish to work with streams of trending content in any niche. Right now, it's powering widgets on major news sites, internal dashboards, and mobile apps in Europe and North America.

For details on getting access, email: [api@newswhip.com](mailto:api@newswhip.com).

# Rate Limits

Each API key is limited by default to 100 API requests per 5 minutes. Once you exceed this limit, calls will return:

Error Code | Meaning
---------- | -------
429 | Too Many Requests -- You're requesting too many kittens! Slow down!

<aside class="notice">Contact us at api@newswhip.com if your application requires higher limits.</aside>

# API Endpoints

NewsWhip provides 2 different endpoints designed for different use cases, each available at varying commercial rates.

* `GET` requests: best suited for finding real-time trending articles in any niche and social network, with or without video and published in any country up to a week ago.
* `POST` requests: best suited for very precise article filtering, real-time analytics, aggregations and reporting. These APIs slice and dice our data in any form you want.

### HTTPS Endpoint
`https://api.newswhip.com/`

# GET Requests

The real-time GET API endpoints are designed to mirror Spike's functionality. You can get all trending content in any Niche or Region, ordered by any social metric.

There are 4 different endpoints:

* `GET /v1/region/{region}/{category}/{time_period}`
* `GET /v1/publisher/{publisher}/{time_period}`
* `GET /v1/local/{city}/All/{time_period}`
* `GET /v1/search?q={search_term}`

All 4 GET endpoints accept the following Query Parameters:

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
video_only | false | If set to true, the result will ONLY include content with embedded video.
sort_by | default | Defines how the articles are ranked. Accepts one of the following: `default`, `fb_total_engagement`, `twitter`, `linkedin`, `fb_tw_and_li`, `nw_score`, `nw_max_score`
size |  | Number of articles to be returned (including related articles).

To retrieve a full list of the available fields for each filter (regions, categories, publishers), access:

### Available Regions and Categories
`GET /v1/region`

### Sample of publishers we support
`GET /v1/publisher`

### Available cities and local regions
`GET /v1/local`


## GET /v1/region

> Get the top trending English content published in the last 24 hours

``` shell
curl "https://api.newswhip.com/v1/region/World/All/24?key=YOUR_API_KEY"
```

``` php
<?php
require 'vendor/autoload.php';
use GuzzleHttp\Client;

$client = new Client();
$response = $client->get('https://api.newswhip.com/v1/region/World/All/24?key=YOUR_API_KEY', []);
echo $response->getBody();
?>
```

```json
{
  "articles": [
    {
      "link": "https://www.fcbarcelona.com/football/first-team/news/2016-2017/fc-barcelona-v-leicester-city-victory-in-the-battle-of-champions-4-2-",
      "headline": "FC Barcelona v Leicester City: Victory in the battle of champions (4-2) | FC Barcelona",
      "excerpt": "Goals from Munir (2) and Luis Suárez put Barça in early command, and a late strike from Mújica puts paid to Premiership champions’ bid to make a comeback",
      "keywords": "",
      "source": {
        "publisher": "fcbarcelona.com",
        "link": "https://fcbarcelona.com",
        "country": "",
        "country_code": ""
      },
      "nw_score": 637.4492809499226,
      "max_nw_score": 3814.5714659846194,
      "fb_data": {
        "total_engagement_count": 62988,
        "total_count_delta": 9820,
        "delta_period": 208,
        "delta_period_unit": "m"
      },
      "tw_data": {
        "tw_count": 480,
        "total_count_delta": 40,
        "delta_period": 208,
        "delta_period_unit": "m"
      },
      "li_data": {
        "li_count": 1,
        "total_count_delta": 0,
        "delta_period": 208,
        "delta_period_unit": "m"
      },
      "tw_creator": null,
      "delta_time": 208,
      "uuid": "9cb602c0-59b7-11e6-aec9-8557dc1ae32f",
      "publication_timestamp": 1470255517000,
      "image_link": "https://pro-cdn-public-fcb.everincloud.com/20157/0/document_thumbnail/20197/163/163/14590883/1.0-1/14590883.png?t=1453214443000",
      "relatedStories": [
        {
          "link": "http://www.goal.com/en/match/barcelona-vs-leicester-city/2223206/report",
          "headline": "Barcelona 4 - 2 Leicester City Match report - 8/3/16 International Champions Cup - Goal.com",
          "excerpt": "Read the full Barcelona v Leicester City match report, including goals, incidents, and much more. Have your say on the game in our comments feature.",
          "keywords": "",
          "source": {
            "publisher": "goal.com",
            "link": "http://goal.com",
            "country": "",
            "country_code": ""
          },
          "nw_score": 514.8946690316512,
          "max_nw_score": 1740.3519248567559,
          "fb_data": {
            "total_engagement_count": 44464,
            "total_count_delta": 8736,
            "delta_period": 254,
            "delta_period_unit": "m"
          },
          "tw_data": {
            "tw_count": 90,
            "total_count_delta": 0,
            "delta_period": 254,
            "delta_period_unit": "m"
          },
          "li_data": {
            "li_count": 0,
            "total_count_delta": 0,
            "delta_period": 254,
            "delta_period_unit": "m"
          },
          "tw_creator": null,
          "delta_time": 254,
          "recent_fb_counts": 8736,
          "recent_tw_counts": 0,
          "uuid": "a39d81a0-59b5-11e6-8992-ffce69f79e2d",
          "publication_timestamp": 1470254187000,
          "image_link": "",
          "relatedStories": [],
          "topics": [
            {
              "id": 32,
              "name": "Sports"
            },
            {
              "id": 33,
              "name": "Soccer"
            }
          ],
          "has_video": false
        }
      ],
      "topics": [],
      "has_video": false
    }
  ]
}
```

`GET /v1/region/{region}/{category}/{time_period}`

This endpoint retrieves all articles published in `{region}` and `{category}` within the `{time_period}`.

### Parameters

Parameter | Description
--------- | -----------
region | Filters articles published in `{region}`. See above for available countries. i.e. `U.S.`, `France`, `Ireland`. Note: the region should be passed in English.
category | Filters articles by `{category}`. See above for available categories. i.e. `All`, `News`, `Pre-Viral`. Note: the category should be passed in English.
time_period | Filters articles published within the last `{time_period}` hours. Valid `time_periods` range from 1 up to 168 hours

## GET /v1/publisher

> Get the top trending content published in the last 24 hours by the New York Times.

``` shell
curl "https://api.newswhip.com/v1/publisher/nytimes.com/24?key=YOUR_API_KEY"
```

``` php
<?php
require 'vendor/autoload.php';
use GuzzleHttp\Client;

$client = new Client();
$response = $client->get('https://api.newswhip.com/v1/publisher/nytimes.com/24?key=YOUR_API_KEY', []);
echo $response->getBody();
?>
```

`GET /v1/publisher/{publisher}/{time_period}`

This endpoint retrieves all articles published by `{publisher}` within the `{time_period}`.

### Parameters

Parameter | Description
--------- | -----------
publisher | Any domain or subdomain. i.e. `nytimes.com`, `blog.newswhip.com`.
time_period | Filters articles published within the last `{time_period}` hours. Valid `time_periods` range from 1 up to 168 hours

## GET /v1/local

> Get the top trending content published in Seattle, in the last 12 hours.

``` shell
curl "https://api.newswhip.com/v1/local/Seattle, WA/All/12?key=YOUR_API_KEY"
```

``` php
<?php
require 'vendor/autoload.php';
use GuzzleHttp\Client;

$client = new Client();
$response = $client->get('https://api.newswhip.com/v1/local/Seattle, WA/All/12?key=YOUR_API_KEY', []);
echo $response->getBody();
?>
```

`GET /v1/local/{city}/All/{time_period}`

This endpoint retrieves all articles published in `{city}` within the `{time_period}`.

### Parameters

Parameter | Description
--------- | -----------
city | Any city or local region. See above for available local regions. i.e. `New York, NY`, `London`, `Toronto`, `Hamburg-Schleswig-Holstein`.
time_period | Filters articles published within the last `{time_period}` hours. Valid `time_periods` range from 1 up to 168 hours

## GET /v1/search

> Get the top trending content published talking about `Tom Cruise`, in the last 24 hours.

``` shell
curl "https://api.newswhip.com/v1/search?q=Tom%20Cruise&key=YOUR_API_KEY"
```

``` php
<?php
require 'vendor/autoload.php';
use GuzzleHttp\Client;

$client = new Client();
$response = $client->get('https://api.newswhip.com/v1/search?q=Tom%20Cruise&key=YOUR_API_KEY', []);
echo $response->getBody();
?>
```

`GET /v1/search?q={search_term}`

This endpoint retrieves all articles talking about `{search_term}` in the last 24 hours.

### Parameters

Parameter | Description
--------- | -----------
search_term | Matches all stories containing `{search_term}`.

# POST Requests

The POST API endpoints are designed for increased flexibility and are much more powerful. With these server-side only endpoints your application gets full access to NewsWhip's database, including all content published within the last 6 months from any publisher in any supported language. Filtered, sorted and aggregated by any field you want.

There are 2 different endpoints:

* `POST /v1/articles` - provides stories(web articles, youtube post) matching the query provided
* `POST /v1/fbPosts` - provides facebook posts matching the query provided 
* `POST /v1/stats` - provides stats on the content matching the query provided


## POST /v1/articles

> Get the top trending stories published in United States or United Kingdom that talk about Rihanna not published in youtube.com since a week ago

``` shell
curl -H "Content-Type: application/json" -X POST -d '{
    "filters": ["country_code:(us OR gb) AND -publisher:youtube.com AND headline:rihanna"],
    "language": "en",
    "video_only":false,
    "sort_by": "nw_max_score",
    "find_related": false,
    "size": 1
}' "https://api.newswhip.com/v1/articles?key=YOUR_API_KEY"
```

```php
<?php
require 'vendor/autoload.php';
use GuzzleHttp\Client;

$client = new Client();
$response = $client->post('https://api.newswhip.com/v1/articles?key=YOUR_API_KEY', [
    'headers' => ['Content-Type' => 'application/json'],
    'body' => '{
        "filters": [
            "country_code:(us OR gb) AND -publisher:youtube.com AND headline:rihanna"
        ],
        "language": "en",
        "video_only":false,
        "sort_by": "nw_max_score",
        "find_related": false,
        "size": 1
    }']);
echo $response->getBody();
?>
```

```json
{
  "articles": [
    {
      "link": "http://www.rap-up.com/2016/11/15/partynextdoor-talks-drake-rihanna-jeremih-tour/",
      "headline": "PARTYNEXTDOOR Talks Drake, Rihanna, & Touring with Jeremih",
      "excerpt": "In the midst of his \"Summer's Over Tour\" with Jeremih, PARTYNEXTDOOR stopped by Power 98 in Charlotte, North Carolina for ...",
      "keywords": "",
      "source": {
        "publisher": "rap-up.com",
        "link": "http://rap-up.com",
        "country": "United States",
        "country_code": "us"
      },
      "nw_score": 0.05852343318906164,
      "max_nw_score": 729.5439348623742,
      "fb_data": {
        "total_engagement_count": 2128,
        "total_count_delta": 3,
        "delta_period": 1033,
        "delta_period_unit": "m"
      },
      "tw_data": {
        "tw_count": 20,
        "total_count_delta": 0,
        "delta_period": 1033,
        "delta_period_unit": "m"
      },
      "li_data": {
        "li_count": 0,
        "total_count_delta": 0,
        "delta_period": 1033,
        "delta_period_unit": "m"
      },
      "tw_creator": null,
      "delta_time": 1033,
      "uuid": "cec8e680-ab68-11e6-a1c9-8b1fd34d6bab",
      "publication_timestamp": 1479237731560,
      "image_link": "http://www.rap-up.com/wp-content/uploads/2016/11/partynextdoor-red.jpg",
      "relatedStories": [],
      "topics": [
        {
          "id": 3,
          "name": "Entertainment"
        }
      ],
      "has_video": true
    }
  ]
}
```

> Get the top trending  youtube posts that is talking about Rihanna since a week ago

``` shell
curl -H "Content-Type: application/json" -X POST -d '{
    "filters": ["country_code:(us OR gb) AND headline:rihanna"],
    "language": "en",
    "content_type": "youtube"
}' "https://api.newswhip.com/v1/articles?key=YOUR_API_KEY"
```

```php
<?php
require 'vendor/autoload.php';
use GuzzleHttp\Client;

$client = new Client();
$response = $client->post('https://api.newswhip.com/v1/articles?key=YOUR_API_KEY', [
    'headers' => ['Content-Type' => 'application/json'],
    'body' => '{
        "filters": [
            "country_code:(us OR gb) AND headline:rihanna"
        ],
        "language": "en",
        "content_type": "youtube"
    }']);
echo $response->getBody();
?>
```

```json
{
  "articles": [
    {
      "youtube_post": {
        "ytLikes": 12,
        "ytViews": 2795,
        "ytComments": 4,
        "ytDislikes": 28,
        "author": "NowThis",
        "thumbnail": "https://yt3.ggpht.com/-QYtGzlfBEUI/AAAAAAAAAAI/AAAAAAAAAAA/Pc6X3NBuup0/s240-c-k-no-mo-rj-c0xffffff/photo.jpg",
        "channel": "https://www.youtube.com/channel/UCn4sPeUomNGIr26bElVdDYg"
      },
      "fb_data": {
        "total_engagement_count": 0,
        "total_count_delta": 0,
        "delta_period": 0,
        "delta_period_unit": "m"
      },
      "tw_data": {
        "tw_count": 0,
        "total_count_delta": 0,
        "delta_period": 0,
        "delta_period_unit": "m"
      },
      "li_data": {
        "li_count": 0,
        "total_count_delta": 0,
        "delta_period": 0,
        "delta_period_unit": "m"
      },
      "relatedStories": [],
      "uuid": "f6f17650-13fe-11e7-98a6-114dfe4272d3",
      "publication_timestamp": 1490737083000,
      "link": "https://www.youtube.com/watch?v=o9ulb26biqI",
      "headline": "Rihanna Rocks Iconic 'Psycho' Shower Scene",
      "excerpt": "Rihanna Rocks Iconic 'Psycho' Shower Scene - But her 'Bates Motel' character is here to stay. --- Follow us on Facebook: https://www.facebook.com/NowThisNews...",
      "keywords": "",
      "source": {
        "publisher": "youtube.com",
        "link": "https://youtube.com",
        "country": "United States",
        "country_code": "us"
      },
      "image_link": "https://i.ytimg.com/vi/o9ulb26biqI/maxresdefault.jpg",
      "has_video": true,
      "delta_time": 0,
      "nw_score": 0,
      "max_nw_score": 0,
      "topics": []
    }
  ]
}
```

`POST /v1/articles`

This endpoint retrieves all articles matching the filters provided.

### Query Parameters

* Stories are filtered and sorted using the following `JSON` encoded parameters
* Required fields are denoted *
* Filtering by category or country requires ids which can be found here: [NewsWhip API Coverage](https://www.newswhip.com/coverage/)

Parameter | Default | Type | Description
--------- | ------- | ---- | -----------
filters* |  | Array[String] | Up to 10 [Lucene QueryString](https://lucene.apache.org/core/5_5_2/queryparser/org/apache/lucene/queryparser/classic/package-summary.html#package_description) filters to be applied to the articles. Each fitler allowes up to 150 terms where calculation is based on lucene query string semantics, e.g: `country_code:us` counts as 1 Term, `country_code:(us AND uk)` counts as 2 Terms, `headline: “The Right Way”` counts as 3 terms". See available fields for filtering down below
from | A week ago | Unix timestamp in milliseconds | Filters articles published after `{from}`
to | Now | Unix timestamp in milliseconds | Filters articles published before `{to}`
language | Any | Two letter ISO 639-1 language code | See availalbe languages <a href="#supported-languages">here</a>
sort_by | default | String | One of the following: `default`, `fb_total_engagement`, `twitter`, `linkedin`, `fb_tw_and_li`, `nw_score`, `nw_max_score`, `created_at`. When searching by the content_type `youtube` it’s supported to sort by `yt_likes`, `yt_views`, `yt_comments`, `yt_dislikes`
video_only | false | Boolean | Ignored when searching by the content_type `youtube`
default_field | Relevant field | String |  Field to be used when filtering by keywords (like `"Barack Obama"`) and no fields are used in the Query String. Note: This will be deprecated on the 01-06-2017, please switch to `default_fields` by then
default_fields | [<code style="white-space:nowrap">"headline"</code>, <code style="white-space:nowrap">"summary"</code>, <code style="white-space:nowrap">"authors"</code>] | Array[String] | Up to 3 available fields to be used filtering by keywords (like `"Barack Obama"`) and no fields are used in the Query String
size | 200 | Integer | Max number of articles to be returned (includes relatedStories)
find_related | true | Boolean | Related stories will be collapsed when set. Ignored when searching by the content_type `youtube`
content_type | stories | String | Filters by `stories` or `youtube`


### Available fields for filtering Articles/Stats request

Field | Type
----- | ----
headline |  
summary |  
authors |  
<del>country</del> | Number. Deprecated: use country_code instead
country_code | Two letter (lower case) ISO 3166 country code
region_code | Available regions (lower case): `na`, `eu`, `oc`, `sea`, `sa`, `as`, `me`, `af`
language | [Two letter ISO 639-1 language code](#supported-languages)
categories | Number
publisher | TLD such as newswhip.com
domain | Exact domain where the article was published. i.e. blog.newswhip.com
href | 
siteStructure| Handy for articles that followes a particular path on a site, e.g: to look for all articles with url follows "http://www.complex.com/tag/politics", use filter with `publisher:complex.com AND siteStructure:\\/tags\\/politics` or `publisher:complex.com AND siteStructure:"/tags/politics"` will be sufficient(check the note down below regarding researved characters)

<aside class="notice">Special characters (+ - && || ! ( ) { } [ ] ^ " ~ * ? : \ /)  are reserved for lucene query string, you’ll need to escape them with \\\\ before the character, i.e: f-150 should be wrapped up as f\\\\-150, or wrapped inside double quotes as `"f-150"` </aside>
<aside class="notice">Due to historical reasons, the query able fields `headline` and `summary` differ in naming from their `Article` counterparts `link` and `excerpt`.</aside>



## POST /v1/fbPost

> Get all facebook posts from Donald J. Trump's fb page that of content-type status and sort by the number of likes

``` shell
curl --request POST \
  --url 'https://api.newswhip.com/api/v1/fbPosts?key=YOUR_API_KEY' \
  --header 'content-type: application/json' \
  --data '{"filters": ["country_code:us"],  "sort_by":"fb_likes", "content_type":"Status"}'
```

```php
<?php
require 'vendor/autoload.php';
use GuzzleHttp\Client;

$client = new Client();
$response = $client->post('https://api.newswhip.com/v1/fbPosts?key=YOUR_API_KEY', [
    'headers' => ['Content-Type' => 'application/json'],

    'body' => '{
        "filters": [
            "page_id:153080620724"
        ],
        "sort_by": "fb_likes",
        "content_type": "status"
    }']);
echo $response->getBody();
?>
```

```json
{
  "fbPosts": [
    {
      "page_id": "153080620724",
      "page_name": "DonaldTrump",
      "post_type": "Status",
      "is_live_video": false,
      "fb_story": "",
      "fb_sponsor_tags": [],
      "fb_data": {
        "total_engagement_count": 26781,
        "total_count_delta": 72,
        "delta_period": 283,
        "delta_period_unit": "m",
        "reactions": {
          "comments": 2777,
          "likes": 21030,
          "shares": 854,
          "loves": 1575,
          "wows": 56,
          "hahas": 407,
          "sads": 11,
          "angrys": 71
        }
      },
      "uuid": "91d47480-12e5-11e7-9384-d37f0d6d833b",
      "publication_timestamp": 1490616000000,
      "link": "https://www.facebook.com/153080620724/posts/10158861256115725",
      "headline": "",
      "excerpt": "President Donald J. Trump's tentative schedule for Monday, March 27th:\nReceives daily intelligence briefing\nParticipates in a roundtable with women small business owners\nSigns bills",
      "keywords": "",
      "source": {
        "publisher": "",
        "link": "http://",
        "country": "United States",
        "country_code": "us"
      },
      "image_link": "",
      "has_video": false,
      "nw_score": 3.6609456724297877,
      "max_nw_score": 4590.83356759275,
      "topics": [
        {
          "id": 2,
          "name": "News"
        },
        {
          "id": 20,
          "name": "Politics"
        },
        {
          "id": 751,
          "name": "US Election 2016"
        }
      ]
    }
  ]
}
```

`POST /v1/fbPosts`

This endpoint retrieves articles from Facebook matching your filters.

### Parameters

* Facebook posts are filtered and sorted using the following `JSON` encoded parameters
* Required fields are denoted *
* Filtering by category or country requires ids which can be found here: [NewsWhip API Coverage](https://www.newswhip.com/coverage/)


Parameter | Default | Type | Description
--------- | ------- | ---- | -----------
filters* |  | Array[String] | Up to 10 [Lucene QueryString](https://lucene.apache.org/core/5_5_2/queryparser/org/apache/lucene/queryparser/classic/package-summary.html#package_description) filters to be applied to the fbPosts. Each fitler allowes up to 150 terms where calculation is based on lucene query string semantics, e.g: `country_code:us` counts as 1 Term, `country_code:(us AND uk)` counts as 2 Terms, `headline: “The Right Way”` counts as 3 terms". See available fields for filtering down below
from | A week ago | Unix timestamp in milliseconds | Filters articles published after `{from}`
to | Now | Unix timestamp in milliseconds | Filters articles published before `{to}`
language | Any | Two letter ISO 639-1 language code | See availalbe languages <a href="#supported-languages">here</a>
default_fields | [ <code style="white-space:nowrap">`page_id`</code>, <code style="white-space:nowrap">`page_name`</code>, <code style="white-space:nowrap">`external_link`</code>] | Array[String] |Up to 3 available fields to be used when filtering by keywords (like `"Barack Obama"`) and no fields are used in the Query String
size | 200 | Integer | Max number of articles to be returned (includes relatedStories.)
content_type| | String | `video`, `live_video`, `link`, `photo`, `status`, `branded_content`, `event`
sort_by | default | String | `default`, `fb_total_engagement`, `fb_likes`, `fb_shares`, `fb_comments`, `fb_loves`, `fb_wows`, `fb_hahas`, `fb_sads`, `fb_angrys`

### Available fields for filtering Facebook Posts

Field | Type
----- | ----
language | String
country_code | Two letter (lower case) ISO 3166 country code
region_code | Available regions (lower case): `na`, `eu`, `oc`, `sea`, `sa`, `as`, `me`, `af`
authors | String
page_id | Facebook page id
page_name | Facebook page username, usually the one come after ‘@’
external_link | The href shared inside facebook post
fb_story | String
fb_sponsor_tags.id | String
fb_sponsor_tags.name | String

<aside class="notice">Special characters (+ - && || ! ( ) { } [ ] ^ " ~ * ? : \ /)  are reserved for lucene query string, you’ll need to escape them with \\\\ before the character, i.e: f-150 should be wrapped up as f\\\\-150, or wrapped inside double quotes as “f-150” </aside>


## POST /v1/stats

> Get the top English language publishers that create the best performing content on Facebook about `"3d printing"` since a week ago

``` shell
curl -H "Content-Type: application/json" -X POST -d '{
    "filters": [
        "3d printing"
    ],
    "language" : "en",
    "sort_by" : "fb_total.sum",
    "aggregate_by" : "domain"
}' "https://api.newswhip.com/v1/stats?key=YOUR_API_KEY"
```

```php
<?php
require 'vendor/autoload.php';
use GuzzleHttp\Client;

$client = new Client();
$response = $client->post('https://api.newswhip.com/v1/stats?key=YOUR_API_KEY', [
    'headers' => ['Content-Type' => 'application/json'],
    'body' => '{
        "filters": [
            "3d printing"
        ],
        "language" : "en",
        "sort_by" : "fb_total.sum",
        "aggregate_by" : "domain"
    }']);
echo $response->getBody();
?>
```

```json
[
  {
    "key": "geek.com",
    "stats": {
      "fb_total": {
        "count": 3,
        "min": 56,
        "max": 3839,
        "avg": 1609.3333333333333,
        "sum": 4828,
        "sum_of_squares": 15611546,
        "variance": 2613894.888888889,
        "std_deviation": 1616.7544306074715
      },
      "twitter": {
        "count": 3,
        "min": 90,
        "max": 200,
        "avg": 133.33333333333334,
        "sum": 400,
        "sum_of_squares": 60200,
        "variance": 2288.8888888888882,
        "std_deviation": 47.84233364802441
      },
      "pinterest": {
        "count": 3,
        "min": 0,
        "max": 3,
        "avg": 1,
        "sum": 3,
        "sum_of_squares": 9,
        "variance": 2,
        "std_deviation": 1.4142135623730951
      },
      "linkedin": {
        "count": 3,
        "min": 0,
        "max": 7,
        "avg": 3,
        "sum": 9,
        "sum_of_squares": 53,
        "variance": 8.666666666666666,
        "std_deviation": 2.943920288775949
      }
    },
    "total": 5237
  }
]
```

`POST /v1/stats`

This endpoint retrieves stats for articles matching your filters.

### Parameters

* Article stats are filtered and sorted using the following `JSON` encoded parameters
* Required fields are denoted *
* Filtering by category or country requires ids which can be found here: [NewsWhip API Coverage](https://www.newswhip.com/coverage/)

Parameter | Default | Type | Description
--------- | ------- | ---- | -----------
filters* |  | Array[String] | Up to 10 [Lucene QueryString](https://lucene.apache.org/core/5_5_2/queryparser/org/apache/lucene/queryparser/classic/package-summary.html#package_description) filters to be applied to the articles. Each fitler allowes up to 150 terms where calculation is based on lucene query string semantics, e.g: `country_code:us` counts as 1 Term, `country_code:(us AND uk)` counts as 2 Terms, `headline: “The Right Way”` counts as 3 terms". See available fields for filtering <a href="#available-fields-for-filtering-articles-stats-request">here</a>.
from | A week ago | Unix timestamp in milliseconds | Filters articles published after `{from}`
to | Now | Unix timestamp in milliseconds | Filters articles published before `{to}`
language | Any | Two letter ISO 639-1 language code | See availalbe languages <a href="#supported-languages">here</a>
sort_by* |  | String.{aggregation_name}.{stat_value} | `{aggregation_name}` is one of `fb_total`, `twitter`, `linkedin`, `pinterest` and `{stat_value}` is one of `count`, `min`, `max`, `avg`, `sum`, `sum_of_squares`, `variance`, `std_dev`
aggregate_by* |  | String | Groups all matched stories by any of the following: `publisher`, `domains`, `domain`, `language`, `authors`, `country_code`, `categories`
video_only | false |
default_field | Relevant field | String |  Field to be used when filtering by keywords (like `"Barack Obama"`) and no fields are used in the Query String. Note: This will be deprecated on the 01-06-2017, please switch to `default_fields` by then
default_fields | [`headline`, `summary`, `authors`] | Array[String] |Up to 3 available fields to be used filtering by keywords (like `"Barack Obama"`) and no fields are used in the Query String
size | 200 | Integer | Max number of aggregations to be returned


### Supported languages

Language | Code
-------- | ----
English | en
Spanish | es 
French | fr
German | de
Dutch | nl
Italian | it
Portuguese | pt
Swedish | sv
Finnish | fi 
Norwegian | nb
Japanese | ja
Turkish | tr
Arabic | ar
Armenian | hy
Basque | eu
Bulgarian | bg
Catalan | ca
Chinese | zh
Korean | ko
Czech | cs
Galician | gl
Greek | el
Hindi | hi
Hungarian | hu
Indonesian | id
Irish | ga
Persian | fa
Romanian | ro
Russian | ru
Sorani | ku
Thai | th



# Entities

## Article

Field | Description
--------- | -----------
link |
headline |  
excerpt |  summary for the story
source.publisher |  domain of source publication
source.link |  website of source publication
<del>source.country</del> |  deprecated
source.country_code | country of source publication
nw_score | NewsWhip's current social speed for the story
fb_data | An object describing total and recent Facebook interactions
tw_data | An object describing total and recent Twitter interactions
li_data | An object describing total and recent LinkedIn interactions
tw_creator |  Nullable. Where available, the creator's Twitter handle as supplied through Twitter Cards
uuid |  NewsWhip's unique story identifier
publication_timestamp |  Timestamp representing when the article was published
image_link |  Where available, link to the source's featured image
relatedStories |  List of `Article` related to this story
topics | List of `Topic`
keywords | comma separated string of keywords attributed to this story
has_video | set to `true` when the story has an embedded video

## FacebookPost

Field | Description
--------- | ---------
page_id | Id of Facebook Page
page_name | Name of Facebook Page 
post_type | Type of Post eg. Status
is_live_video | Is content live video
fb_story | is a description generated by facebook about an event eg. when two people become friends
fb_sponsor_tags | facebook sponsors if available
fb_data | An object describing total and recent Facebook interactions
reactions| An object descriping the facebook reactions (comments, likes , shares , loves, wows, hahas, sads, angrys)
uuid | Newswhip's unique story identifier
publication_timestamp | Timestamp representing when the article was published
link | Link of the post
headline | Headline of post
excerpt | Excerpt from post
keywords | Keywords in Article     
source.publisher| Publisher of the original article
source.link | Link to article
source.country | Country of source
source.country_code | Country code of country 
image_link |  Where available, link to the source's featured image
has_video | set to `true` when the story has an embedded video
nw_score |  NewsWhip's current social speed for the story
max_nw_score | Max Newswhip score all time
topics.id | id of topic 
topics.name | Name of topic

## Topic

Field | Description
--------- | -----------
id |  NewsWhip's unique id for this Topic
name |  English name for this topic