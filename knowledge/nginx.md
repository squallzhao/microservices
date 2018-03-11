# 安装
apt-get install nginx

# 简单教程 
http://www.runoob.com/linux/nginx-install-setup.html

# book
http://tengine.taobao.org/book/

# rewrite
https://www.cnblogs.com/czlun/articles/7010604.html

# last与break的区别

    last： 停止当前这个请求，并根据rewrite匹配的规则重新发起一个请求。新请求又从第一阶段开始执行…
    break：相对last，break并不会重新发起一个请求，只是跳过当前的rewrite阶段，并执行本请求后续的执行阶段…

    举一个例子：
    server {
    listen 80 default_server;
    server_name dcshi.com;
    root www;

    location /break/ {
    rewrite ^/break/(.*) /test/$1 break;
    echo "break page";
    } 

    location /last/ {
    rewrite ^/last/(.*) /test/$1 last;
    echo "last page";
    } 

    location /test/ {
    echo "test page";
    }
    }

    请求:http://dcshi.com/break/***
    输出: break page
    分析：正如上面讨论所说，break是跳过当前请求的rewrite阶段，并继续执行本请求的其他阶段，很明显，对于/foo 对应的content阶段的输出为 echo “break page”; (content阶段，可以简单理解为产生数据输出的阶段，如返回静态页面内容也是在content阶段；echo指令也是运行在content阶段，一般情况下content阶段只能对应一个输出指令，如同一个location配置两个echo，最终只会有一个echo指令被执行)；当然如果你把/break/里的echo 指令注释，然后再次访问/break/xx会报404，这也跟我们预期一样：虽然/break/xx被重定向到/test/xx,但是break指令不会重新开启一个新的请求继续匹配，所以nginx是不会匹配到下面的/test/这个location；在echo指令被注释的情况下，/break/ 这location里只能执行nginx默认的content指令，即尝试找/test/xx这个html页面并输出起内容，事实上，这个页面不存在，所以会报404的错误。

# redirect和permanent区别

    nginx的rewrite指令中可以通过设置该条rewrite的flag来对该规则进行说明。一般可以设置的flag有：last，break，redirect，permanent四种。

    redirect说明，这条规则是一个临时的跳转，并且此时如果观察http请求的话，http的响应状态码为302.

    permanent说明，这条规则是一个永久性的跳转，并且此时，http的响应状态码为301.


    那么什么是永久性跳转，什么是临时跳转，这有什么作用呢？下面我们举例说明：

    如果有一个url，/a。

    如果配置成
    rewrite "/a" "http://test.html" redirect;

    则说明这个跳转是一个临时跳转，此时如果有网络爬虫爬这个链接时，是不会更新自己的url数据库的。

    但是如果配置成permanet，则爬虫会更新自己的url数据库，把/a更新为http://test.html。

    这也就是临时跳转和永久跳转的区别。

