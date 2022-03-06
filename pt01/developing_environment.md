# 开发环境配置与mod信息

------

这一节将会介绍forge文件夹下相关文件的配置以及作用。

首先是目录下的`src`文件夹，这里保存了你的模组的代码和资源文件。`main`文件夹下保存了模组的代码，`test`用来保存测试的代码。打开`main/java`文件夹可以看到forge提供了一个示例模组`examplemod`，将其删除，并且新建一个你自己的模组文件夹，命名规则为`<你的域名的倒写>.mod名称`。如果你没有域名，可以采用用户名等其他名称。我这里创建的是`lcyzsdh.phoenixcode`。请注意大小写，Java包名称建议全为小写。

![image-20220306163334571](https://s2.loli.net/2022/03/06/IvsBkrPgaFiAGxq.png)

创建完成后，在`phoenixcode`包下新建一个Java类，名字为`PhoenixCode`（具体的命名规则请参考第二章第四节）。

这个就是我们模组的主类。在类名上添加`@Mod`注释，告诉Forge这是我们模组的主类

`main/java/lcyzsdh/phoenixcode/PhoenixCode.java`:

```java
import net.minecraftforge.fml.common.Mod;

@Mod("phoenixcode")
public class PhoenixCode {
}
```

`@Mod`后的字符串代表了你的`modid`，这是你的模组唯一的id,将你的模组和其他的模组区分开来。`modid`在整个模组中都应该保持一致，不允许大写字符或者空格，注意和模组名称区分开来。

接下来我们要配置`resources/META-INF`下的`mods.toml`文件，这里保存了你的模组相关信息。具体的配置项目如下：

|     选项      | 是否必填 |                             描述                             |
| :-----------: | :------: | :----------------------------------------------------------: |
|   modLoader   |    是    |                  模组的加载方式，默认值即可                  |
| loaderVersion |    是    |                  模组加载的版本，默认值即可                  |
|    license    |    是    |  模组的许可证，可在[这里](https://choosealicense.com/)找到   |
|     modId     |    是    |       模组的唯一id，请全部小写,保持和项目文件中的一致        |
|    version    |    是    |  模组版本号，保持默认值即可，会自动和项目文件中的版本号同步  |
|  displayName  |    是    |                          模组的名称                          |
| updateJSONURL |   可选   | 模组更新链接，具体写法可参照[Forge文档](https://mcforge.readthedocs.io/en/1.16.x/gettingstarted/autoupdate/) |
|  displayURL   |   可选   |                         模组展示网站                         |
|   logoFile    |   可选   |                           模组logo                           |
|    credits    |   可选   |                        模组的鸣谢名单                        |
|    authors    |   可选   |                          模组的作者                          |
|  description  |    是    |                          模组的描述                          |

以上标记为必填的选项请根据自己的内容填写，其他内容选填，下面是我的`mods.toml`文件：

`main/resources/META-INF/mods.toml`<部分>:

```toml
modLoader="javafml" 
loaderVersion="[36,)" 
license="GNU GPLv3"
[[mods]]
modId="phoenixcode" 
version="${file.jarVersion}" 
displayName="PhoenixCode"
authors="lcyzsdh" 
description='''
A Minecraft 1.16.5 modding tutorial.
'''

```

填写完自己模组的内容以后，请将`mods.toml`文件剩下部分中的`examplemod`字段改为自己的`modid`。

------

接下来，请打开项目目录下的`build.gradle`文件，如果你对Gradle了解，应该知道这是Gradle项目的项目文件，当然你从未接触过也没关系，我们一起来看：

首先`buildscript`部分是你的模组构建的依赖部分，如果你的模组需要依赖于其他的模组，可以在这里添加相关的配置，Gradle将会自动为你下载这些依赖，我们暂时不会用到。

往下你会看到以下代码，请将其修改为你自己的内容。其中的`version`代表了你模组的版本号，具体的版本号规范请见。

`build.gradle`<部分>：

```
version = '1.0'
group = 'lcyzsdh.phoenixcode'
archivesBaseName = 'phoenixcode'
```

