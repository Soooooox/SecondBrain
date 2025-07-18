# 自定义头文件与源文件

## 文件结构

```plaintext
工作区
└── src
    └── 功能包
        ├── include
        │   └── 功能包名
        │       └── 头文件.h
        └── src
            ├── 源文件.cpp
            │
            └── 执行文件.cpp

```

## 流程

1. 编写头文件
2. 编写源文件
3. 编写可执行文件（需要运行的文件）
4. 修改 CMakeLists.txt 文件

## 头文件的编写

```c++
#ifndef _大写的头文件名称_H
#define _大写的头文件名称_H

函数或类声明等

#endif
```

## 注意

在 VScode 中，为了后续包含头文件时不抛出异常，请配置 `.vscode` 下 `c_cpp_properties.json` 的 `includepath` 属性

```json
"功能包的绝对路径/include/**"
```

## 源文件的编写

```c++
#include "功能包名/头文件.h"

函数实现
```

## 可执行文件的编写

```c++
#include "功能包名/头文件.h"

函数的调用等
```

## CMakeLists.txt 的配置

```txt
include_directories(

    include # 从本包的头文件路径中查寻和加载头文件
    ${catkin_INCLUDE_DIRS}
)

## 声明 C++ 库
add_library(库名称（自己命名）
  include/功能包名/头文件.h
  src/源文件.cpp
)

add_dependencies(库名称 ${${PROJECT_NAME}_EXPORTED_TARGETS} ${catkin_EXPORTED_TARGETS})

target_link_libraries(库名称
  ${catkin_LIBRARIES}
)
add_executable(执行文件名（自己命名） src/执行文件.cpp)

add_dependencies(执行文件名 ${${PROJECT_NAME}_EXPORTED_TARGETS} ${catkin_EXPORTED_TARGETS})

#此处需要添加之前设置的 head 库
target_link_libraries(执行文件名
  库名称
  ${catkin_LIBRARIES}
)
```

以下根据情况选择：（保守做法：始终包含这两行）

- `add_dependencies(库名称 ${${PROJECT_NAME}_EXPORTED_TARGETS} ${catkin_EXPORTED_TARGETS})`
- `add_dependencies(执行文件名 ${${PROJECT_NAME}_EXPORTED_TARGETS} ${catkin_EXPORTED_TARGETS})`