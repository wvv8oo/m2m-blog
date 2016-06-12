<!--
title: 关于M2M的配置文件
-->


在阅读此文之前，我相信你已经阅读过[如何将Markdown生成html格式的邮件并发送](./markdown-to-mail.html)和[如果将Markdown生成一个网站](./markdown-to-site.html)两篇文件。

M2M提供更丰富的配置方式，在此之前，我们先了解一下配置文件是如何工作的吧。

## 配置文件是如何工作的

`M2M`的配置文件分为两个部分，分别是全局配置与本地配置，全局配置在`~/.m2m/m2m.config`，而本地配置则在你的工作目录下，同样的，文件名也是`m2m.config`。

当你使用`m2m`的时候，它会把你的全局配置与本地配置全并，当然，本地配置的优先级别更高，也就是说，你可以用本地的配置文件去覆盖全局的配置，也可以在全局配置中定义一些常用的配置。

 一个通用的优先级是：命令行(如果允许) > 文件中指定(如果允许) > 本地配置 > 全局配置

## 配置文件的格式

`M2M`的配置文件是基于`YAML`格式的，虽然我十分想用`JSON`格式，但考虑到ruby社区的习惯，我决定还是使用`YAML`格式的配置文件了。其实还有一个比较重要的一点是，JSON文件格式不支持注释。

如果你不了解`YAML`格式，没关系，你可以使用[json2yaml](http://www.json2yaml.com/)这个网站进行转换，也可使用[yamltojson](http://yamltojson.com/)进行反向转换。

## 详细配置

这是一份完整的配置，我在配置中加了注释，就不一一展开了。

    ---
    #网站相关的配置
    site:
      #网站的标题
      title: M2B官方博客
      #网站的主机地址
      host: http://m2b.wvv8oo.com/
      #分页时每页的大小，如果没有设置，默认按每页10条进行分页
      page_size: 10
      #生成网站后，执行的shell脚本
      after_build_shell: "pwd"
    #markdown文件内容的路径，如果没有配置，会在工作目录查找
    content: "./content"
    #生成的目录，如果没有配置，则会生成到m2m-site这个目录
    target: "./site"
    #邮件配置，这个配置一般是在全局的m2m.config文件，工作目录如果有需要，也可以覆盖
    mail:
      #SMTP服务器地址
      smtp_server: smtp.example.com
      #SMTP的端口号
      port: 465
      #你的邮箱帐号
      username: mail@example.com
      #发件人
      from: 张三 <mail@example.com>
      #默认主题
      subject: 周报 张三 $last_week - $now
      #格式化标题中的日期
      format: '%Y/%m/%d'
      #加密过后的密码，这个仅限于M2M写入
      password: |
        hAZ+LfAAey22P/Xh1PPiIA==
      #默认的收件人
      to: 007@example.com,peter@example.com
      #是否启用SSL，启用为y，不启用为n
      ssl: n
      #安全性配置，这个不要更改，在你设置密码的时候会自动配置
      safer: false