# 软件-同步-FreeFileSync

## 下载与安装

下载地址：<https://freefilesync.org/download.phps>

Linux 端安装：官方地址下载压缩包，解压得到安装脚本，运行安装脚本，跟着提示安装

## 界面介绍

### 比较与同步界面

<img src="https://raw.githubusercontent.com/Soooooox/Image-Hosting-Service/main/20231030190430.png" alt="20231030190430" width=500>

### 状态栏界面

<img src="https://raw.githubusercontent.com/Soooooox/Image-Hosting-Service/main/20231030192745.png" alt="20231030192745" width=500>

### 配置界面

<img src="https://raw.githubusercontent.com/Soooooox/Image-Hosting-Service/main/20231030202645.png" alt="20231030202645" width=250>

## 路径配置

### 基本路径配置

<img src="https://raw.githubusercontent.com/Soooooox/Image-Hosting-Service/main/20231030183712.png" alt="20231030183712" width=600>

### 多路径配置

<img src="https://raw.githubusercontent.com/Soooooox/Image-Hosting-Service/main/20231030184623.png" alt="20231030184623" width=600>

同一行，路径是一个同步对；不同行路径不能进行同步

## 双向差异处理

<details>
<summary>名词说明</summary>

<img src="https://raw.githubusercontent.com/Soooooox/Image-Hosting-Service/main/20231030182328.png" alt="20231030182328" width=600>

我们将**路径1**的文件夹称为**左侧**，**路径2**的文件夹称为**右侧**（用于更好说明区分）

</details>

### 差异面板图介绍

<img src="https://raw.githubusercontent.com/Soooooox/Image-Hosting-Service/main/20231030185737.png" alt="20231030185737" width=600>

- 比较结果类型：说明比较以后，两侧文件的差异结果类型
- 比较结果差异动作：说明比较差异后，需要执行的文件动作，即 `删除`、`更新`、`复制`、`冲突`、`不执行`

**补充**：将鼠标移到差异动作可以选择其他动作进行执行

**双向差异的多种情况**：

1. 左侧增加文件  or  右侧增加文件
2. 左侧修改文件  or  右侧修改文件
3. 左侧删除文件  or  右侧删除文件
4. 左右侧对同一文件进行不同修改

### 情况 1：左侧增加文件  or  右侧增加文件

<img src="https://raw.githubusercontent.com/Soooooox/Image-Hosting-Service/main/20231030190112.png" alt="20231030190112" width=600>

对于新增加的文件，同步动作一般为**复制**到未新增的路径上

### 情况 2：左侧修改文件  or  右侧修改文件

<img src="https://raw.githubusercontent.com/Soooooox/Image-Hosting-Service/main/20231030190817.png" alt="20231030190817" width=600>

对于修改的文件，同步动作一般为**更新**另一路径下的文件

### 情况 3：左侧删除文件  or  右侧删除文件

<img src="https://raw.githubusercontent.com/Soooooox/Image-Hosting-Service/main/20231030191030.png" alt="20231030191030" width=600>

对于删除的文件，同步动作一般为**删除**另一路径下的文件

### 情况 4：左右侧对同一文件进行不同修改

<img src="https://raw.githubusercontent.com/Soooooox/Image-Hosting-Service/main/20231030191545.png" alt="20231030191545" width=300>

<img src="https://raw.githubusercontent.com/Soooooox/Image-Hosting-Service/main/20231030191215.png" alt="20231030191215" width=600>

对于两侧修改同一文件的行为，同步动作一般为冲突，这种情况下，根据自己的选择来进行 `更新左侧`、`不执行`、`更新右侧`

### 干预同步动作

<img src="https://raw.githubusercontent.com/Soooooox/Image-Hosting-Service/main/20231030191959.png" alt="20231030191959" width=700>

说明：将鼠标放到同步动作上，往左一点会出现另一个同步动作，往右一点会出现另一个同步动作，放在中间出现不执行同步动作，这样就进行动作的相应干预，可以针对任何同步动作

## 同步的模式

1. 双向同步：严格意义上的同步，最新修改文件覆盖原文件
2. 镜像同步：右侧的文件完全与左侧保持一致，右侧的文件变化不影响左侧文件
3. 增量同步：左侧新增和已更新文件会复制到右侧，左侧删除文件不会影响右侧，右侧的文件变化不影响左侧
4. 自定义同步

<img src="https://raw.githubusercontent.com/Soooooox/Image-Hosting-Service/main/20231030193513.png" alt="20231030193513" width=500>

### 删除与覆盖的选择

对于删除与覆盖，可以选择放到回收站（推荐）、永久删除/覆盖、历史版本（推荐）

<img src="https://raw.githubusercontent.com/Soooooox/Image-Hosting-Service/main/20231030204009.png" alt="20231030204009">

## 过滤器

<img src="https://raw.githubusercontent.com/Soooooox/Image-Hosting-Service/main/20231030200700.png" alt="20231030200700" width=300>

### 包括内容

<img src="https://raw.githubusercontent.com/Soooooox/Image-Hosting-Service/main/20231030200911.png" alt="20231030200911" width=300>

包括部分使用[通配符](https://freefilesync.org/manual.php?topic=exclude-files)，可添加需要同步的文件

<img src="https://raw.githubusercontent.com/Soooooox/Image-Hosting-Service/main/20231030201827.png" alt="20231030201827" width=500>

### 排除内容

<img src="https://raw.githubusercontent.com/Soooooox/Image-Hosting-Service/main/20231030201416.png" alt="20231030201416" width=400>

排除部分参考[示例](https://freefilesync.org/manual.php?topic=exclude-files)，可进行排除哪些文件夹和哪些文件进行同步

## 配置

### 配置的保存

<img src="https://raw.githubusercontent.com/Soooooox/Image-Hosting-Service/main/20231030202846.png" alt="20231030202846" width=600>

### 配置的切换

<img src="https://raw.githubusercontent.com/Soooooox/Image-Hosting-Service/main/20231030202928.png" alt="20231030202928" width=300>

### 批量处理

<img src="https://raw.githubusercontent.com/Soooooox/Image-Hosting-Service/main/20231030203024.png" alt="20231030203024" width=500>

保存为一个脚本文件，点击可以进行批量处理，可用于定时的批量处理

### 定时处理

使用RealTimeSync进行定时批量处理：

<img src="https://raw.githubusercontent.com/Soooooox/Image-Hosting-Service/main/20231030203624.png" alt="20231030203624" width=400>

说明：下载完FreeFileSync会有FreeFileSync（绿色）、RealTimeSync（红色）两个软件

## 参考

- 整体：
  - [【14001】FreeFileSync](https://www.bilibili.com/video/BV18f4y1t7jS)
