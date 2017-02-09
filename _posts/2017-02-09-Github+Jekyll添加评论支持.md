以[IntenseDebate](https://intensedebate.com/)为例，先去 [IntenseDebate](https://intensedebate.com/)注册一个账号。

1.在Jekyll站点的_includes目录下创建intensedebate-comments.html文件，文件内容如下。

![](2017-02-09-Github+Jekyll%E6%B7%BB%E5%8A%A0%E8%AF%84%E8%AE%BA%E6%94%AF%E6%8C%81/QQ20170209-162604@2x.png)

2.在站点配置文件(_config.yml)中添加评论配置参数，方便灵活的enable/disable评论功能。

`intensedebate_comments: true`

3.在post.html文件末尾后面添加代码引用intensedebate-comments.html来显示评论框。

![](2017-02-09-Github+Jekyll%E6%B7%BB%E5%8A%A0%E8%AF%84%E8%AE%BA%E6%94%AF%E6%8C%81/QQ20170209-162436@2x.png)

OK，快去评论一个吧！