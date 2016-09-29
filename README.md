xSkyProxy
=====
xSkyProxy是一个简单易用的MYSQL代理程序，提供mysql数据分库分表，连接池，主从读写分离等功能。 xSkyProxy 开源社区群 302102856

* 功能与特性
    * 1.多模式运行：Mysql数据代理转发或是分库分表
    * 2.按自定义规则进行分库分表与SQL改写
    * 3.自动读写分离, 支持MySQL一主多从
    * 4.自动负载均衡
    * 5.支持到每个分片库的连接池
    * 6.强大的Web管理后台


### xSkyProxy 的 Sharding 架构
![mahua](http://xskyproxy.0xsky.com/images/plans.png)

### xSkyProxy 中的分库分表概念

在 xSkyProxy 中,一个表可以分库后存储在多个mysqlDB中，每个DB中可以包含多个mysql数据表; mysql数据表是数据存储的单位, 一个表的路由是由 database.tabname 组成。 一个逻辑表可以分片到多个database里, 每个DB里由一个或是多个分表组成; 这些分片的 DB可以存储在一个或是多个MYSQL实例里，每个DB可以的有0个或者多个slave。


### xSkyProxy内置的分库分表算法
todo

### xSkyProxy数据切分策略
xSkyProxy自带多种常见分库分表算法(取模/按时间/按范围/等)
也支持运行时从外部SO加载自定义的分库分表算法。

### xSkyProxy中MYSQL语句与语法的有限支持
xSkyProxy 目前只支持 select/delete/update/insert/replace 语句(经过测试,别的语句可能也支持但未经测试过);

###xSkyProxy中关于事务支持

xSkyProxy 目前不支持分布式事务。因为数据被分库分表的原因，如果需要事务功能，只能支持数据都在同一个库里的事务。 此需求可以对数据都在同一个库里时用存储过程里采用事务实现。

### xSkyProxy 中数据库的节点扩展与负载均衡
xSkyProxy 的分库分表功能支持数据分布在同一个库的多个表里，也支持分布在多个库的多个表里;采用分库的方式在数据量大时可以很容易的做到迁移数据降低负载,只需要把分库迁移到新的MYSQL实例上,同时修改连接表里对应新库对应的主机连接信息。

###xSkyProxy 管理后台与性能监控
xSkyProxy 提供web后台对配置信息进行管理，同时后台也可以查看 xSkyProxy进程内部运行状态与统计信息。
[后台demo](http://yun.0xsky.com:8000)

###xSkyProxy 与 mysqlproxy 
xSkyProxy 不是基于mysqlproxy的修改版. 程序主要框架用C++开发,基于libevent, 语法分析Flex.


##有问题反馈
在使用中有任何问题，欢迎反馈给我，可以用以下联系方式跟我交流

* 邮件(guozhw#gmail.com, 把#换成@)
* xSkyProxy 社区QQ群 302102856
* [http://xskyproxy.0xsky.com/](http://xskyproxy.0xsky.com/)
