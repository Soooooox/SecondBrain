# CMakeList.txt

## CMakeList.txt 概述

`CMakeLists.txt` 简称编译脚本，是 `CMake` 构建系统的配置文件，用于构建功能包

`CMakeLists.txt` 描述如何构建功能包

## 整体结构

|代码|结构含义|
|:-:|:-:|
|`cmake_minimum_required()`|CMake 版本（必要）|
|`project()`|功能包名称（必要）|
|`find_package()`|查找并加载外部依赖包（必要）|
|`add_message_files()` `add_service_files()` `add_action_files()`|添加 消息/服务/操作 文件（自定义消息时必要）|
|`generate_messages()`|生成消息文件（自定义消息时必要）|
|`catkin_package()`|声明 catkin 特定的构建信息（必要）|
|`include_directories()`|添加头文件包含路径（必要）|
|`add_library()`|构建库文件（有自定义头文件时必要）|
|`add_executable()`|构建可执行文件（C++ 文件作为执行文件时必要）|
|`add_dependencies()`|显式声明目标之间的依赖关系（自定义消息和动态库/自定义头文件时必要）|
|`target_link_libraries()`|将目标（可执行文件或库）链接到库（必要）|
|`catkin_python_setup()`|启用 Python 模块支持|
|`catkin_add_gtest()`|编译测试|
|`install()`|安装规则|

## 函数串联流程

1. 查找依赖：`find_package()` 查找所有需要的依赖包
2. 配置 catkin：`catkin_package()` 声明包的构建信息
3. 设置包含路径：`include_directories()` 设置头文件搜索路径
4. 构建库：`add_library()` 将源代码编译为库（如果有）
5. 构建可执行文件：`add_executable()` 将源代码编译为可执行文件
6. 指定构建顺序：`add_dependencies()` 声明构建顺序依赖
7. 链接库：`target_link_libraries()` 将可执行文件与需要的库链接

## cmake_minimum_required()

每个 `CMakeLists.txt` 文件必须以所需的 CMake 版本开始，Catkin 需要 2.8.3 或更高版本：

```xml
cmake_minimum_required(VERSION 2.8.3)
```

## project()

```xml
project(功能包名)
```

- 功能包名必须与对应的功能包名相同
- 可通过使用变量 `${PROJECT_NAME}` 引用功能包名

## find_package()

作用：查看并加载外部依赖包

写法一：

```xml
find_package(功能包名 REQUIRED)
```

- 作用：
  - 仅检查功能包的存在
  - 不加载任何组件
- 适用场景：只需要验证包是否存在，且不需要其特定功能模块
- 例子：如 `Eigen3`

写法二：

```xml
find_package(功能包名 REQUIRED COMPONENTS 组件名1 组件名2 ... 组件名n)
```

- 作用：
  - 检查功能包的存在，加载所选组件
  - 确保这些组件的头文件和库可用
- 适用场景：需要包的具体功能模块时
- 例子：如 `catkin` 的组件化设计（`roscpp`、`std_msgs` 等）

**加载依赖包用于本功能包的构建**：会定义一些变量，供后续 CMake 命令使用

1. 所查找功能包的头文件路径变量：`功能包名_INCLUDE_DIRS`
   - 作用：用于 `include_directories()`，使得编译器能找到依赖包的头文件
   - 用法：

      ```xml
      find_package(功能包名 REQUIRED)
      include_directories(${功能包名_INCLUDE_DIRS})
      ```

2. 所查找功能包的库文件路径：`功能包名_LIBRARIES`
   - 作用：用于 `target_link_libraries()`，链接依赖包的库文件
   - 用法：

      ```xml
      find_package(功能包名 REQUIRED)
      target_link_libraries(执行文件名 ${功能包名_LIBRARIES})
      ```

3. Catkin 特有的变量：`catkin_INCLUDE_DIRS`、`catkin_LIBRARIES`

    ```xml
    find_package(catkin REQUIRED COMPONENTS roscpp std_msgs)
    include_directories(${catkin_INCLUDE_DIRS})  # 包含所有依赖的头文件
    target_link_libraries(执行文件名 ${catkin_LIBRARIES})  # 链接所有依赖的库
    ```

## 自定义数据类型：消息/服务/操作

`.msg` 、 `.srv` 和 `.action` 文件被 ROS 包编译和使用之前需要一个特殊的预处理器构建步骤

宏的目的是生成特定于编程语言的文件，以便可以使用所选编程语言中的消息、服务和操作

### 处理消息、服务和操作的宏

- 消息：`add_message_files(...)`
- 服务：`add_service_files(...)`
- 操作：`add_action_files(...)`

这些宏后面必须跟调用生成消息文件的函数：`generate_messages( )`

### 使用结构

```xml
 find_package(catkin REQUIRED COMPONENTS message_generation ...)
 add_message_files(FILES xxx.msg ...)
 add_service_files(FILES xxx.srv ...)
 add_action_files(FILES xxx.action ...)
 generate_messages(DEPENDENCIES std_msgs ...)
 catkin_package(CATKIN_DEPENDS message_runtime ...)
 ...
```

- `find_package()` 的组件必须要有 `message_generation`
- `catkin_package()` 的 DEPENDS 依赖项必须要有 `message_runtime`

## catkin_package()

作用：主要用于解决以下 ROS 包构建中的三个核心问题

1. 依赖传递：声明本包对其他包的依赖关系，使依赖关系能正确传递给下游包
   - 确保下游包的 `find_package()` 能正确找到本包的头文件和库
2. 接口导出：定义本包对外提供的头文件和库文件
3. 构建隔离：确保包能独立构建，同时保持正确的依赖关系

```xml
catkin_package(
  INCLUDE_DIRS include
  LIBRARIES 库名称
  CATKIN_DEPENDS 组件名1 组件2 ... 组件名n
  DEPENDS 功能包名
)
```

**注意**：`库名称` 为 `add_library(库名称)` 的库名称

|参数|作用|
|:-:|:-:|
|`INCLUDE_DIRS`|本包对外提供的头文件目录 `include/`|
|`LIBRARIES`|本包对外提供的库文件（通过 `add_library()` 创建的）|
|`CATKIN_DEPENDS`|本包依赖的纯 Catkin 包|
|`DEPENDS`|本包依赖的非 Catkin 包|

**补充**：可以全不使用，需要使用哪个添加哪个

```xml
# 纯头文件库
catkin_package(
  INCLUDE_DIRS include
  CATKIN_DEPENDS 组件名1 组件2 ... 组件名n
)

# 带库的包
catkin_package(
  INCLUDE_DIRS include
  LIBRARIES 库名称
  CATKIN_DEPENDS 组件名1 组件2 ... 组件名n
  DEPENDS 功能包名
)

# 元包
catkin_package(
  METAPACKAGE TRUE
)
```

**时序位置**：

`catkin_package()` 必须在使用 `add_library()` 或 `add_executable()` 之前调用

```xml
find_package(catkin REQUIRED ...)  # (1) 先找依赖
catkin_package(...)                # (2) 声明本包信息
add_library(...)                   # (3) 然后构建
```

原因：需先知道本包的依赖，才能正确声明本包的信息，最后才能基于这些信息构建目标

## include_directories()

作用：指定头文件搜索路径

```xml
include_directories(
  include                  # 本包的头文件目录（可选）
  ${catkin_INCLUDE_DIRS}   # ROS 依赖包的头文件路径（必须）
  ${功能包_INCLUDE_DIRS}   # 第三方库的头文件路径（可选）
)
```

## add_library()

作用：将 `.cpp` 文件编译成库（静态库 `.a` 或动态库 `.so`）

**补充**：其依赖于 `include_directories()`，`add_library()` 在编译 `.cpp` 文件时，会使用 `include_directories()` 指定的路径来解析 `#include` 语句

```xml
add_library(库名称
  src/源文件1.cpp
  src/源文件2.cpp
  src/源文件n.cpp
)
```

**生成的库的用处**：

1. 本包的 `add_executable()` 目标：

    ```xml
    add_executable(执行文件名 src/执行文件.cpp)
    target_link_libraries(执行文件名 库名称)  # 链接本包生成的库
    ```

2. 其他 ROS 包（通过 `catkin_package()` 导出）使用结构

## add_executable()

作用：构建可执行文件

```xml
add_executable(执行文件名 src/执行文件.cpp)
```

## add_dependencies()

作用：用于显式声明目标之间的依赖关系，确保构建顺序的正确性

适用场景：当目标依赖 ROS 消息/服务、其他动态生成的文件或库时

解决的问题：

- 解决隐式依赖问题：当目标（如可执行文件）依赖于其他目标生成的文件（如 ROS 消息/服务/动态库），但 CMake 无法自动推断这种关系时，强制指定构建顺序。
- 确保文件生成优先：典型场景是确保 ROS 的 `.msg`/`.srv`/`.action` 文件先被编译成代码，再被其他目标使用。

在 ROS 构建流程中的位置：`add_dependencies()` 必须在 `add_executable()` 或 `add_library()` 之后调用

1. 定义目标：`add_executable()` 或 `add_library()`
2. 声明依赖：`add_dependencies()`
3. 链接库：`target_link_libraries()`

与 `target_link_libraries()` 的区别：即使通过 `target_link_libraries()` 链接了库，CMake 也可能无法自动推断构建顺序，仍需 `add_dependencies()`

## target_link_libraries()

作用：将可执行文件与它依赖的库进行链接

**编译与链接**：

- 编译：`add_executable()` 将 `.cpp` 文件编译成目标文件（`.o` 或 `.obj`），此时，代码中的函数调用只是符号引用（未确定实际地址）
- 链接：`target_link_libraries()` 将目标文件与库（`.so`/`.a`）绑定，解析符号引用
  - 如果是动态链接，可执行文件运行时还需要加载 `.so` 文件

## 初始建立的包的 CmakeLists.txt 的内容

```txt
cmake_minimum_required(VERSION 3.0.2)
project(功能包名)
find_package(catkin REQUIRED COMPONENTS
  roscpp
  rospy
  std_msgs
)
catkin_package(
#  INCLUDE_DIRS include
#  LIBRARIES admittance
#  CATKIN_DEPENDS roscpp rospy std_msgs
#  DEPENDS system_lib
)
include_directories(
# include
  ${catkin_INCLUDE_DIRS}
)
```

## 参考链接

- [CMakeLists.txt](http://wiki.ros.org/catkin/CMakeLists.txt)
- [CMakeList.txt 中文翻译](https://blog.csdn.net/jinking01/article/details/102891918)
- [【ROS 学习笔记】CMakeLists.txt 与 package.xml](https://zhuanlan.zhihu.com/p/94579820)

## 推荐阅读

- [“轻松搞定CMake”系列之find_package用法详解](https://blog.csdn.net/zhanghm1995/article/details/105466372)
