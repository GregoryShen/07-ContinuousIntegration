# [Jenkins 快速上手](https://www.bilibili.com/video/BV1jc411h79J)

课程大纲

jenkins介绍

持续集成&持续交付

Jenkins安装

jenkins启动

job的创建

Job内的配置详解

凭据管理

全局工具配置

## 什么是Jenkins

免费的开源平台

常用语持续集成、持续交付还有自动化测试项目

它基于java开发, 可以跨平台运行

插件丰富, 支持各种扩展, 可以玩的东西不少

它的优势很多, 最大的优势就是使用广泛(用它的人多, 只因为好用; 很多人为它贡献插件, 于是乎就更加好用)

持续集成与持续交付诞生

持续集成、持续交付带来的优点

* 持续集成可以帮助研发与测试团队快速的发现错误, 每完成一个功能, 就将更新内容集成到对应分支上, 然后进行测试, 这样定位错误会相对容易、高效
* 持续交付能够帮助产品与业务团队能够更快速的在线上尝试最新的产品设计是否能够满足市场的需求, 能够快速纠偏, 快速让产品满足实际的市场需求.

## Jenkins安装

* 下载站点: https://jenkins.io/download/ 下载war包
* 下载站点: https://jenkins.io/download/ 下载对应的dmg或exe文件
* `docker pull jenkins/jenkins`

Jenkins 启动 -war包启动

* `java -jar jenknis.war`
* 将jenkins.war 放到

jenkins 启动-docker启动

需要找一台装好了docker的机器

启动

选择“参数化构建过程”

文本参数.

勾选`限制项目的运行节点`

构建环境下勾选: `Delete workspace before build starts`, 主要是用来在构建之前清理上一次构建的残留

构建,增加构建步骤



增加构建后的步骤

然后保存.

回到主界面后左侧导航栏中多了“`Build with Parameters`”

### 创建一个自由风格的job

### Job内配置-源码管理

添加凭据,

`Branches to build` 选择想要build的分支

### Job内配置-触发器

构建触发器, 选择定时构建, 日程表采用的是 cron格式

### Job内配置-参数化构建

This project is parametrized

名称:

默认值:

### Job内配置-构建命令

构建

执行shell

命令:

```shell
. ~/.bash_profile
java -version
mvn -Dtest=TestSearch test
```

### 凭据管理-创建凭据

添加凭据

```shell
docker ps

docker exec -it tech_jenkins bash
```

系统管理 -> 节点管理

新建节点

执行器数量:

远程工作目录:

标签:

用法: 尽可能的使用这个节点

启动方式: 通过Java Web启动代理

点击Launch, 或者

说明jenkins用的是本地的环境

构建方式改成轮询, 然后等待时间测试

钩子, 如果没有更新的话是不会更新的.

### 全局工具配置-maven

### 全局工具配置-jdk





