# 安装
    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
    add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
    apt-get update
    apt install docker-ce

1.1如果是Centos7，直接使用sudo yum install -y docker
1.2 如果是Centos6，sudo yum install -y http://mirrors.yun-idc.com/epel/6/i386/epel-release-6-8.noarch.rpm
sudo yum install -y docker-io

杀死所有正在运行的容器
复制代码 代码如下:
docker kill $(docker ps -a -q)

 删除所有已经停止的容器
复制代码 代码如下:
docker rm $(docker ps -a -q)

 删除所有未打 dangling 标签的镜像
复制代码 代码如下:
docker rmi $(docker images -q -f dangling=true)


docker
http://blog.csdn.net/wuapeng/article/details/51728614
docker search <image>：在docker index中搜索image
docker search centos

下载镜像
docker pull centos:latest
docker run -it centos:latest /bin/bash

创建新镜像
docker commit 6c4b67800f97(为容器名/ID) node:node1(为新的镜像名)

删除镜像
docker rmi <镜像名或ID>

容器
docker start/stop/restart <container> ：开启/停止/重启container
docker start [container_id]：再次运行某个container（包括历史container）
docker run -i -t <image> /bin/bash ：使用image创建container并进入交互模式, login shell是/bin/bash
docker run -i -t -p <host_port:contain_port> ：映射 HOST端口到容器，方便外部访问容器内服务，host_port可以省略，省略表示把 container_port映射到一个动态端口

docker ps -a

映射目录启动
docker run  -v /root:/mnt/ --name mytest -i -t centos:latest /bin/bash
docker run -d centos /bin/sh -c "while true; do echo hello world; sleep 1; done"

保存到文件
docker save -o centos_with_net.tar 92b2e7f857ae

从文件中加载
docker load <centos_with_net.tar

导出和save区别
udo docker images --tree
执行命令，显示下面的内容。正你看到的，导出后再导入(exported-imported)的镜像会丢失所有的历史，而保存后再加载（saveed-loaded）的镜像没有丢失历史和层(layer)。这意味着使用导出后再导入的方式，你将无法回滚到之前的层(layer)，同时，使用保存后再加载的方式持久化整个镜像，就可以做到层回滚（可以执行docker tag <LAYER ID> <IMAGE NAME>来回滚之前的层）。

https://hub.docker.com,搜索要的软件,比如redis,可以看到

# supervisord
http://debugo.com/docker-supervisord/

# docker-compose

    curl -L https://github.com/docker/compose/releases/download/1.14.0/docker-compose-`uname -s`-`uname -m` > /usr/local/bin/docker-compose
    chmod +x /usr/local/bin/docker-compose

*[docker-compose](https://linux.cn/article-8746-1.html)

http://wiki.jikexueyuan.com/project/docker-technology-and-combat/usage.html

*[docker-compose资源](https://github.com/yeasy/docker-compose-files)

*[example-3](http://blog.csdn.net/yl_1314/article/details/53761049)



