## 17 Jenkins 持续集成

### 17.1 Jenkins 持续集成的简介

#### 持续集成与自动化测试的关系

随着软件技术的不断发展，集成的频率也越来越快，在瀑布模型的年代，只有一个软件进入测试阶段才会开始做集成。而现在，每天集成多次也完全可能。这一切依赖于自动化的持续集成工具。值得注意的是，自动化在持续集成中是必须的，在持续集成系统上自动化构建软件，其步骤包括编译，自动化单元测试，自动化集成测试，代码扫描，发布，部署等环节。其中每个环节步骤又有很多工具和脚本。这些工具和脚本往往和自动化测试密切相关，因此测试人员需要掌握这些。

自动化测试在持续集成中至关重要。任何未经过测试的版本，即使构建出来，也是无用的版本。而为了快速迭代，快速发布软件的新版本，测试必须是自动化的。诚然，自动化测试不能完全替代手工测试，但是，它正在替代大多数手工测试。其原因在于，自动化测试的超高效率，以及它和持续集成的紧密配合。当持续集成刚刚出现，每天集成一个新版本的时候，手工测试还能跟得上节奏，然而随着技术发展，每天集成几个新版本甚至十几个新版本时，只有自动化测试能跟得上持续集成的节奏。

要实现持续集成，需要使用很多工具，但其中最重要的工具则是持续集成系统。Jenkins在第一次使用的时候就要开始理解他的设计原理： Jenkins通过提供Web界面，让用户可以简单地组分布式来执行各种任务（这些任务被称为Job）

#### Jenkins 的简介

Jenkins的最核心功能是以分布式的形式运行我们预先设置好的任务。

首先，在没有持续集成，软件也都是单机软件的时候，我们要发布一个软件的新版本，可以在自己的个人电脑上直接编译源代码，然后打包成exe文件，并把这个exe文件拿去发布。后来，网络软件成了主流，我们的发布方式改成把源代码编译成软件包，然后发送到Web服务器上去完成部署。之后用户就可以访问这个Web服务器来使用

### 17.2 Jenkins 的安装

Jenkins 的下载主要是从官网 https://jenkins.io/download 或者镜像站 http://mirrors.jenkins-ci.org/ 下载。我下载的是war包，war包的使用比较简单，镜像站中的 `mirrors.jenkins-ci.org/war/latest/` 这个地址可以下载到 `jenkins.war` 这个war 包。 安装方面， war包是免安装的。我们只需要在命令行里打开存放这个包的路径，然后使用以下命令启动 jenkins：

```java
java -jar jenkins.war
```

然后，我们打开浏览器，输入地址 http://localhost:8080/ ，经过一番等待后，正常的话就会看到这个界面：

这里，我们按照提示，打开指定的文件，把管理员密码输进去，然后点击继续。 Jenkins这时应该跳转到下载插件的页面。

在这个页面上，选择“选择插件来安装”，然后在后续页面上选择“无”， 再点击下方安装按钮：

则可以不下载任何插件而完成Jenkins 的安装。我们可以在后面进入插件管理页面再进行安装和删除等管理操作。

而如果在Jenkins界面时网络连接失败（国内有些网络经常遇到这个现象），则会进入下面界面：

在这个页面上，我们选择“跳过插件安装”即可，也可以完成安装过程。后续仍然可以在插件管理页面进行插件下载安装，也可以后续通过手动安装等其他方式来安装插件。

然后就到了“创建第一个管理员用户”页面：

在这里，Jenkins要求我们创建第一个管理员用户，要求我们输入用户名 Username, Password。这里，我们可以依次这样输入：

Username: admin

Password: admin

Confirm password: admin

Full name: admin

点击保存并完成后进入实例配置页面，这里保持默认值不需要改变， 直接保存并继续。

然后点击开始使用Jenkins，进入Jenkins首页。

### 17.3 Jenkins 的插件配置和下载

从Jenkins 首页上，我们要关注这几个链接：中间最大的 create new jobs 是用来创建新的 job 的。左边的 New Item （中文版为“新建任务”） 也是起到同样的作用。 左边的 Manage Jenkins 里可以对Jenkins 做配置。我们第一次使用Jenkins的话，需要下载一些插件，点击页面左侧的 manage Jenkins，进入Jenkins 管理页面：

这个页面上显示的都是管理相关的功能，介绍如下：

* Configure System：系统配置，一些全局参数的设置
* Configure Global Security: 安全配置，定义谁可以用这个Jenkins
* Global Tool Configuration：全局工具配置，用于配置Maven，JDK之类的工具，这里的配置对整个Jenkins生效
* Reload Configuration from Disk：重置配置信息，以磁盘上存储的配置为准
* Manage Plugins：添加、删除、或者禁用、启用插件，这个功能是最常用的
* System Information: 展示 Jenkins 系统的一些属性
* System Log: 这里可以看到 Jenkins 本身的日志
* Load Statistics: 这里可以看到 Jenkins 的负载情况的图表
* Jenkins CLI: Jenkins 命令行工具的帮助信息 
* Script Console: 可以执行一些脚本. 这种属于高级功能, 脚本可以做到几乎任何事情
* Manage Nodes: 管理节点. 节点包括 master 和 slave. Master 就是指我们安装 jerkins 的这台电脑, 而 slave 则是 master 可以管理的其他电脑, 我们可以把其他电脑设置成 Jenkins 的 slave, 从而在 slave 上运行 job.
* About Jenkins: 显示版本和证书信息
* Manage Old Data: 可以管理和删除一些过期数据.
* Install as Windows Service: 用来把 Jenkins 注册成 Windows 服务
* Manage Users: 用户管理
* Prepare for Shutdown: 用来关闭 Jenkins 系统.

这里, 我们点击 Manage Plugins 进入插件管理页面, 在这个页面上就可以下载 jerkins 的插件了:

图略

左侧 Install 列下的小方框里打钩, 然后按最下面的 Install without restart 按钮即可安装插件. 如果你进入这个页面之后看到的是空的列表, 那么说明网络出问题了, 连不上插件服务器. 此时需要手工安装插件, 进入上方 Advanced 这个标签页, 会跳转到这个界面:

图略

在这个界面上, 我们作为 Jenkins 管理员, 可以手工上传预先下载好的 `.hpi` 文件, 并在重启 Jenkins 后生效, 这样就可以做插件的手工安装了. 当然, 手工安装比较麻烦, 我们一般还是在插件列表里选择插件来安装. 

除了手工安装插件以外, 还可以通过修改 Update Site 的 URL 来获取插件列表, 具体步骤如下:

将 https://updates.jenkins.io/update-center.json 修改为 http://updates.jenkins.io/update-center.json 也就是把 https 改为 http 即可. 此外, 如果网速仍然缓慢, 可以修改为镜像站点: http://mirror.xmission.com/jenkins/updates/update-center.json

此时, 从插件下载页面的 “Available” 选项卡下即可下载我们需要的插件. 以下是一个常用插件列表:

Local

Localization: Chinese(Simplified) 这个是本地化插件, 想要中文界面就必选

Folders

OWASP Markup Formatter

Build Timeout

Credentials Binding

Timestamper

Workspace Cleanup

Maven Integration

Pipeline

GitHub Branch Source

Pipeline: GitHub Groovy Libraries

Git 这个是 Git 插件, 注意 filter 会过滤出一大堆和 git 有关的插件, 其中只有一个叫 Git 的

Subversion 支持 svn 的插件, 如果不用 svn 可以不装

SSH Slaves

Matrix Authorization Strategy

PAM Authentication

LDAP

Email Extension

GitLab

Ansible

SaltStack

Parameterized Trigger

Build Pipeline

Build Authorization Token Root

如下图所示, 我们依次在右上角 Filter 中输入插件名称, 然后在下面列表中打钩, 如果有不确定打钩哪个的可以跳过. 等列表中所有插件都打完钩, 点击左下角 Install without restart 按钮, 然后等 Jenkins 一个一个安装插件即可.

如果还有失败的可以尝试重复上面步骤再次下载或手工安装.

### 17.4 Jenkins 上创建和运行job

首先，我们在 Jenkins 首页上点击左侧” New Item”或者“新建任务”， 进入如下的 Jenkins job 创建页面。

图略。

这里我们可以输入 Job 的名称为 job001, 并且选择类型是 “构建一个自由风格的软件项目” 或者是 “Freestyle project”。注意这里可以选择的类型和我们安装的插件有关，如果你的 Jenkins 上类型比上图中少，说明缺少相应的插件。有时由于本地化插件的版本出错，也会遗留一些英文在界面上。

图2 源码管理中的 git 的配置 （图略）

Repository URL 为： https://github.com/TestUpCommunity/TUGithubAPI.git

Branch Specifier (blank for ‘any’) 为 */teach_011

其他不用选择，保持默认即可。

图3 构建触发器的配置

构建触发器我们这次不用做设置。

其中重要的设置项有：

* 如果要定时执行任务，则勾选 Build periodically
* 如果要处理 post commit hook 来做到每次提交代码到指定分支都触发 job，则勾选 Poll SCM

图4 构建环境的配置

这里，勾选 Add timestamps to the Console Output 来给 job 执行日志加上时间戳。

图5 构建步骤的配置

这里选择 ”增加构建步骤“，然后选择 ”Execute shell“ 才能看到上图中的命令窗口，在命令窗口中输入 `echo "hello world"` 来完成我们的第一个 job。随后点击最下方的保存按钮。系统会自动跳转到以下页面。

图6 新建的 Jenkins job 界面

在这里，我们点击 Build Now 即可开始执行这个 job，在刚才的配置里，我们先从 github 上 clone 了我们接口测试项目，然后让脚本运行一个 hello world。运行一个job，也叫触发一个 job。

图7 新建的 Jenkins job 触发后

这个 Jenkins job 触发后，屏幕左侧出现 Build History 界面，点击序号 #1 前闪烁的圆球进入控制台日志显示界面。一个 job 每一次运行的记录，都称为一个 Build，这里显示的数字称为 Build ID。

图8 新建的 Jenkins job 的运行日志

在控制台输出的 job 运行日志中，我们可以看到， Jenkins 成功地使用 git 插件 clone 了我们的项目代码，并在屏幕上输出了 hello world。

### 17.5 Jenkins 上运行接口测试

首先，我们按照上一节的操作来创建一个新job，名为job002，这次在“源码管理”中直接选择“无”，因为我们要用命令行来完成所有操作。其他设置都一样，而命令窗口中的命令改为如下代码：

```shell
export token=xxxx # 替换成真实token
export env = test_env

rm -rf TUGithubAPI
rm -rf TUGithubAPITest
git clone https://github.com/TestUpCommunity/TUGithubAPI.git
git clone https://github.com/TestUpCommunity/TUGithubAPITest.git
cd TUGithubAPI
git checkout teach_011
cd ..
cd TUGithubAPITest
git checkout teach_011
cd ..
cd TUGithubTest/api_test/
pytest
```

这些 shell 命令是分别clone了接口测试项目实战的两个子项目，并运行了其中的 TUGithubAPITest/api_tests 目录下的三个测试用例。

运行结果的控制台输入如下：

略

最后，我们为这个 job 添加图形化的测试报告，首先在构建后操作中添加 ”Publish Junit test result report“ 这个步骤。

然后把命令窗口最后一行修改为：

`pytest --junitxml=output.xml`

再次运行 job002， 我们可以通过点击最新测试结果或使用下面链接来看到如下界面：

http://localhost:8080/job/job002/lastCompletedBuild/testReport/(root)/test_01_repos/



























