# 软件-网盘-OneDrive-Windows

## Proxifier 设置代理端口

1. 用管理员身份运行软件
   - 注意：第一次启动使用管理员身份，如果想要开机启动，后面需要取消勾选管理员身份运行
2. 输入注册码，最好是勾选 `All userss on this computer(require administrator)`

   - 免安装版本：`L6Z8A-XY2J4-BTZ3P-ZZ7DF-A2Q9C`
   - 安装版本：`5EZ8G-C3WL5-B56YG-SCXM9-6QZAP`
   - Mac 版本：`P427L-9Y552-5433E-8DSR3-58Z68`

3. `Profile`->`Proxy Servers`，添加 HTTPS 和 Socks5 代理配置

    <img src="https://raw.githubusercontent.com/Soooooox/Image-Hosting-Service/main/20240722124500.png" alt="20240722124500">

4. `Profile`->`Proxification Rules`，配置软件代理规则

    <img src="https://raw.githubusercontent.com/Soooooox/Image-Hosting-Service/main/20240722124716.png" alt="20240722124716">

    其中，点击 `Browse`，并找到 `onedrive.exe` 执行文件：

      - WIN10：`C:\Program Files\Microsoft OneDrive\` 文件夹下
      - WIN11：`%localappdata%\Microsoft\OneDrive\` 文件夹下（与 WIN10 通用）

5. 把 `default` 的 `action` 设置为 `direct`（所有程序不全都通过代理）

下载地址：<https://www.proxifier.com/download/>

<details>
<summary>问题：proxifier 和 chrome 不能共存</summary>

解决办法：安装 proxifier 的安装版，不使用便携版

</details>

## 开启多线程

1. 进入以下文件：`C:\Users\用户名\AppData\Local\Microsoft\OneDrive\settings\Personal\global.ini`

    或者直接地址栏输入：`%localappdata%\Microsoft\OneDrive\settings\Personal\global.ini`

2. 在打开的文件的第一行添加以下代码

    ```txt
    numberOfConcurrentUploads=3
    ```

    数值项即为线程数，最小值为 1，最大值为 3

## 参考

- 整体：[科学地让 OneDrive 飞，下载速度 5Mb/s](https://blog.tcpsoft.app/2020/03/let-onedrive-fly-scientifically/)
- `Proxifier 注册码`：[Proxifier 注册码序列号_proxifier 序列号](https://blog.csdn.net/weixin_43845335/article/details/88396826)
