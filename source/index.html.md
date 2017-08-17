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

Welcome to the NewsWhip API documentation. The NewsWhip API provides access to real time data trends, aggregate data, statistics, and social numbers for all content we have been tracking since January 1, 2014 - hundreds of millions of stories, fully categorised and ranked.

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

By default, API keys have limits of 100 API requests per 5 minutes. Once you exceed this limit, calls will return:

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

There are 5 different endpoints:

* `GET /v1/region/{region}/{category}/{time_period}`
* `GET /v1/publisher/{publisher}/{time_period}`
* `GET /v1/local/{city}/All/{time_period}`
* `GET /v1/search?q={search_term}`
* `GET /v1/trendingEntities?timeRange{time in hours}&q={search_term}`

All region, publisher, local and search endpoints support the following Query Parameters:

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
video_only | false | If set to true, the result will ONLY include content with embedded video.
sort_by | default | Sorts articles in descending order. Accepts one of the following: `default`, `fb_total_engagement`, `twitter`, `linkedin`, `fb_tw_and_li`, `nw_score`, `nw_max_score`, `predicted_interactions`
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

``` json
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

## GET /v1/trendingEntities 

> Get the top entities that have become trending in the last x hours

``` shell
curl "https://api.newswhip.com/v1/trendingEntities?timeRange=24&q=Sports&key=YOUR_API_KEY"
```

``` php
<?php

$request = new HttpRequest();
$request->setUrl('https://api.newswhip.com/v1/trendingEntities');
$request->setMethod(HTTP_METH_GET);

$request->setQueryData(array(
  'timeRange' => '24',
  'q' => 'Sports',
  'key' => 'T4hC9wTT7p83C'
));

$request->setContentType('application/x-www-form-urlencoded');
$request->setPostFields(null);

try {
  $response = $request->send();

  echo $response->getBody();
} catch (HttpException $ex) {
  echo $ex;
}
?>
```

```json
{
  "trendingEntities": [
    "Nicky Hayden",
    "Mike Greenberg",
    "Game",
    "Rohit Sharma",
    "Ariana Grande",
    "Nashville Predators",
    "Cris Cyborg",
    "Anaheim Ducks",
    "BCCI",
    "Los Angeles Lakers",
    "RBI",
    "FA",
    "World Series",
    "Petco Park",
    "Dray Day"
  ]
}
```

`GET /v1/trendingEntities`

This endpoint gets the trending entities over a certain {time in hours}. A trending entity is a an entity that has become popular that wasn't popular before.

### Parameters

* All parameters for trending entities are optional

Parameter | Description
--------- | -----------
search-term | Matches all trending entities related to the given `{search_term}`.
time-in-hours | Searches for trending entities over the given number of hours (default=24)


# POST Requests

The POST API endpoints are designed for increased flexibility and are much more powerful. With these server-side only endpoints, your application gets full access to NewsWhip's database, including all content published within the last 6 months from any publisher in any supported language. Filtered, sorted and aggregated by any field you want.

There are 2 different endpoints:

* `POST /v1/articles` - provides stories(web articles, youtube post) matching the query provided
* `POST /v1/fbPosts` - provides Facebook posts matching the query provided 
* `POST /v1/stats` - provides stats on the content matching the query provided


## POST /v1/articles

> Get the top trending stories published in the United States or the United Kingdom that have Rihanna in the headline and are not published in youtube.com over the last 7 days

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


`POST /v1/articles`

This endpoint retrieves all articles matching the filters provided.

### Query Parameters

* Stories are filtered and sorted using the following `JSON` encoded parameters
* Required fields are denoted *
* Filtering by category or country requires country_ids. These are found here: [NewsWhip API Coverage](https://www.newswhip.com/coverage/)

Parameter | Default | Type | Description
--------- | ------- | ---- | -----------
filters* |  | Array[String] | Up to 20 [Lucene QueryString](https://lucene.apache.org/core/5_5_2/queryparser/org/apache/lucene/queryparser/classic/package-summary.html#package_description) filters are allowed to be applied to the articles. Each filter allows up to 150 terms where calculation is based on lucene query string semantics, e.g: `country_code:us` counts as 1 Term, `country_code:(us AND uk)` counts as 2 Terms, `headline: “The Right Way”` counts as 3 terms". See available fields for filtering down below
from | A week ago | Unix timestamp in milliseconds | Filters articles published after `{from}`
to | Now | Unix timestamp in milliseconds | Filters articles published before `{to}`
language | Any | Two letter ISO 639-1 language code | See available languages <a href="#supported-languages">here</a>
sort_by |`default` | String | Sorts one of the following in descending order: `default`, `fb_total_engagement`, `fb_tw_overperforming`, `fb_overperforming`, `tw_overperforming`, `predicted_interactions`, `twitter`, `linkedin`, `fb_tw_and_li`, `nw_score`(deprecated on the 01-06-2017), `nw_max_score`, `created_at`. (The `default` sort_by is `nw_max_score` when the selected time-range is <= 25h, otherwise it will be `fb_tw_overperforming`)
sort_by (Youtube) | `created_at` | String |  When searching by the content_type `youtube`, sort in descending order by `yt_likes`, `yt_views`, `yt_comments`, `yt_dislikes`, `fb_total_engagement`, `twitter`, `created_at`
video_only | false | Boolean | Ignored when searching by the content_type `youtube`
default_field | Relevant field | String |  Field to be used when filtering by keywords (like `"Barack Obama"`) and no fields are used in the Query String. Note: This will be deprecated on the 01-06-2017, please switch to `default_fields` by then
default_fields | [<code style="white-space:nowrap">"headline"</code>, <code style="white-space:nowrap">"summary"</code>, <code style="white-space:nowrap">"authors"</code>] | Array[String] | Up to 3 available fields to be used filtering by keywords (like `"Barack Obama"`) and no fields are used in the Query String
size | 200 | Integer | Max number of articles to be returned (includes relatedStories)
find_related | true | Boolean | Related stories will be collapsed when set. Ignored when searching by the content_type `youtube`
content_type | stories | String | Filters by `stories` or `youtube`


### Available fields for filtering Articles/Stats/TrendingEntities request

Field | Type
----- | ----
headline | String
summary | String
authors | String 
<del>country</del> | Number. Deprecated: use country_code instead
country_code | Two letter (lower case) ISO 3166 country code
region_code | Available regions (lower case): `na`, `eu`, `oc`, `sea`, `sa`, `as`, `me`, `af`
language | [Two letter ISO 639-1 language code](#supported-languages)
categories | Number
publisher | TLD such as newswhip.com
domain | Exact domain where the article was published. i.e. blog.newswhip.com
href | Search by the full url of the article eg. "href:\"https://www.coldwellbankerhomes.com/az/concho/669-county-road-8235-stanford/pid_18337473/\""
siteStructure| Handy for articles that follows a particular path on a site, e.g: to look for all articles with url follows "http://www.complex.com/tag/politics", use filter with `publisher:complex.com AND siteStructure:\\/tags\\/politics` or `publisher:complex.com AND siteStructure:"/tags/politics"` will be sufficient(check the note down below regarding reserved characters)

<aside class="notice">Special characters (+ - && || ! ( ) { } [ ] ^ " ~ * ? : \ /)  are reserved for lucene query string, you’ll need to escape them with \\\\ before the character, i.e: f-150 should be wrapped up as f\\\\-150, or wrapped inside double quotes as "f-150", however please note that "" will replace the special characters inside with empty space, so f\\\\-150 will be counted as 1 term while “f-150” is counted as 2 terms </aside>
<aside class="notice">Due to historical reasons, the queryable fields `headline` and `summary` differ in naming from their `Article` counterparts `link` and `excerpt`.</aside>



## POST /v1/fbPosts

> Get all Facebook posts from Donald J. Trump's fb page that of content-type status and sort by the number of likes

``` shell
curl --request POST \
  --url 'https://api.newswhip.com/v1/fbPosts?key=YOUR_API_KEY' \
  --header 'content-type: application/json' \
  --data '{"filters": ["country_code:us"],  "sort_by":"fb_likes", "content_type":"Status"}'
```

``` php
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
filters* |  | Array[String] | Up to 20 [Lucene QueryString](https://lucene.apache.org/core/5_5_2/queryparser/org/apache/lucene/queryparser/classic/package-summary.html#package_description) filters to be applied to the fbPosts. Each filter allows up to 150 terms where calculation is based on lucene query string semantics, e.g: `country_code:us` counts as 1 Term, `country_code:(us AND uk)` counts as 2 Terms, `headline: “The Right Way”` counts as 3 terms". See available fields for filtering down below
from | A week ago | Unix timestamp in milliseconds | Filters articles published after `{from}`
to | Now | Unix timestamp in milliseconds | Filters articles published before `{to}`
language | Any | Two letter ISO 639-1 language code | See available languages <a href="#supported-languages">here</a>
default_fields | [ <code style="white-space:nowrap">`page_name`</code>, <code style="white-space:nowrap">`external_link`</code>] | Array[String] |Up to 3 available fields to be used when filtering by keywords (like `"Barack Obama"`) and no fields are used in the Query String
size | 200 | Integer | Max number of articles to be returned (includes relatedStories.)
content_type| | String | `video`, `live_video`, `link`, `photo`, `status`, `branded_content`, `event`
sort_by | `default` | String | Sorts by the following in descending order`default`,`nw_max_score`,`fb_overperforming`, `fb_total_engagement`, `created_at` `fb_likes`, `fb_shares`, `fb_comments`, `fb_loves`, `fb_wows`, `fb_hahas`, `fb_sads`, `fb_angrys`.(The `default` sort_by is `nw_max score` when the selected time-range is <= 25h, otherwise it will be `fb_overperforming`)

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

<aside class="notice">Special characters (+ - && || ! ( ) { } [ ] ^ " ~ * ? : \ /)  are reserved for lucene query string, you’ll need to escape them with \\\\ before the character, i.e: f-150 should be wrapped up as f\\\\-150, or wrapped inside double quotes as “f-150”, however please note that "" will replace the special characters inside with empty space, so f\\\\-150 will be counted as 1 term while “f-150” is counted as 2 terms</aside>


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
filters* |  | Array[String] | Up to 20 [Lucene QueryString](https://lucene.apache.org/core/5_5_2/queryparser/org/apache/lucene/queryparser/classic/package-summary.html#package_description) filters are allowed to be applied to the articles. Each filter allows up to 150 terms where calculation is based on lucene query string semantics, e.g: `country_code:us` counts as 1 Term, `country_code:(us AND uk)` counts as 2 Terms, `headline: “The Right Way”` counts as 3 terms". See available fields for filtering <a href="#available-fields-for-filtering-articles-stats-request">here</a>.
from | A week ago | Unix timestamp in milliseconds | Filters articles published after `{from}`
to | Now | Unix timestamp in milliseconds | Filters articles published before `{to}`
language | Any | Two letter ISO 639-1 language code | See available languages <a href="#supported-languages">here</a>
sort_by |`default` | String | One of the following in descending order: `default`, `fb_total_engagement`, `fb_tw_overperforming`, `fb_overperforming`, `tw_overperforming`, `predicted_interactions`, `twitter`, `linkedin`, `fb_tw_and_li`, `nw_score`(deprecated on the 01-06-2017), `nw_max_score`, `created_at`. (The `default` sort_by is `nw_max_score` when the selected time-range is <= 25h, otherwise it will be `fb_tw_overperforming`)
sort_by (Youtube) | `created_at` | String |  When searching by the content_type `youtube`, sort by `yt_likes`, `yt_views`, `yt_comments`, `yt_dislikes`, `fb_total_engagement`, `twitter`, `created_at`
video_only | false | Boolean | Ignored when searching by the content_type `youtube`
default_field | Relevant field | String |  Field to be used when filtering by keywords (like `"Barack Obama"`) and no fields are used in the Query String. Note: This will be deprecated on the 01-06-2017, please switch to `default_fields` by then
default_fields | [<code style="white-space:nowrap">"headline"</code>, <code style="white-space:nowrap">"summary"</code>, <code style="white-space:nowrap">"authors"</code>] | Array[String] | Up to 3 available fields to be used filtering by keywords (like `"Barack Obama"`) and no fields are used in the Query String
size | 200 | Integer | Max number of articles to be returned (includes relatedStories)
find_related | true | Boolean | Related stories will be collapsed when set. Ignored when searching by the content_type `youtube`
content_type | stories | String | Filters by `stories` or `youtube`



## POST /v1/trendingEntities

> Get the top entities that have become trending in the last x hours


``` shell
curl -X POST \
  'http://api.newswhip.com/v1/trendingEntities?key=YOUR_API_KEY' \
  -H 'content-type: application/json' \
  -d '{
   "filters": [],
 "from":1481932800000,
 "to":1494975600000
}'
```

```php
<?php

$request = new HttpRequest();
$request->setUrl('http://st:9000/api/v1/trendingEntities');
$request->setMethod(HTTP_METH_POST);

$request->setQueryData(array(
  'key' => 'YOUR_API_KEY'
));

$request->setBody('{
   "filters": [],
 "from":1481932800000,
 "to":1494975600000
}');

try {
  $response = $request->send();

  echo $response->getBody();
} catch (HttpException $ex) {
  echo $ex;
}
?>
```

```json
{
  "trendingEntities": [
    "Donald Trump",
    "Barack Obama",
    "U.S",
    "Republican",
    "US",
    "FBI",
    "James Comey",
    "Democrats",
    "Manchester United",
    "Premier League",
    "IPL",
    "Sean Spicer",
    "House",
    "UK",
    "CNN"
  ]
}
```

`POST /v1/trendingEntities`

This endpoint gets the trending entity over a certain {time in hours}. A trending entity is a an entity that has become popular that wasn't popular before.

### Parameters

* Article stats are filtered and sorted using the following `JSON` encoded parameters
* Required fields are denoted *
* Filtering by category or country requires ids which can be found here: [NewsWhip API Coverage](https://www.newswhip.com/coverage/)
* As the trendingEntities is aggregating a large about of data it can take up to 5 seconds to return.
* The max number of trending entities returned is 15 but it can be less if you search is more specific


Parameter | Default | Type | Description
--------- | ------- | ---- | -----------
filters* |  | Array[String] | publisher, categories, headline, countryCode
from | A week ago | Unix timestamp in milliseconds | Filters articles published after `{from}`
to | Now | Unix timestamp in milliseconds | Filters articles published before `{to}`



## POST /v1/twitterInfluencers

> Get the top Influencers on twitter for a particular query


``` shell
curl -X POST \
  'http://api.newswhip.com/v1/twitterInfluencers?key=TESTKEY123' \
  -H 'cache-control: no-cache' \
  -H 'content-type: application/json' \
  -d '{
"filters":["countryCode:us"],
"size":250
}'
```

```php
<?php

$request = new HttpRequest();
$request->setUrl('http://api.newswhip.com/v1/twitterInfluencers');
$request->setMethod(HTTP_METH_POST);

$request->setQueryData(array(
  'key' => 'TESTKEY123'
));

$request->setHeaders(array(
  'cache-control' => 'no-cache',
  'content-type' => 'application/json'
));

$request->setBody('{
"filters":["countryCode:us"],
"size":250
}');

try {
  $response = $request->send();

  echo $response->getBody();
} catch (HttpException $ex) {
  echo $ex;
}
?>
```

```json
{
    "twitterInfluencers": [
        {
            "twitter_id": 19394188,
            "twitter_handle": "SenJohnMcCain",
            "likes_count": 44,
            "followers_count": 2439704,
            "following_count": 378,
            "statuses_count": 13287,
            "max_retweet_value": 37562,
            "social_referrals": [
                {
                    "article_id": "207d6140-7fb7-11e7-b89c-b3951ad1b925",
                    "twitter_url": "https://twitter.com/any/status/896515795114766337",
                    "favourite_count": 102465,
                    "rt_count": 37562,
                    "created_at": 1502580996000,
                    "description": "Washington, D.C. – U.S. Senator John McCain (R-AZ) released the following statement today on the white supremacist attack in Charlottesville, Virginia:",
                    "article_url": "https://www.mccain.senate.gov/public/index.cfm?p=press-releases&id=64ED6753-345F-4F64-9B64-2D8BDAE952B5"
                }
            ]
        },
        {
            "twitter_id": 592730371,
            "twitter_handle": "JackPosobiec",
            "likes_count": 42372,
            "followers_count": 184577,
            "following_count": 716,
            "statuses_count": 100483,
            "max_retweet_value": 26625,
            "social_referrals": [
                {
                    "article_id": "c12fb330-80ee-11e7-b89c-b3951ad1b925",
                    "twitter_url": "https://twitter.com/any/status/897107711434915842",
                    "favourite_count": 51500,
                    "rt_count": 26625,
                    "created_at": 1502722120000,
                    "description": "Nine people were killed and at least 30 others were wounded in shootings across Chicago between Friday night and Monday morning.",
                    "article_url": "http://abc7chicago.com/2305976/"
                }        ]
    }
  ]
```

`POST /v1/twitterInfluencers`

This endpoint show the twitter uses that have the most influence on stories related to your search.

### Parameters

* Twitter Influencer are filtered and sorted using the following `JSON` encoded parameters
* Required fields are denoted *
* Filtering by category or country requires ids which can be found here: [NewsWhip API Coverage](https://www.newswhip.com/coverage/)
* As the twitterInfluencers is aggregating a large about of data it can take up to 5 seconds to return.
* If a query String is passed into the filter it will search on headline, authors and summary.
* The results are sorted number of retweets


Parameter | Default | Type | Description
--------- | ------- | ---- | -----------
filters* |  | Array[String] | Can use the following filters publisher, categories, countryCode, headline, summary, region_code, language, domain
from | A week ago | Unix timestamp in milliseconds | Filters articles published after `{from}`
to | Now | Unix timestamp in milliseconds | Filters articles published before `{to}`
language | | String
size | 200 | number | Number of influencer to return (max 500)

## POST /v1/fbInfluencers

> Get the top Facebook influencer for a particular query.


``` shell
curl -X POST \
  'http://api.newswhip.com/v1/fbInfluencers?key=TESTKEY123' \
  -H 'cache-control: no-cache' \
  -H 'content-type: application/json' \
  -d '{
"filters":[]
}'
```

```php
<?php

$request = new HttpRequest();
$request->setUrl('http://api.newswhip.com/v1/fbInfluencers');
$request->setMethod(HTTP_METH_POST);

$request->setQueryData(array(
  'key' => 'TESTKEY123'
));

$request->setHeaders(array(
  'cache-control' => 'no-cache',
  'content-type' => 'application/json'
));

$request->setBody('{
"filters":[]
}');

try {
  $response = $request->send();

  echo $response->getBody();
} catch (HttpException $ex) {
  echo $ex;
}
?>
```

```json
{
    "fbInfluencers": [
        {
            "fb_page_id": 15704546335,
            "fb_username": "FoxNews",
            "about": "Welcome to the official Fox News facebook page.  Get breaking news, must see videos and exclusive interviews from the #1 name in news.",
            "followers_count": 15634977,
            "likes_count": 15634977,
            "profile_image": "https://scontent.xx.fbcdn.net/v/t1.0-1/p50x50/417751_10150581617531336_1949382366_n.jpg?oh=be1fa613ac8f3c553749f213e5c2351a&oe=5A197086",
            "max_fb_interactions": 587652,
            "social_referrals": [
                {
                    "article_id": "27aeb210-8170-11e7-9a30-c9dd3e4cb15e",
                    "fb_post_id": "15704546335_10155823554046336",
                    "headline": "Iowa State Fair cow and boy taking nap wins the internet after photo goes viral",
                    "description": "This here is a little story about a boy and his cow.",
                    "fb_total_interactions": 587652,
                    "created_at": 1502816913000,
                    "article_url": "http://www.foxnews.com/us/2017/08/14/iowa-state-fair-cow-and-boy-taking-nap-wins-internet-after-photo-goes-viral.html"
                },
                {
                    "article_id": "876a2d60-82ba-11e7-8b54-9f4c7b0f94de",
                    "fb_post_id": "15704546335_10155831874366336",
                    "headline": "Gettysburg Stands Firm: Battlefield Says All Monuments Staying Put",
                    "description": "Officials at the Gettysburg National Military Park said Wednesday that the monuments at the expansive Pennsylvania battlefield will stay despite unrest over Confederate memorials.",
                    "fb_total_interactions": 97525,
                    "created_at": 1502931295000,
                    "article_url": "http://insider.foxnews.com/2017/08/16/gettysburg-confederate-monuments-not-moving-battlefield-says-pennsylvania-union"
                }
        ]
    },
    {
            "fb_page_id": 9124187907,
            "fb_username": "senatorsanders",
            "about": "Sen. Bernie Sanders of Vermont is the longest serving independent in U.S. congressional history.",
            "followers_count": 7371777,
            "likes_count": 7371777,
            "profile_image": "https://scontent.xx.fbcdn.net/v/t1.0-1/c20.0.50.50/p50x50/400832_10151148541197908_1621512611_n.jpg?oh=1d45b3c211e83e5925b08bde7b25ca68&oe=59F0258C",
            "max_fb_interactions": 311430,
            "social_referrals": [
                {
                    "article_id": "f2cff040-7fa3-11e7-927a-ebb7ea9adb61",
                    "fb_post_id": "9124187907_10156228952697908",
                    "headline": "Trump blames 'many sides' after violent white supremacist rally in Virginia",
                    "description": "President Donald Trump on Saturday blamed \"many sides\" for the violent clashes between protesters and white supremacists in Charlottesville, Virginia.",
                    "fb_total_interactions": 311430,
                    "created_at": 1502573718000,
                    "article_url": "http://www.chicagotribune.com/news/nationworld/politics/ct-trump-charlottesville-violence-20170812-story.html"
                }
]
```

`POST /v1/fbInfluencers`

This endpoint show the Facebook users that have the most influence on stories related to your search.

### Parameters

* Facebook Influencer are filtered and sorted using the following `JSON` encoded parameters
* Required fields are denoted *
* Filtering by category or country requires ids which can be found here: [NewsWhip API Coverage](https://www.newswhip.com/coverage/)
* As the fbInfluencers is aggregating a large about of data it can take up to 5 seconds to return.
* If a query String is passed into the filter it will search on headline, authors and summary.
* The results are sorted total number of Facebook interactions


Parameter | Default | Type | Description
--------- | ------- | ---- | -----------
filters* |  | Array[String] | Can use the following filters publisher, categories, countryCode, headline, summary, region_code, language, domain
from | A week ago | Unix timestamp in milliseconds | Filters articles published after `{from}`
to | Now | Unix timestamp in milliseconds | Filters articles published before `{to}`
language | | String
size | 200 | number | Number of influencer to return (max 500)

# Entities

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
fb_data | Facebook interactions data (total_engagement_count, total_count_delta, delta_period, delta_period_unit, fb_overperforming,reactions)
tw_data | Twitter Interactions (tw_count, total_count_delta, delta_period, delta_period_unit, tw_overperforming)
li_data |LinkedIn interactions (li_count, total_count_delta, delta_period, delta_period_unit)
predicted_interactions | How many interactions are expected on the article based on current velocity
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
fb_story | is a description generated by Facebook about an event eg. when two people become friends
fb_sponsor_tags | Facebook sponsors if available
fb_data | Facebook interactions data (total_engagement_count, total_count_delta, delta_period, delta_period_unit, fb_overperforming,reactions)
reactions| An object describing the Facebook reactions (comments, likes , shares , loves, wows, hahas, sads, angrys)
uuid | Newswhip's unique story identifier
publication_timestamp | Timestamp representing when the article was published
link | Link of the post
headline | Headline of post
excerpt | Excerpt from post
keywords | Keywords in Article     
source.publisher| Publisher of the original article
source.link | Link to article
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

## TwitterInfluencer
Field | Description
--------- | -----------
twitter_id | twitter id of the influencer
twitter_handle | The twitter handle of the influencer
likes_count | Number of likes this user has
followers_count | Number of followers this user has
following_count | Number of accounts this user is following
statuses_count | Number of statuses this user has posted
max_retweet_value | The number of retweets on this uses most influenced article
social_referrals | List of the social referrals of a user

## Social Referral (Twitter)
Field | Description
--------- | -----------    
article_id | id of the article
twitter_url | URl of the Twitter post
favourite_count | The number of favorites this user has
rt_count | The number of times the user has retweeted
created_at | The date the article was created at
description | Description of the article
article_url | The original URL of the article

## FacebookInfluencer
Field | Description
--------- | -----------
fb_page_id | The Facebook page id of the influencer
fb_username | The Facebook username of the influencer
about | The description on the Facebook page of the influencer
followers_count | The number of users following this user on Facebook
likes_count | The number of likes this user has on Facebook
profile_image | The URL of the users profile picture
max_fb_interactions | The number of interaction on the users most influenced stories
social_referrals | The list of articles that this user has influenced

## Social Referral (Facebook)
Field | Description
--------- | -----------
article_id | id of the article
fb_post_id | Facebook Post Id
headline | The headline of the article
description | A description of the article
fb_total_interactions | The total number of interactions on the Facebook post
created_at | Unix timestamp for the time the article was posted
article_url | The URL of the article influenced by the influencer






