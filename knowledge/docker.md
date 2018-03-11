# 安装
    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
    add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
    apt-get update
    apt install docker-ce
    
    
    curl -L https://github.com/docker/compose/releases/download/1.14.0/docker-compose-`uname -s`-`uname -m` > /usr/local/bin/docker-compose
    chmod +x /usr/local/bin/docker-compose

*[docker-compose](https://linux.cn/article-8746-1.html)

http://wiki.jikexueyuan.com/project/docker-technology-and-combat/usage.html

*[docker-compose资源](https://github.com/yeasy/docker-compose-files)

*[example-3](http://blog.csdn.net/yl_1314/article/details/53761049)

