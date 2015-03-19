##如何使用多说评论组件

1. 将此`CP`目录拷到`_includes`目录下
2. 将下列代码添加到`_config.yml`，将`short_name`替换为你的名字(需要到多说注册)

```yaml
# components
CP: 
  # setting comments
  comments:
    provider: duoshuo
    duoshuo:
      short_name: url2io #将此
```

3. 将下列代码添加到需要评论的页面中

```
{% include CP/comments %}
```
