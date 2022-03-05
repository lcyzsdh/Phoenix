# **Forge环境部署**

## **开始之前**

你需要先下载以下内容：

- JDK8，[Oracle官网](https://www.oracle.com/java/technologies/javase/javase8u211-later-archive-downloads.html) 或者 [OpenJDK](https://adoptopenjdk.net/?variant=openjdk8&jvmVariant=hotspot) ：下载后请安装并自行配置环境变量

- [Forge MDK 1.16.5 36.2.20](https://files.minecraftforge.net/net/minecraftforge/forge/index_1.16.5.html)：下载后请解压到不含中文和特殊符号的文件夹

- [IntelliJ IDEA 社区版 2021.3.1](https://www.jetbrains.com/idea/download/#section=windows)：下载后请安装，可自行上网寻找相关的配置、快捷键教程

推荐使用 IDEA 作为模组开发的 IDE。当然，Forge 本身也添加了对 Eclipse 与 VS code 的支持，你也可以选择使用，但IDEA的操作以及对Gradle的集成较好。若无特殊说明，本教程之后都以IDEA为例。

## **部署Forge开发环境**

开发环境的配置依赖于Forge开发的一个叫ForgeGradle的Gradle工具，可以用来打包模组，安装前置依赖以及帮助我们构建。

首先，请确保你的Forge目录之下包含以下文件(本教程示例代码文件名为`PhoenixCode`，下同)：
`PhoenixCode/`

```
gradle/...
build.gradle
gradle.properties
gradlew
gradlew.bat
src/...
```
关于FG以及这些文件的具体作用将于第二章介绍。

打开IDEA，在开始界面选择`Open or Import`,选择刚刚解压的文件夹下的`build.gradle`文件，选择`Open As Project`。

成功打开之后，IDEA便会自动的进行Gradle构建,从forge以及mc的海外服务器缓慢的(?)下载文件。根据所在的地区以及网络的原因，构建的时间短则几分钟，长则几小时。

构建极有可能失败，如果你有代理，可以为gradle配置代理。

~~FledgeXu提供了一个ForgeGradle的fork ForgeGradleCN，配置见[此文](https://www.mcbbs.net/thread-1076799-1-1.html)。~~(好像因为FG版本更新挂了？)

也可以采用Lss233搭建的镜像加快构建，具体配置见[此文](https://www.mcbbs.net/thread-800729-1-1.html)。可以加快下载gradle和maven仓库的速度。

如果上述办法都不可行，请采用耗子的[离线包](https://www.mcbbs.net/thread-896542-1-1.html)并按照提示安装。

当然不是百分之百的原因都是由网络引起的，尝试删除用户文件夹下的`.gradle`文件夹可以解决非网络相关的失败问题。

如果上述配置一切顺利，那么在最后你可以看到`BUILD SUCCESSFUL`提示，说明导入成功！

![image-20220227163754417](https://s2.loli.net/2022/02/27/ru6lA4vxf1dVcUN.png)

恭喜你，已经成功配置Forge开发环境！

## 相关设置

Gradle启动速度较慢，打开IntelliJ的设置，找到`Gradle`页，将`使用此工具构建和运行`改为`IntelliJ IDEA`并保存。

![image-20220227164359623](https://s2.loli.net/2022/02/27/DnXug3sbPl2A9Ni.png)

设置完成后，点击运行右侧的`Gradle`面板中的`Tasks`，`fg_runs`下的`genIntelliJRuns`。