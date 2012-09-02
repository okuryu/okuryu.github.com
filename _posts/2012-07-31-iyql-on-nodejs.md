---
layout: post
title: iYQL on Node.js
description: Implement Interactive YQL with Node.js.
---

In the past, Diego Souza implemented [iYQL][iyql]. This is command line based
simple [YQL][yql] client. I liked this approach, but its not easy to install
on my machine for me (need install Haskell) and I met a few strange bugs on
my environment for some reason.

Since I just published "iyql" npm module that has features similar to that
one on npmjs.org. And, its open sourced on [my GitHub repository][node-iyql].
Please read just below if you are familiar with Node.js.

### Installation

	$ npm install -g iyql

Note: Currently, depend on Node.js 0.8.x.

### Usage

	$ iyql -h
	Usage: iyql [options]
	
	Options:
	  -p, --endpoint set YQL endpoint URL
	                 default: http://query.yahooapis.com/v1/public/yql
	  -e, --env      set YQL env URL
	  -h, --help     print help
	  -v, --version  print version

You can pass YQL statements into iyql REPL prompt.

	$ iyql
	iyql> desc weather.forecast
	{
	  "query": {
	    "count": 1,
	    "created": "2012-07-30T14:45:14Z",
	    "lang": "en-US",
	    "diagnostics": {
	      "publiclyCallable": "true",
	      "url": {
	        "execution-start-time": "0",
	        "execution-stop-time": "575",
	        "execution-time": "575",
	        "id": "4a00f6a7-0c5d-4d86-877a-c211fa3e88bb",
	        "proxy": "DEFAULT",
	        "content": "http://www.datatables.org/alltables.env"
	      },
	      "user-time": "626",
	      "service-time": "588",
	      "build-version": "29152"
	    },
	    "results": {
	      "table": {
	        "hash": "aae78b1462a6a8fbc748aec4cf292767",
	        "name": "weather.forecast",
	        "security": "ANY",
	        "meta": {
	          "author": "Yahoo! Inc",
	          "description": "Weather forecast table",
	          "documentationURL": "http://developer.yahoo.com/weather/",
	          "sampleQuery":
	            "select * from weather.forecast where woeid=2502265"
	        },
	        "request": {
	          "select": [
	            {
	              "key": [
	                {
	                  "name": "location",
	                  "required": "true",
	                  "type": "xs:string"
	                },
	                {
	                  "name": "u",
	                  "type": "xs:string"
	                }
	              ]
	            },
	            {
	              "key": [
	                {
	                  "name": "woeid",
	                  "required": "true",
	                  "type": "xs:string"
	                },
	                {
	                  "name": "u",
	                  "type": "xs:string"
	                }
	              ]
	            }
	          ]
	        }
	      }
	    }
	  }
	}
	iyql> select * from geo.places where text="hikarigaoka"|truncate(count=1)
	{
	  "query": {
	    "count": 1,
	    "created": "2012-07-30T14:51:20Z",
	    "lang": "en-US",
	    "diagnostics": {
	      "publiclyCallable": "true",
	      "url": [
	        {
	          "execution-start-time": "0",
	          "execution-stop-time": "577",
	          "execution-time": "577",
	          "id": "313d9c69-0140-4b3c-970d-3f5ce33cd66e",
	          "proxy": "DEFAULT",
	          "content": "http://www.datatables.org/alltables.env"
	        },
	        {
	          "execution-start-time": "625",
	          "execution-stop-time": "655",
	          "execution-time": "30",
	          "content":
	            "http://where.yahooapis.com/v1/places.q(hikarigaoka);
	            start=0;count=10"
	        }
	      ],
	      "user-time": "656",
	      "service-time": "618",
	      "build-version": "29152"
	    },
	    "results": {
	      "place": {
	        "lang": "en-US",
	        "uri": "http://where.yahooapis.com/v1/place/28414615",
	        "woeid": "28414615",
	        "placeTypeName": {
	          "code": "10",
	          "content": "Local Administrative Area"
	        },
	        "name": "Hikarigaoka",
	        "country": {
	          "code": "JP",
	          "type": "Country",
	          "content": "Japan"
	        },
	        "admin1": {
	          "code": "JP-13",
	          "type": "Prefecture",
	          "content": "Tokyo Prefecture"
	        },
	        "admin2": {
	          "code": "",
	          "type": "Gun/Ku",
	          "content": "Nerima-ku"
	        },
	        "admin3": null,
	        "locality1": {
	          "type": "Town",
	          "content": "Tokyo"
	        },
	        "locality2": null,
	        "postal": null,
	        "centroid": {
	          "latitude": "35.761822",
	          "longitude": "139.631378"
	        },
	        "boundingBox": {
	          "southWest": {
	            "latitude": "35.753571",
	            "longitude": "139.621826"
	          },
	          "northEast": {
	            "latitude": "35.770081",
	            "longitude": "139.640945"
	          }
	        },
	        "areaRank": "1",
	        "popRank": "0"
	      }
	    }
	  }
	}

This is my experiment implements yet. I would like to enhance more useful
features. So please watch my repository, file a issue on GitHub if you
are interested in this one.

* [node-iyql on GitHub][node-iyql]

[iyql]: https://github.com/dgvncsz0f/iyql
[yql]: http://developer.yahoo.com/yql/
[node-iyql]: https://github.com/okuryu/node-iyql
