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
* docker pull jenkins/jenkins

Jenkins 启动 -war包启动

* java -jar jenknis.war
* 将jenkins.war 放到

jenkins 启动-docker启动

需要找一台装好了docker的机器

启动















