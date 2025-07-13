# 软件-下载器-qBittorrent-03-使用方法

## 操作 1：RSS订阅

1. 视图开启 `RSS订阅器`

    <img src="https://raw.githubusercontent.com/Soooooox/Image-Hosting-Service/main/20240605094951.png" alt="20240605094951" width=200>

2. 进入 `RSS订阅器`，`新 RSS订阅`

    <img src="https://raw.githubusercontent.com/Soooooox/Image-Hosting-Service/main/20240605095150.png" alt="20240605095150" width=300>

    <details>
    <summary>订阅效果</summary>

    <img src="https://raw.githubusercontent.com/Soooooox/Image-Hosting-Service/main/20240605104734.png" alt="20240605104734" width=700>

    </details>

    <details>
    <summary>RSS订阅源获取</summary>

    1. 进入BT网站，搜索需要的资源
    2. 点击 `RSS订阅图标`

        <img src="https://raw.githubusercontent.com/Soooooox/Image-Hosting-Service/main/20240605095431.png" alt="20240605095431" width=200>

    3. 复制上一步骤（第 2 步骤）新打开的网站地址（RSS 订阅地址）

    </details>

3. 进入 `设置`，点击 `RSS` 的 `修改自动下载规则`，进入 `RSS下载器`

    <img src="https://raw.githubusercontent.com/Soooooox/Image-Hosting-Service/main/20240605104809.png" alt="20240605104809" width=500>

4. 新建下载规则

    <img src="https://raw.githubusercontent.com/Soooooox/Image-Hosting-Service/main/20240605104858.png" alt="20240605104858" width=200>

5. 选择 RSS 订阅源，并设置规则定义

    <img src="https://raw.githubusercontent.com/Soooooox/Image-Hosting-Service/main/20240605105159.png" alt="20240605105159" width=500>

    正则表达式：用于筛选订阅源的资源

    分类和保存：对资源进行分类标签，保存至不同文件夹

6. 点击关闭，即可进行订阅自动下载

## 操作 2：添加Tracker

<img src="https://raw.githubusercontent.com/Soooooox/Image-Hosting-Service/main/20230810162001.png" alt="20230810162001" width=600>

**tracker 源**：[tracker-source](https://github.com/XIU2/TrackersListCollection/tree/master#tracker-source)

## 操作 3：qBittorrent 数据迁移

**迁移的数据**：

1. **种子列表信息**：在 `C:\Users\用户名\AppData\Local\qBittorrent\BT_backup` 文件夹下（Windows 端）
2. **RSS 订阅**: 在 `C:\Users\用户名\AppData\Roaming\qBittorrent\rss\` 文件夹下（Windows 端）

   - `download_rules.json`：RSS 下载规则
   - `feeds.json`：RSS 订阅源消息列表

3. **qBittorrent 设置**：在 `C:\Users\用户名\AppData\Roaming\qBittorrent\` 文件夹下（Windows 端）

   - `qBittorrent.ini`：qBittorrent 的设置信息

## 操作 4：换主题

**主题链接**：[List of known qBittorrent themes](https://github.com/qbittorrent/qBittorrent/wiki/List-of-known-qBittorrent-themes)

1. 下载主题文件到 qBittorrent 软件文件夹下

2. 进入 `设置` 的 `行为`，点击 `使用自定义界面主题`，选择相应主题文件

    <img src="https://raw.githubusercontent.com/Soooooox/Image-Hosting-Service/main/20240605112902.png" alt="20240605112902" width=500>

3. 点击应用，并重启软件

## 操作 5：IP 过滤与恶意客户端

1. 添加 IP 过滤

    <img src="https://raw.githubusercontent.com/Soooooox/Image-Hosting-Service/main/20240605130010.png" alt="20240605130010" width=500>

    IP 屏蔽段：<https://docs.qq.com/doc/DQnJBTGJjSFZBR2JW>

2. 屏蔽恶意客户端

    将下面 `peer_blacklist.txt` 文件放在 `C:\Users\用户名\AppData\Local\qBittorrent` 里

    ```txt
    -GT0003- github.com/anacrolix/torrent\s\(devel\)\s\(anacrolix/torrent\sunknown\)
    -DT0001- .*
    -HP0001- .*
    -XM0001- .*
    ```

3. `设置`->`高级`->`上传链接策略`：改为 `反吸血`

## 操作 6：手动屏蔽 IP 地址导出

1. `设置`->`连接`->`IP 过滤`
2. 点击 `手动屏蔽 IP 地址...`
3. 将其中的 IP 地址复制到一个文档进行保存

## 操作 7：Web UI

1. `设置`->`Web UI`
2. 开启并自定义用户名和密码

    <img src="https://raw.githubusercontent.com/Soooooox/Image-Hosting-Service/main/20250222150341.png" alt="20250222150341">

3. 进入浏览器，输入：`localhost:端口号`，如 `localhost:8080`

## 操作 8：配合 PeerBanHelper 反吸血

1. 下载并安装 [PeerBanHelper](https://github.com/PBH-BTN/PeerBanHelper/releases/)，安装的插件内容全选
2. 打开 PeerBanHelper ( 无后缀名的 )
3. 等待 PeerBanHelper 进行初始化
4. 进行初始化设置：
   1. 设置一个随机的 token ( token 需要自行保存 )
   2. 添加下载器

        <img src="https://raw.githubusercontent.com/Soooooox/Image-Hosting-Service/main/20250222152838.png" alt="20250222152838">

        注意：最后需要点击 `测试下载器`，如果添加失败，可能原因是地址结尾是 `\`

## 参考

- `操作 1：RSS订阅`：[qBittorrent 如何自动追番](https://www.bilibili.com/video/BV1Bx4y1V7M4)
- `操作 2：添加Tracker`：[XIU2/TrackersListCollection](https://github.com/XIU2/TrackersListCollection/tree/master)
- `操作 3：qBittorrent 数据迁移`：
  - [qbittorrent 数据迁移](https://v2ex.com/t/852321)
  - [How to enter multiple RSS feeds?](https://forum.qbittorrent.org/viewtopic.php?p=41281&hilit=RSS+storage#p41281)
  - [[软件] 重装系统，QB里的种子怎么备份和恢复？](https://www.chiphell.com/thread-2458627-1-1.html)
  - [[软件] 请问重装系统后怎么恢复qBittorrent做种任务？](https://www.chiphell.com/forum.php?mod=viewthread&tid=2489912)
- `IP 过滤与恶意客户端`：
  - [关于QB恶意客户端及其IP的通用解决办法](https://www.tieba.com/p/8976433334)
  - [hp/torrent/v2.01是什么软件，对方下载速度快的离谱](https://tieba.baidu.com/p/9001972940)
  - [qbittorrent屏蔽anacrolix、dt、hp等吸血客户端](https://www.bilibili.com/read/cv32717071/)
  - [关于近期anacrolix等无限下载的BT工具的说明与对策](https://docs.qq.com/doc/DQnJBTGJjSFZBR2JW)
  - [利用路由器安全规则及第三方工具反PCDN放血·反吸血の不完全指南](https://www.bilibili.com/video/BV1Xb421J7ed/)
- `操作 7：Web UI`：<https://www.bilibili.com/video/BV1VyyUYVEMq?t=924.1>
- `操作 8：配合 PeerBanHelper 反吸血`：<https://www.bilibili.com/video/BV1VyyUYVEMq?t=984.1>
