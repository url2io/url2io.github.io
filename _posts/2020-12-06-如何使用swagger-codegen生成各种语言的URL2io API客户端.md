---
layout: post
title: 如何使用 Swagger Codegen 生成各种语言的 URL2io API 客户端
category: news
tags: url2io-python-client sdk swagger-codegen

---

URL2io提供了强大的智能信息处理服务，包括**URL2Article** 可以用来对网页进行结构化解析，智能识别网页正文、标题、下一页链接等，**URL2NLP** 可以用来对文本信息进行智能处理，提供中文分词、词性标注、关键词提取等功能。不过在应用开发阶段，开发者需要集成如此多的Rest API还是有一些难度的。好在官方提供的易于上手使用的SDK。不过对于大部分编程语言并没有提供对应的SDK。

<!--more-->

![在这里插入图片描述](/assets/img/swagger-codegen.png)



面对这种情况，我们可以使用[Swagger Codegen](https://github.com/swagger-api/swagger-codegen) 来自动生成30多个不同语言的SDK。当前URL2io提供了所有Rest API的[描述文件](https://github.com/url2io/url2io-python-client/blob/master/etc/services-url2io-api.yaml)，基于Swagger2.0。当前官方的 [url2io-python-client](https://github.com/url2io/url2io-python-client) 就是基于该描述文件生成的，下面以 url2io-python-client为例说明如何利用swagger-codegen来生成SDK代码。

![image-20201206013737566](/assets/img/services-url2io-api.yaml.png)



当前Swagger Codegen支持生成以下语言的SDK

>  **ActionScript**, **Ada**, **Apex**, **Bash**, **C#** (.net 2.0, 3.5 or later), **C++**(cpprest, Qt5, Tizen), **Clojure**, **Dart**, **Elixir**, **Elm**, **Eiffel**, **Erlang**, **Go**, **Groovy**, **Haskell** (http-client, Servant), **Java** (Jersey1.x, Jersey2.x, OkHttp, Retrofit1.x, Retrofit2.x, Feign, RestTemplate, RESTEasy, Vertx, Google API Client Library for Java, Rest-assured), **Kotlin**, **Lua**, **Node.js** (ES5, ES6, AngularJS with Google Closure Compiler annotations) **Objective-C**, **Perl**, **PHP**, **PowerShell**, **Python**, **R**, **Ruby**, **Rust** (rust, rust-server), **Scala** (akka, http4s, swagger-async-httpclient), **Swift** (2.x, 3.x, 4.x, 5.x), **Typescript** (Angular1.x, Angular2.x, Fetch, jQuery, Node)



## 安装swagger-codegen

**有几种安装方式：** 

官方文档见：https://github.com/swagger-api/swagger-codegen#prerequisites

方式一：直接下载

```bash
# Download current stable 2.x.x branch (Swagger and OpenAPI version 2)
# windows用户直接下载
wget https://repo1.maven.org/maven2/io/swagger/swagger-codegen-cli/2.4.17/swagger-codegen-cli-2.4.17.jar -O swagger-codegen-cli.jar

java -jar swagger-codegen-cli.jar help
```

方式二：brew方式（适用于Mac）

```bash
brew install swagger-codegen
```

方式三：Docker

```bash
docker pull swaggerapi/swagger-codegen-cli
```



## 生成SDK

不同的安装方式运行生成命令的方式有一点不同，不过流程和参数基本是一致的，具体可以看[官方文档](https://github.com/swagger-api/swagger-codegen#getting-started)。

以下以docker安装的方式做为示例:

### 步骤一：下载URLI2io Rest API描述文件services-url2io-api.yaml ：

下载地址：https://github.com/url2io/url2io-python-client/blob/master/etc/services-url2io-api.yaml

保存为`services-url2io-api.yaml`

![image-20201206014509737](/assets/img/service-url2io-api.yaml-snapshot.png)



### 步骤二：生成特定编程语言的配置文件 config.json

查看支持的语言：

```bash
$ docker run --rm swaggerapi/swagger-codegen-cli langs
>> Available languages: [ada, ada-server, akka-scala, android, apache2, apex, aspnetcore, bash, csharp, clojure, cwiki, cpprest, csharp-dotnet2, dart, dart-jaguar, elixir, elm, eiffel, erlang-client, erlang-server, finch, flash, python-flask, go, go-server, groovy, haskell-http-client, haskell, jmeter, jaxrs-cxf-client, jaxrs-cxf, java, inflector, jaxrs-cxf-cdi, jaxrs-spec, jaxrs, msf4j, java-pkmst, java-play-framework, jaxrs-resteasy-eap, jaxrs-resteasy, javascript, javascript-closure-angular, java-vertx, kotlin, lua, lumen, nancyfx, nodejs-server, objc, perl, php, powershell, pistache-server, python, qt5cpp, r, rails5, restbed, ruby, rust, rust-server, scala, scala-gatling, scala-lagom-server, scalatra, scalaz, php-silex, sinatra, slim, spring, dynamic-html, html2, html, swagger, swagger-yaml, swift5, swift4, swift3, swift, php-symfony, tizen, typescript-aurelia, typescript-angular, typescript-inversify, typescript-angularjs, typescript-fetch, typescript-jquery, typescript-node, ue4cpp, undertow, ze-ph, kotlin-server]
```



查看该编程语言支持哪些自定义参数，以python为例`-l python`：

不同的编程语言可以自定义的参数并不相同，在实际生成时需要运行一下命令来查看特定编程语言的参数。

```bash
$ docker run --rm swaggerapi/swagger-codegen-cli config-help -l python

CONFIG OPTIONS
	packageName
	    python package name (convention: snake_case). (Default: swagger_client)
	projectName
	    python project name in setup.py (e.g. petstore-api).
	packageVersion
	    python package version. (Default: 1.0.0)
	packageUrl
	    python package URL.
	sortParamsByRequiredFlag
	    Sort method arguments to place required parameters before optional parameters. (Default: true)
	hideGenerationTimestamp
	    Hides the generation timestamp when files are generated. (Default: true)
	library
	    library template (sub-template) to use (Default: urllib3)
```



根据需要编写`config.json`，提供url2io-python-client的示例：

```json
{
  "packageName": "url2io_client",
  "projectName": "url2io-client",
  "packageVersion": "1.0.1",
  "packageUrl": "https://github.com/url2io/url2io-python-client",
  "sortParamsByRequiredFlag": true,
  "hideGenerationTimestamp": true,
  "library": "urllib3"
}
```



### 步骤三：生成SDK

将 `services-url2io-api.yaml` 和 `config.json` 放在当前目录，运行以下命令

```bash
docker run --rm -v ${PWD}:/Downloads swaggerapi/swagger-codegen-cli generate \
     -i /Downloads/services-url2io-api.yaml \
     -l python \
     -o /Downloads/src \
     -c /Downloads/config.json
```



生成目录结构如下的SDK，其中有SDK代码`url2io_client`，也有对应的SDK使用文档`README.md`。

详细的目录结构请访问：https://github.com/url2io/url2io-python-client/tree/master/src

![image-20201206020811584](/assets/img/url2io-python-client-dir.png)



## Refs：

* [基于 Swagger 的 RESTful API 的定义与生成](https://developer.ibm.com/zh/devpractices/api/articles/define-and-generate-restful-api-using-swagger/)
* Github: [swagger-api/swagger-codegen](https://github.com/swagger-api/swagger-codegen)

