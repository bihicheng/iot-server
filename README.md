# iot-server
iot管理平台，监控，通知，管理

#### 背景
我们生活在物联网时代，身边各种各样的智能硬件，作为一个智能硬件生产商如何保证硬件设备正常工作，如何在设备离线后第一时间知道？以及如何远程控制智能硬件？
本项目的使命就是提供一个这样的平台，把各种智能硬件集中管理，为中小客户提供服务。

#### 架构图
![架构图](https://github.com/bihicheng/iot-server/blob/master/%E6%9E%B6%E6%9E%84%E5%9B%BE.jpg)

* http服务器使用gin，官网提供的数据http路由速度提升40倍，因为他的router是用 radix tree的实现，节省存储空间，避免hash冲突，所以更快, 算法参见wiki[radix](https://en.wikipedia.org/wiki/Radix_tree)
* 数据采用mysql, mysql当前主从复制模式提供高可用，1主2从，主要是因为mysql成熟，各种运维工具和优化措施
* golang mysql数据库驱动采用go-sql-driver，（本打算不用orm,但是看了一下gorm还不错，比较简单比较容易修改，在开发便捷和性能上是个折中方案）写原生sql（注意sql注入安全风险），不使用orm，因为不方便优化sql查询等
* 消息队列先使用redis， 以后可能会用kafaka，主要是考虑到可能同时有大量100万的数据上报
* 系统配置模块 仔细看了一下![configor](https://github.com/jinzhu/configor)，满足需要就不重复造轮子了。
* 日志模块
* 部署方式
* 开发方式
* 单元测试，回归测试
* ci
* 
