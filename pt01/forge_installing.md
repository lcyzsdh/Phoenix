# **Forge环境部署**
------

## **开始之前**

在开始之前，你需要先下载以下内容：

- JDK8：[Oracle官网](https://www.oracle.com/java/technologies/javase/javase8u211-later-archive-downloads.html) 或者 [OpenJDK](https://adoptopenjdk.net/?variant=openjdk8&jvmVariant=hotspot) ，下载后请安装并自行配置环境变量

- [Forge MDK 1.16.5 36.2.20](https://files.minecraftforge.net/net/minecraftforge/forge/index_1.16.5.html)：下载后请解压到不含中文和特殊符号的文件夹

- [IntelliJ IDEA 社区版 2021.3.1](https://www.jetbrains.com/idea/download/#section=windows)：下载后请安装，可自行上网寻找相关的配置、热键教程

推荐使用 IDEA 作为模组开发的 IDE。当然，Forge 本身也添加了对 Eclipse 与 VS code 的支持，你也可以选择使用，但IDEA的操作以及对Gradle的功能集成较好。若无特殊说明，本教程之后的操作都以IDEA为例。

## **部署Forge开发环境**

开发环境的配置依赖于Forge开发的一个叫ForgeGradle的Gradle工具(以下简称FG)，可以用来编译、反编译，打包模组，安装前置依赖以及帮助我们构建。

首先，请确保你的Forge目录之下包含以下文件(本教程示例代码文件名为`PhoenixCode`，下同)：
`PhoenixCode/<部分>`：

```
gradle/...
build.gradle
gradle.properties
gradlew
gradlew.bat
src/...
```
关于FG以及这些文件的具体作用将于第二章介绍。

打开IDEA，在开始界面选择`Open or Import`,选择刚刚解压的文件夹下的`build.gradle`文件，选择`Open As Project`打开。

成功导入项目之后，IDEA便会自动的进行Gradle构建,从forge以及mc的海外服务器缓慢的(?)下载文件。根据所在的地区以及网络的原因，构建的时间短则几分钟，长则几小时。

构建有很大的可能失败，我在这里提供了如下几种加快配置的方案：

- 如果你有代理，可以为gradle配置代理，请自行上网搜索配置方法。

- ~~FledgeXu提供了一个ForgeGradle的fork ForgeGradleCN，添加了国内的下载源，具体配置见[此文](https://www.mcbbs.net/thread-1076799-1-1.html)。~~(好像因为FG版本更新挂了？)

- 可以采用Lss233搭建的镜像加快构建，具体配置见[此文](https://www.mcbbs.net/thread-800729-1-1.html)。可以加快下载gradle和maven仓库的速度。但mc本体等资源的下载由FG在代码里写死了，仍然会拖慢构建的速度。


- 如果上述办法都不可行，请采用耗子的[离线包](https://www.mcbbs.net/thread-896542-1-1.html)并按照提示安装。


当然不是百分之百的构建失败的原因都是由网络引起的，尝试删除用户文件夹下的`.gradle`文件夹可能可以解决非网络相关的失败问题。

如果上述配置一切顺利，那么在最后你可以看到`BUILD SUCCESSFUL`提示，说明导入成功。出现黄色的感叹号警示说明你当前使用的是官方映射表，可以忽略。

![image-20220227163754417](https://s2.loli.net/2022/02/27/ru6lA4vxf1dVcUN.png)

**恭喜你，已经成功配置Forge开发环境！**

## **启动器相关设置**

Gradle启动速度较慢，打开IntelliJ的设置，找到`Gradle`页，将`使用此工具构建和运行`的值改为`IntelliJ IDEA`并保存。

![image-20220227164359623](https://s2.loli.net/2022/02/27/DnXug3sbPl2A9Ni.png)

设置完成后，点击运行右侧的`Gradle`面板中的`Tasks`，`fg_runs`下的`genIntelliJRuns`，会自动下载运行剩余所需的依赖文件，同样在完成之后可以看到`BUILD SUCCESSFUL`的提示。

![image-20220306153321422](https://s2.loli.net/2022/03/06/TlC3fcia91LVZSQ.png)

然后选择运行任务中的`runClient`任务(不是那个Gradle的任务)。可能会有一段等待的时间，可以看到mc成功启动了。

![image-20220306154114754](https://s2.loli.net/2022/03/06/DjMkaREiYIBC6nF.png)

-----

## **附录：其他相关配置**

#### 启动客户端配置

在运行启动客户端的任务时，Gradle会先运行检查更新等在大多数情况下不必要的操作，可以选择去掉。

请在确保至少已经成功运行过一遍`runClient`任务后，打开`运行`选项卡 -> `编辑配置`选项，删除"启动前"中的Gradle任务(下图中划线部分)。

![image-20220306155213126](https://s2.loli.net/2022/03/06/XqHWSfzoDZGIgUO.png)

可以加快客户端的启动速度。

#### IDEA切换成中文

在插件中搜索"Chinese"，可以找到中文语言包，下载即可。