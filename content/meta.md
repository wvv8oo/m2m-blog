<!--
title: 如何使用meta
-->

## 什么要使用meta

通常markdown只包含文章的主体部分，但实际上，一篇文章或者邮件，还会包含其它内容，如作者、排序、tag、发布日期等，某些时候我们可能还需要自定义标题与url。对于markdown这种非结构化的内容来说，我们需要增加一些结构化的内容来保存这些内容，而meta就是为了解决这个问题的。

## 如何定义meta

你只需要在markdown的第一行加入如下内容即可：

    <!--
    title: 这里是自定义的meta
    subject: 这是另一个meta
    -->

meta被`<!-- -->`包裹起来，每行一个，采用`key: value`的方式书写，注意meta一定要顶行开始写。

### m2m已定义的meta

* `title`：文章标题
* `author`：文章的作者
* `subject`：邮件主题，如果要将当前markdown作为发邮件发送，并且不采用默认标题，可以用这个meta
* `to`：收件人，如果要将当前markdown作为发邮件发送，并且不采用默认收件人，可以用这个meta

### m2m计划定义的meta

* `order`：文章排序
* `publish_date`：文章发布时间，如果没有设置，则使用最后修改时间
* `tag`：文章的tag，多个tag用英文逗号`,`分隔

## 使用自己的meta

如果你使用自定义theme，可以增加更多的meta，自己在theme中使用`{{meta.your_key}}`就可以使用了。