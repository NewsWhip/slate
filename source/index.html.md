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

For details on getting access, please email: [api@newswhip.com](mailto:api@newswhip.com).

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
      "recent_fb_counts": 9820,
      "recent_tw_counts": 40,
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

There are 3 different endpoints:

* `POST /v1/articles` - provides stories(web articles, youtube post) by matching it against a set of filters
* `POST /v1/fbPosts` - provides facebook posts by matching it against a set of filters
* `POST /v1/stats` - provides stats on the content matching the filters provided

## POST /v1/articles

> Get the top trending stories published in United States or United Kingdom that talk about Rihanna not published in youtube.com since a week ago

``` shell
curl -H "Content-Type: application/json" -X POST -d '{
    "filters": ["(country_code:us OR country_code:gb) AND -publisher:youtube.com AND headline:rihanna"],
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
            "(country_code:us OR country_code:gb) AND -publisher:youtube.com AND headline:rihanna"
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
      "recent_fb_counts": 3,
      "recent_tw_counts": 0,
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

> Get the top trending Facebook posts published in United States or United Kingdom that talk about Rihanna not published in youtube.com since a week ago

``` shell
curl -H "Content-Type: application/json" -X POST -d '{
    "filters": ["(country_code:us OR country_code:gb) AND -publisher:youtube.com AND headline:rihanna"],
    "language": "en",
    "video_only":false,
    "sort_by": "nw_max_score",
    "find_related": false,
    "size": 1,
    "content_type": "fb_posts"
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
            "(country_code:us OR country_code:gb) AND -publisher:youtube.com AND headline:rihanna"
        ],
        "language": "en",
        "video_only":false,
        "sort_by": "nw_max_score",
        "find_related": false,
        "size": 1,
        "content_type": "fb_posts"
    }']);
echo $response->getBody();
?>
```

```json
{
  "articles": [
    {
      "link": "https://www.facebook.com/10092511675/posts/10154185324896676",
      "headline": "Rihanna's cover photo",
      "excerpt": "",
      "keywords": "",
      "source": {
        "publisher": "",
        "link": "http://",
        "country": "United States",
        "country_code": "us"
      },
      "nw_score": 1.632236314298637,
      "max_nw_score": 5046.852808216844,
      "fb_data": {
        "total_engagement_count": 24808,
        "total_count_delta": 42,
        "delta_period": 453,
        "delta_period_unit": "m",
        "reactions": {
          "comments": 449,
          "likes": 20772,
          "shares": 280,
          "loves": 3169,
          "wows": 100,
          "hahas": 26,
          "sads": 5,
          "angrys": 7
        }
      },
      "fb_post": {
        "post_type": "Photo",
        "page_name": "Rihanna",
        "category": ""
      },
      "tw_data": {
        "tw_count": 0,
        "total_count_delta": 0,
        "delta_period": 453,
        "delta_period_unit": "m"
      },
      "li_data": {
        "li_count": 0,
        "total_count_delta": 0,
        "delta_period": 453,
        "delta_period_unit": "m"
      },
      "tw_creator": "",
      "delta_time": 453,
      "recent_fb_counts": 42,
      "recent_tw_counts": 0,
      "uuid": "3f0bea00-adda-11e6-9b4e-dd9ee0636270",
      "publication_timestamp": 1479506348000,
      "image_link": "https://scontent.xx.fbcdn.net/v/t1.0-9/q81/s720x720/15073550_10154185324731676_7190497282078870243_n.jpg?oh=e399b348b5f0242da43d363343cacd0b&oe=58C338AC",
      "relatedStories": [],
      "topics": [
        {
          "id": 3,
          "name": "Entertainment"
        },
        {
          "id": 4,
          "name": "Culture"
        },
        {
          "id": 9,
          "name": "Music"
        },
        {
          "id": 699,
          "name": "Celebrity"
        }
      ],
      "has_video": false
    }
  ]
}
```

`POST /v1/articles`

This endpoint retrieves all articles matching the filters provided.

### Parameters

* Stories are filtered and sorted using the following `JSON` encoded parameters.
* Required fields are denoted *.
* Filtering by category or country requires ids which can be found here: [NewsWhip API](http://www.newswhip.com/api#regions-covered)

Parameter | Default | Type | Description
--------- | ------- | ---- | -----------
filters* |  | Array[String] | List of [Lucene QueryString](https://lucene.apache.org/core/4_10_2/queryparser/org/apache/lucene/queryparser/classic/package-summary.html#package_description) filters to be applied to the articles. See available fields for filtering below.
from | A week ago | Unix timestamp in milliseconds | Filters articles published after `{from}`.
to | Now | Unix timestamp in milliseconds | Filters articles published before `{to}`.
language | Any | Two letter ISO 639-1 language code |
sort_by | default | String | One of the following: `default`, `fb_total_engagement`, `twitter`, `linkedin`, `fb_tw_and_li`, `nw_score`, `nw_max_score`, `created_at`. When searching by the content_type `fb_posts` it's possible sort by `fb_likes`, `fb_shares`, `fb_comments`, `fb_loves`, `fb_wows`, `fb_hahas`, `fb_sads`, `fb_angrys`.
video_only | false | Boolean |
default_field | Relevant fields | String | Field to be used when filtering by keywords (like `"Barack Obama"`) and no fields are used in the Query String.
size |   | Integer | Max number of articles to be returned (includes relatedStories.)
find_related | true | Boolean | Related stories will be collapsed when set.
content_type | stories | String | Filters by one of the following types: `stories`, `fb_posts`, `youtube`.

### Available fields for filtering

Field | Type
----- | ----
headline |  
summary |  
authors |  
<del>country</del> | Number. Deprecated: use country_code instead
country_code | Two letter (lower case) ISO 3166 country code
region_code | Available regions (lower case): `na`, `eu`, `oc`, `sea`, `sa`, `as`, `me`, `af`
language | Two letter ISO 639-1 language code
categories | Number
publisher | TLD such as newswhip.com
domain | Exact domain where the article was published. i.e. blog.newswhip.com
href |   

<aside class="notice">Due to historical reasons, the queryable fields `headline` and `summary` differ in naming from their `Article` counterparts `link` and `excerpt`.</aside>

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

Stories are filtered and sorted using the following JSON encoded parameters.
Required fields are denoted *. Filtering by category or country requires ids which can be found here: [NewsWhip API](http://www.newswhip.com/api#regions-covered)

Parameter | Default | Type | Description
--------- | ------- | ---- | -----------
filters* |  | Array[String] | List of Lucene QueryString filters to be applied to the articles. See available fields for filtering above.
from | A week ago | Unix timestamp in milliseconds | Filters articles published after {from}.
to | Now | Unix timestamp in milliseconds | Filters articles published before {to}.
language | Any | Two letter ISO 639-1 language code |
sort_by* |  | String.{aggregation_name}.{stat_value} | `{aggregation_name}` is one of `fb_total`, `twitter`, `linkedin`, `pinterest` and `{stat_value}` is one of `count`, `min`, `max`, `avg`, `sum`, `sum_of_squares`, `variance`, `std_dev`.
aggregate_by* |  | String | Groups all matched stories by any of the following: `publisher`, `domains`, `domain`, `language`, `authors`, `country`, `categories`
video_only | false |
default_field | Relevant fields | String | Field to be used when filtering by keywords (like `"Barack Obama"`) and no fields are used in the Query String.
size |   | Integer | Max number of aggregations to be returned.

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

## Topic

Field | Description
--------- | -----------
id |  NewsWhip's unique id for this Topic
name |  English name for this topic
