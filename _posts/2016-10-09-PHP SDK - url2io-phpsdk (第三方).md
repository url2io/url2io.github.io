---
layout: post
title: url2io-phpsdk 一个第三方PHP SDK
category: dev
tags: SDK PHP

---

[![Build Status](https://travis-ci.org/ety001/url2io.svg?branch=master)](https://travis-ci.org/ety001/url2io)

[url2io-phpsdk](https://packagist.org/packages/ety001/url2io-phpsdk) 是一个第三方的 URL2io PHP SDK，由 [ety001](http://www.domyself.me/) 实现，十分感谢！

<!--more-->
> URL2io 提供简单，强大的网页信息提取服务。所有服务都以 RESTful API 接口的形式提供，用于 Web 内容的结构化处理。其中 URL2Article 用来提取并解析网页中的正文区域，实现网页正文提取、标题提取、发布日期提取、下一页链接提取等。


### 1. URL2io 官网文档

相关 RESTful API 的细节请参考 <http://www.url2io.com/docs>

### 2. 使用说明

#### composer 安装

```
composer require ety001/url2io-phpsdk
```

#### 在项目中使用

使用PHP进行对网页进行正文提取：

```
<?php
use ETY001\URL2io\URL2io;             // 使用上述 SDK

$token = 'your_token';                // 开发者 token, 注册后可得
$url = 'http://';                     // 要提取正文网页的网址
$fields = join(',', array('next', )); // 可选字段

$url2io = new URL2io($token);
$result = $url2io->contentGet($url, $fields);

?>

{"content": "...",
 "date": null,
 "next": null,
 "title": "...",
 "url": "http://..."}

```

### 3. 其他

#### 待完善

* 是否由库来处理返回的结果，还是交给用户处理
* 完善错误处理机制

#### 协议

`MIT`

#### 联系方式

* Email: <ety002@gmail.com>
* Blog: <http://www.domyself.me>
* [源码](https://github.com/ety001/url2io)

最后，URL2io 的成长，离不开热心朋友的关注与支持。希望您多提需求及建议，为 URL2io 的完善提供源源不断的养分。
