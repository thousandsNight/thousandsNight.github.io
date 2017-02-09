以[IntenseDebate](https://intensedebate.com/)为例，先去 [IntenseDebate](https://intensedebate.com/)注册一个账号。

1.在Jekyll站点的_includes目录下创建intensedebate-comments.html文件，文件内容如下。

`{% if page.comments != false %}
	给你的站点Install IntenseDebate之后获得的脚本
{% endif %}`

2.在站点配置文件(_config.yml)中添加评论配置参数，方便灵活的enable/disable评论功能。

`intensedebate_comments: true`

3.在post.html文件末尾后面添加代码引用intensedebate-comments.html来显示评论框。

{% if page.path contains '_posts' %}
    {% if site.intensedebate_comments %}
    {% include intensedebate-comments.html %}
    {% endif %}
{% endif %}

OK，快去评论一个吧！