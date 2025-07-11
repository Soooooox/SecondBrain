# package.xml

## package.xml 概述

`package.xml` 简称包清单，定义了功能包的属性，是功能包的描述信息（声明包的元数据和依赖关系）

### 功能包的属性

1. 功能包名称
2. 版本号
3. 作者
4. 维护者
5. 对 catkin 软件包和其他软件包的依赖关系

### package.xml 格式

由于历史遗留问题，目前有两种格式：

1. 旧版本（传统）
2. 新版本（推荐）

结构：

- 基础结构
  - 必要标签
  - 依赖

## 基础结构

以 `<package>` 标签作为根标签

**旧版本**：

```xml
<package>

</package>
```

**新版本**：

```xml
<package format="2">

</package>
```

## 必要标签

必要标签包含在 `<package> </package>` 内部

|标签|含义|
|:-:|:-:|
|`<name>`|功能包的名称（**必须与功能包的名称一致**）|
|`<version>`|功能包的版本号（必须是 3 个点分隔整数）|
|`<description>`|功能包内容的描述|
|`<maintainer>`|功能包的维护者|
|`<license>`|软件许可证|

<details>
<summary>例子</summary>

```xml
<package>
  <name>foo_core</name>
  <version>1.2.4</version>
  <description>
  This package provides foo capability.
  </description>
  <maintainer email="ivana@willowgarage.com">Ivana Bildbotz</maintainer>
  <license>BSD</license>
</package>
```

</details>

## 依赖

指明对其他包的依赖关系

### 旧版本依赖

|依赖标签|内容|
|:-:|:-:|
|`<buildtool_depend>`|编译包的工具|
|`<build_depend>`|编译时的依赖|
|`<run_depend>`|运行时的依赖|
|`<test_depend>`|单元测试的附加依赖项|

<details>
<summary>旧版本的依赖例子</summary>

```xml
<package>
  <buildtool_depend>catkin</buildtool_depend>

  <build_depend>message_generation</build_depend>
  <build_depend>roscpp</build_depend>
  <build_depend>std_msgs</build_depend>

  <run_depend>message_runtime</run_depend>
  <run_depend>roscpp</run_depend>
  <run_depend>rospy</run_depend>
  <run_depend>std_msgs</run_depend>

  <test_depend>python-mock</test_depend>
</package>
```

</details>

<!-- </br> -->

### 新版本依赖

`<depend>` 指定依赖项为编译、导出、运行需要的依赖

说明：`<depend>` = `<build_depend>` + `<build_export_depend>` + `<exec_depend>`（三者之和效果）

|依赖标签|内容|
|:-:|:-:|
|`<buildtool_depend>`|构建包的工具，一般为`catkin`|
|`<build_depend>`|编译时的依赖|
|`<build_export_depend>`|编译导出时的依赖|
|`<exec_depend>`|运行时的依赖|
|`<test_depend>`|单元测试的附加依赖项|
|`<doc_depend>`|生成文档所需的文档工具|

**注意**：前四个是必要，`导出时的依赖` 可自行选择（不是必要）

<details>
<summary>新版本的依赖例子</summary>

```xml
<package format="2">
  <buildtool_depend>catkin</buildtool_depend>

  <depend>roscpp</depend>
  <depend>std_msgs</depend>

  <build_depend>message_generation</build_depend>

  <exec_depend>message_runtime</exec_depend>
  <exec_depend>rospy</exec_depend>

  <test_depend>python-mock</test_depend>

  <doc_depend>doxygen</doc_depend>
</package>
```

</details>

## 依赖项

依赖项是一个功能包

因这个包被其他功能包共同需要使用到，不如把它封装成依赖项，避免重复

安装 ros 时，会安装一些基础包

基础包存放在 `/opt/ros/<ROS版本>/share`

基础包软件来源：

- `sudo apt-get install ros-<ROS版本>-desktop-full`：基础包
- `sudo apt-get install ros-<ROS版本>-xxx`：独立扩展包

基础包和工作空间的包区别：

- 基础包是已经编译好的，可以直接使用
- 工作空间的包是源码，需要编译使用

## 参考链接

- [package.xml](http://wiki.ros.org/catkin/package.xml)
- [package.xml中文翻译](https://zhuanlan.zhihu.com/p/669588339)
- [package.xml使用说明](https://www.cnblogs.com/lisongzzx/p/13652469.html)
