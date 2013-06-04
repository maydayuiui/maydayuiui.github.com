---
layout: post
title: 生命不息，折腾不止
---

![Jakiro](/img/jakiro.png)

### VPS入手
一直以来都想买个VPS，虽然不知道能用它来做些什么，但至少能*翻墙*吧。经同事推荐在[photonVPS][1]下了单。为了每个月能剩几刀，憋了半个月，等到有终身7折的时候才下的手。（真的不知道这个终身有没有意义。）第一次下单由于把地址写成Italy，订单成了Cancelled状态。（果然是国人开的VPS，就是得放着点欺诈啊。不过，互联网上真的没隐私，我们都是弱势群体，没有匿名功能真的很离谱啊。）后来改成China终于成了有VPS一族。几秒后，大约1000秒以内吧。收到开通邮件，怀着忐忑的心情测试了下IP，能ping通。安心了。之前看评论说有几率收到被block的IP。那就悲催了。

[1]: http://www.photonvps.com/

### DNS注册
面对每个月7.67$的VPS支出，如果再加上域名注册的钱（以我一贯坚持不下来的性格），那就赔大发了。幸好有大JZ推荐的免费域名。虽然[TK][2]域名有很多坑爹的地方，但是能用啊，**免费**啊。再配上[DNSPod][3]，速度也是可以的。

[2]: http://www.dot.tk/
[3]: https://www.dnspod.cn/

### Jekyll
接下来就是开始折腾it了。在没有其他可折腾的项目之前，先把博客搭起来。由于我的VPS是最低配的，总是对要使用Wordpress那种*重量级*的东东感觉有些吃力（当然不是说这里会有多大的浏览量，而是吃掉了内存，还怎么折腾啊。）。一个静态页面的博客就是最理想不过了。再加上最近Markdown的红火（难道真是天才挂了，他的作品才能红？），[Jekyll][4]就成了理想的选择。

[4]: http://jekyllrb.com/

> Jekyll is a simple, blog aware, static site generator.

### 搭建Jekyll Blog
Jekyll是使用Ruby写的，在安装Jekyll之前，需要安装Ruby。

    #yum install rubygems
    #yum install ruby-devel

然后就可以使用gems(ruby的package管理器。）来安装Jekyll了。

    #gem install jekyll

安装后，就可以在命令行中使用jekyll命令了。它会对当前目录下的文件进行转换，把Markdown等类型的文件转换成静态的HTML文件。jekyll可以处理的文件需要放在特定的目录结构下：

    .
    |-- _config.yml
    |-- _includes
    |-- _layouts
    |   |-- default.html
    |   `-- post.html
    |-- _posts
    |   |-- 2007-10-29-why-every-programmer-should-play-nethack.md
    |   `-- 2009-04-26-barcamp-boston-4-roundup.md
    |-- _site
    `-- index.html
    
下面是我用的配置文件：_config.yml 

详细的可以参照：<https://github.com/mojombo/jekyll/wiki/Configuration>

    safe:        false
    auto:        true
    server:      false
    server_port: 4000
    baseurl:    /jekyll_demo
    url: http://localhost:4000
    
    source:      .
    destination: ./_site
    plugins:     ./_plugins
    
    future:      true
    lsi:         false
    pygments:    false
    markdown:    maruku
    permalink:   date
    
\_layouts文件夹是放置如何布局的文件的。如果在\_posts文件夹中的文件的YAML Front中指定default,则该文件使用\_layouts中default.html的布局。而\_posts文件夹就是放我们写好的Markdown文件的地方了。当这些都写好后，就可以在.这层目录运行jekyll。它把根据Liquid模板把含有YAML Front的文件转换成html，并存放在\_site中。这样完整的博客站点就搭建好了。可以把\_sites部署了。Jekyll的wiki中介绍了很多部署方法。可以选择部署在github或者apache等。


######题图
Jakiro DOTA2中的双头龙。对于我这个发音不标准的人来说，Jakiro和Jekyll还真有那么点像。


