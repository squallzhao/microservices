基础
-----------
- [what is IO?](knowledge/io.md)
- [IO分类](knowledge/ioclass.md)


微服务周边
-------------
- [简介](http://microservices.io/)

- oss
    - [阿里oss-phpsdk](https://m.aliyun.com/doc/document_detail/32099.html?spm=5176.product31815.3.57.tWoXX8)
    - [阿里oss例子](http://blog.csdn.net/liujiahan629629/article/details/45290311)
    - [openstack swift镜像](https://hub.docker.com/r/morrisjobke/docker-swift-onlyone/)
- gateway
    - [openresty](http://wiki.jikexueyuan.com/project/openresty/openresty/install.html)
    - [API网关Kong](https://github.com/Kong/kong) 
        - [kong教程](http://www.cnblogs.com/SummerinShire/p/6386086.html) 
        - [dashboard](https://github.com/PGBI/kong-dashboard) 
        - [konga](https://github.com/pantsel/konga)
- schedule        
    - [xxl-job源码](https://github.com/xuxueli/xxl-job/) 
    - [xxl-job文档](http://www.xuxueli.com/xxl-job/)
- [Oceanbase](https://www.zhihu.com/question/37421030) 

扩展性
----------------
- 读写分离(Master/salve)

- 垂直分区(分库)

- 水平分区(分表，sharding)

- [Nosql](http://www.runoob.com/mongodb/nosql.html)

分布式共识(一致性）
--------------
- [Master-Slave 一般最终一致性](knowledge/masterslave.md)
- [Master-Master 一般最终一致性](knowledge/mastermaster.md)
- [NWR模型 一般最终一致性](knowledge/nwr.md)
- [2PC两阶段提交  Two  Phase Commit 强一致](knowledge/2pc.md)
- [3PC三阶段提交  ThreePhase Commit 强一致](knowledge/3pc.md)
- raft 强一致
   - [动画演示](http://thesecretlivesofdata.com/raft/)
- [paxos 强一致](http://www.jdon.com/artichect/paxos.html)
- zab 强一致

事务
------------
- [悲观锁，乐观锁](knowledge/lock.md)
- [CAP,ACID,BASE](http://www.jdon.com/37625)
- CAP三原则理论（分布式系统理论，只能满足2个）
    - Consistency(一致性) 数据一致更新，所有数据变动都是同步的
    - Availability(可用性) 好的响应性能
    - Partition tolerance(分区容忍性) 可靠性
- ACID事务策略（关系数据库的ACID模型拥有 强一致性 + 可用性 很难进行分区 CA）
    - Atomicity原子性：一个事务中所有操作都必须全部完成，要么全部不完成。
    - Consistency一致性. 在事务开始或结束时，数据库应该在一致状态。
    - Isolation隔离层. 事务将假定只有它自己在操作数据库，彼此不知晓。
    - Durability. 一旦事务完成，就不能返回。
- BASE事务策略（反ACID模型，完全不同ACID模型，牺牲高一致性，获得可用性或可靠性 AP）
    - Basically Available基本可用。支持分区失败(e.g. sharding碎片划分数据库)
    - Soft state软状态 状态可以有一段时间不同步，异步。
    - Eventually consistent最终一致，最终数据是一致的就可以了，而不是时时高一致。
- NOSQL(拓展了BASE思想，可按照具体情况定制CAP特别方案)
    - Key-Value存储，如Amaze Dynamo等，可根据CAP三原则灵活选择不同倾向的数据库产品。
    - 领域模型 + 分布式缓存 + 存储（Qi4j和NoSql运动），可根据CAP三原则结合项目定制灵活的分布式方案，难度高。
- [两地三中心](http://blog.csdn.net/love_taylor/article/details/73603672) 

安全
--------
*[csrf](http://netsecurity.51cto.com/art/201609/518323.htm)   *[csrf2](https://www.cnblogs.com/shytong/p/5308667.html)

*[xss](http://www.cnblogs.com/shytong/p/5308641.html)



