---
layout: post
title: Quickstart 如何快速上手，一些示例代码
category: dev
tags: Python NodeJS PHP Ruby Curl

---

花 20 秒钟就可以了解如何在 Pyhton、NodeJS、PHP、Ruby、Curl 中对网页进行正文提取、标题提取、日期提取、下一页链接提取。

<!--more-->

以下是一些调用 API 的示例代码，关于 URL2io RESTful API 的详细文档请[看这](http://www.url2io.com/docs)。

### Curl

```shell
$ curl -G --data "token=your_token&fields=next" --data-urlencode "url=http://..." http://api.url2io.com/article

{"content": "...",
 "date": null,
 "next": null,
 "title": "...",
 "url": "http://..."}
```

### Python

```python
# 也可以使用 SDK
# https://github.com/url2io/url2io-python-client

>>> import requests
>>> from urllib import urlencode

>>> token = 'your token'          # 开发者 token, 注册后可得
>>> url = 'http://...'            # 要提取正文网页的网址
>>> fields = ','.join(['next',])  # 可选字段

>>> q = {'token': token, 'url': url, 'fields', fields}
>>> result = requests.get('http://api.url2io.com/article', params=q)
>>> result.json()

{u'content': u'...',
 u'date': None,
 u'next': None,
 u'title': u'...',
 u'url': u'http://...'}
```

### NodeJS

```js
var request = require('request');

request(
  { method: 'GET'
  , uri: 'http://api.url2io.com/article'
  , qs:
    { token: 'your_token'            // 开发者 token, 注册后可得
    , url: 'http://...'              // 要提取正文网页的网址
    , fields: ['next',].join(',')    // 可选字段
	}
  }
, function(error, res, body) {
	console.info(JSON.parse(body);
  }
)

{content: '...',
 date: null,
 next: null,
 title: '...',
 url: 'http://...'}
```

### PHP

```php
# url2io-phpsdk - https://github.com/ety001/url2io

<?php

use ETY001\URL2io\URL2io;             // 使用上述 SDK

$token = 'your_token';                // 开发者 token, 注册后可得
$url = 'http://';                     // 要提取正文网页的网址
$fields = join(',', array('next', )); // 可选字段

$url2io = new URL2io($token);
$result = $url2io->contentGet($url, $fields);

{"content": "...",
 "date": null,
 "next": null,
 "title": "...",
 "url": "http://..."}
```

### Ruby

```ruby
> require 'json'
> require 'open-uri'
> require 'cgi'

> token = 'your_token'           # 开发者 token, 注册后可得
> url = CGI.escape('http://...') # 要提取正文网页的网址
> fields = ['next',].join(',')   # 可选字段

> qs = "token=%s&url=%s&fields=%s" % [token, url, fields]
> JSON.parse(open('http://api.url2io.com/article'+'?'+qs).read)

=> {
  "content"=>"...",
  "data"=>nil,
  "next"=>nil,
  "title"=>"...",
  "url"=>"http://..."}
```
