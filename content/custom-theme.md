<!--
title: 如何使用自己的主题
-->

首先，默认的主题会有太多人不喜欢，不管换成什么样的主题，也会有很多人不喜欢。

## 如何使用我自己的主题

非常简单，你只需要在工作目录下，执行如下命令：

  m2m init --theme

然后`M2M`将会在你的工作目录下，创建一个名为`m2m-theme`的文件夹，并复制默认的主题到此目录下，你可以根据自己的需求进行改造。

主题文件是基于`mustache`的模板，关于`mustache`的语法，请参考[mustache官方网站](http://mustache.github.io/)。CSS要求是原生的CSS，目前还不支持sass或者是less，以后会考虑支持。

## 主题文件

根据默认主题，我们来介绍一下目录结构以及文件的功能。

### 根目录

* `static`：静态文件目录，推荐将css和js放入此文件，但并不是必需的，只要你的引用路径正确，都是没有关系的。
* `template`：模板目录，必需存在

### template目录

* `partials`：子模板的目录，必需存在，比如说可以把header/footer等放入此目录，子模板的命名不作要求，只需要你自己能引用得到即可
* `article.mustache`：单个文章
* `home.mustache`：主页
* `index.mustache`：索引页，这个和home可能会搞混，首页只有一个，而索引页可能有多页
* `mail.mustache`：邮件的模板，你可以在此定义一些邮件的样式
* `page.mustache`：计划用于page的，不过目前没有用，可以忽略

`partials`下是可以自由定的，不再做介绍。

## 模板数据

### site

即`m2m.config`文件中`site`节点的数据，除邮件模板外，这个数据一直存在的。数据结构与`site`定义的完全一样，所以你可以在`site`节点中定义一些你自己的数据。

### article

文章的数据，在`article.mustache`和`mail.mustache`模板会拥有此数据。数据结构如下：


* `file`：完整的文件路径
* `relative_path_md5`：相对路径的md5值
* `mtime`：文件修改时间
* `original`：原始的markdown文件内容，包含`meta`
* `relative_path`：相对路径
* `relative_url`：相对url，即把`.md`扩展名改为`.html`
* `title`：文章的标题，优先取`meta`，如果没有则会取文件名
* `publish_date`：文章的发布时间，优先取`meta`，如果没有则会取`mtime`
* `body_markdown`：不包含`meta`内容的markdown
* `body_html`：`body_markdown`转换为HTML的内容，并不是完全的HTML页
* `excerpt`：摘要，取100个字符
* `toc_html`：TOC生成的HTML
* `meta`：Markdown中的meta部分，已经格式为key/value对应的内容，可以用`meta.title`的方式引用

### articles

文章列表的数据，在`index.mustache`和`index.mustache`模板会拥有此数据。`articles`是一个数组，每一项都是一个完整的`article`，请参考`article`的数据格式。

参考如下：

    <div class="posts">
        {{#articles}}
            <div class="post">
                <h1><a href="{{root/relative_path}}{{relative_url}}">{{meta.title}}</a></h1>
                <span class="post-date">{{meta.publish_date}}</span>
                <p>{{excerpt}}&hellip;</p>
            </div>
        {{/articles}}
    </div>

### nav

导航，用于列表显示上一页或下一页，参考如下：

    <div class="pagination">
        {{#nav.previous}}
            <a class="previous" href="{{nav.previous}}">&larr; 上一页</a>
        {{/nav.previous}}

        {{#nav.next}}
            <a class="next" href="{{nav.next}}">下一页 &rarr;</a>
        {{/nav.next}}
    </div>

### m2m

m2m产品相关的信息，如下：

* `name`：产品名称
* `version`：版本
* `homepage`：主页
* `repos`：仓库地址

### root/relative_path

这个很重要，相对链接地址，特别是对于有多级目录的网站来说，模板中的链接一定要加上这个，如：

    <a href="{{root/relative_path}}{{relative_url}}">{{meta.title}}</a>