## URL2io — 提供简单、强大的网页正文提取服务

@all 感谢每一位支持我们的小伙伴


[URL2io.com][home] — 提供简单、强大的网页正文提取服务

今天给大家分享的是一个网页正文提取服务 [URL2Article][url2article] ，主页地址：[http://www.url2io.com][home]
> **URL2Article** 服务提供 **RESTful API** 接口，用来提取并解析网页中的正文区域，实现网页正文提取、标题提取、发布日期提取、下一页链接提取等。

<!--more-->

## **功能列表**

![features](https://i.v2ex.co/d073pq0c.png)

- **标题识别**：
> 不仅仅是简单地提取title标签，而是智能识别网页正文的标题。

- **正文识别**：
> 提取的内容将不含有任何广告、导航和其他非正文内容。网页正文中的所有链接、图片和其他媒体将予以保留。

- **发布日期识别**：
> 智能识别文章的发布日期。

- **下一页链接识别**：
> 智能识别当前网页的下一页链接。因为一篇完整的文章会被分成多个页面，所以这个功能会非常有用。

## **Demo**

> demo地址：[点这][test]测试效果。


## **API 使用文档**

> 可以查看相关文档 ([URL2Article API doc][doc]) 来了解如何使用。
 

## **示例应用**
> 为了让大家近一步了解这项服务，我们写了一个教学示例 **Pageless**， 它使用 **URL2Article API** 来提取网页正文，并自动将被分成多页的文章合并成一页。  
 > [演示地址][pageless], 代码在 [Github: url2io-app-samples][pageless_github]  
 >   
> ![pageless](https://i.v2ex.co/n87a5I0Ol.png)

## **Feedback**

That's all. 希望有兴趣的童鞋可以试用一下，然后给点反馈（使用中出现的问题、会用来开发什么、意见和建议等都可以）。 欢迎留言讨论，或者url2#sina.com，或者QQ 用户群：341180183

<!-- ref -->

[home]: http://www.url2io.com/?utm_source=v2ex&utm_medium=posted&utm_term=%E6%AD%A3%E6%96%87%E6%8F%90%E5%8F%96&utm_content=%E5%8F%91%E5%B8%83%E6%AD%A3%E6%96%87%E6%8F%90%E5%8F%96%E6%9C%8D%E5%8A%A1&utm_campaign=%E5%8F%91%E5%B8%83url2io

[test]: http://www.url2io.com/products?utm_source=v2ex&utm_medium=posted&utm_term=%E6%AD%A3%E6%96%87%E6%8F%90%E5%8F%96&utm_content=%E5%8F%91%E5%B8%83%E6%AD%A3%E6%96%87%E6%8F%90%E5%8F%96%E6%9C%8D%E5%8A%A1&utm_campaign=%E5%8F%91%E5%B8%83url2io

[url2article]: http://www.url2io.com/products?utm_source=v2ex&utm_medium=posted&utm_term=%E6%AD%A3%E6%96%87%E6%8F%90%E5%8F%96&utm_content=%E5%8F%91%E5%B8%83%E6%AD%A3%E6%96%87%E6%8F%90%E5%8F%96%E6%9C%8D%E5%8A%A1&utm_campaign=%E5%8F%91%E5%B8%83url2io#url2article

[doc]: http://www.url2io.com/docs?utm_source=v2ex&utm_medium=posted&utm_term=%E6%AD%A3%E6%96%87%E6%8F%90%E5%8F%96&utm_content=%E5%8F%91%E5%B8%83%E6%AD%A3%E6%96%87%E6%8F%90%E5%8F%96%E6%9C%8D%E5%8A%A1&utm_campaign=%E5%8F%91%E5%B8%83url2io#url2article

[pageless]: http://blog.url2io.com/url2io-app-samples/pageless/?utm_source=v2ex&utm_medium=posted&utm_term=%E6%AD%A3%E6%96%87%E6%8F%90%E5%8F%96&utm_content=%E5%8F%91%E5%B8%83%E6%AD%A3%E6%96%87%E6%8F%90%E5%8F%96%E6%9C%8D%E5%8A%A1&utm_campaign=%E5%8F%91%E5%B8%83url2io

[pageless_github]: https://github.com/url2io/url2io-app-samples