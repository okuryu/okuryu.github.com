---
layout: post
title: Using YConnect with Node.js and YQL
description: Introduce examples that uses UserInfo API, supplied by YConnect, from Node.js and YQL.
---

Last November, Yahoo! JAPAN released a product called [YConnect][yconnect].
This is a new authorization system that is compatible with OAuth 2.0 and
OpenID Connect. In OAuth 2.0, the flow is simplified compared to OAuth 1.0,
so it is easy for developers to implement. Furthermore, YConnect anticipates
client-side applications such as native applications and can support many
cases of use. This time, I would like to introduce examples that uses
[UserInfo API][userinfo-api], supplied by YConnect, from Node.js and YQL.

### YConnect with Node.js

First, with Node.js, I have created a npm package for YConnect. You can
install the package via npm command.

	$ npm install yconnect

By passing the access token to access the API, you can retrieve the data.

{% highlight javascript %}
var YConnect = require('yconnect').YConnect;
var yc = new YConnect({
    access_token: '<access token>'
});

yc.getUserInfo({schema: 'openid'}, function (error, data) {
    if (!error) {
        console.log(JSON.parse(data));
    } else {
        console.log(error);
    }
});
{% endhighlight %}

The result just below.

	{ user_id: '43M63NAGMHBAYMXRMY3WODOWS4',
	  name: 'OkumuraRyuichi',
	  given_name: 'Ryuichi',
	  'given_name#ja-Kana-JP': '',
	  'given_name#ja-Hani-JP': 'Ryuichi',
	  family_name: 'Okumura',
	  'family_name#ja-Kana-JP': '',
	  'family_name#ja-Hani-JP': 'Okumura',
	  locale: 'ja-JP',
	  email: 'okuryu@gmail.com',
	  email_verified: true,
	  address:
	   { country: 'jp',
	     postal_code: '1060032',
	     region: 'Tokyo',
	     locality: 'Minato-ku' },
	  birthday: '1984',
	  gender: 'male' }

### YConnect with YQL

Next is YQL. In the same way, I have created a table for YConnect. YQL can be
tested easily from the YQL Console too, but this time I will show an example
of executing with the iyql command that [I made last time][iyql-post].

	$ npm install iyql

The result just below.

	$ iyql
	iyql> select * from yahoojp.yconnect.userinfo where access_token="<access token>" and schema="openid"
	{
	    "user_id": "43M63NAGMHBAYMXRMY3WODOWS4",
	    "name": "OkumuraRyuichi",
	    "given_name": "Ryuichi",
	    "given_name_ja-Kana-JP": "",
	    "given_name_ja-Hani-JP": "Ryuichi",
	    "family_name": "Okumura",
	    "family_name_ja-Kana-JP": "",
	    "family_name_ja-Hani-JP": "Okumura",
	    "locale": "ja-JP",
	    "email": "okuryu@gmail.com",
	    "email_verified": "true",
	    "address": {
	     "country": "jp",
	     "postal_code": "1060032",
	     "region": "Tokyo",
	     "locality": "Minato-ku"
	    },
	    "birthday": "1984",
	    "gender": "male"
	}

YConnect can be used immediately once an application ID is issued, so please
try using it.

[yconnect]: http://developer.yahoo.co.jp/yconnect/
[userinfo-api]: http://developer.yahoo.co.jp/yconnect/userinfo.html
[iyql-post]: /2012/07/31/iyql-on-nodejs.html
