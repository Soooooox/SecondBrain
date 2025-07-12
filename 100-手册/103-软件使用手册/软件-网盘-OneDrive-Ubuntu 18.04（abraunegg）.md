# 软件-网盘-OneDrive-Ubuntu 18.04（abraunegg）

**备注**：针对 abraunegg 仓库版本的 OneDrive

## OneDrive 安装

1. 打开命令行，安装必要工具

    ```sh
    sudo apt install build-essential
    sudo apt install libcurl4-openssl-dev
    sudo apt install libsqlite3-dev
    sudo apt install pkg-config
    sudo apt install git
    ```

2. 切换到下载路径，并克隆 OneDrive 软件仓库

    ```sh
    cd ~/Downloads
    git clone https://github.com/abraunegg/onedrive.git
    ```

3. 将 OneDrive 软件移动到安装路径，我选择 `/opt/`

    ```sh
    sudo mv onedrive /opt/
    ```

4. 切换到安装路径，并安装依赖

    ```sh
    cd /opt/onedrive
    sudo wget https://netcologne.dl.sourceforge.net/project/d-apt/files/d-apt.list -O /etc/apt/sources.list.d/d-apt.list
    sudo apt-get update --allow-insecure-repositories
    sudo apt-get -y --allow-unauthenticated install --reinstall d-apt-keyring
    sudo apt-get update && sudo apt-get install dmd-compiler dub
    ```

5. 编译安装 OneDrive

    ```sh
    ./configure
    make
    sudo make install
    ```

6. 首次运行 OneDrive，进行用户绑定

    ```sh
    onedrive
    ```

   - 启动以后，出现 `Authorize this app visiting:`，打开链接进行授权
   - 授权以后，复制授权以后的网址到 `Enter the response uri:`
   - 等待 OneDrive 成功连接

注意：

- 同步位置：`~/OneDrive`

## OneDrive 操作

### 操作 1：用户绑定

1. 终端输入 `onedrive`，出现以下信息：

    ```sh
    [user@hostname ~]$ onedrive

    Authorize this app visiting:

    https://.....

    Enter the response uri:

    ```

2. 进入 `Authorize this app visiting:` 后的链接，进行用户登陆授权

3. 等登陆到最后，不加载任何东西时，将此页面链接复制到刚刚终端 `uri:` 下面

4. 出现以下界面说明绑定成功：

    ```sh
    Application has been successfully authorised, however no additional command switches were provided.

    Please use 'onedrive --help' for further assistance in regards to running this application.
    ```

### 操作 2：同步特定文件夹

```sh
onedrive --synchronize --single-directory '<dir_name>'
```

- 参数解释：`'<dir_name>'`：为 OneDrive 云盘下的文件夹路径

    <details>
    <summary>文件夹路径例子</summary>

    `Documents/Note/SecondBrain` 就是我 Onedrive 下的 Documents 文件夹下 Note 文件夹下的 Secondrain 文件夹

    </details>

- 保存路径：一般保存到 `Home/User_name/Onedrive` 文件夹下面

- 快速进行同步操作： 编写脚本运行

    ```sh
    #!/bin/bash
    onedrive --synchronize --single-directory Documents/Note/SecondBrain
    ```

    以上脚本是同步特定文件夹下的文件

## 参考

- 整体：<https://github.com/abraunegg/onedrive/>
- `OneDrive 安装`：[How to Sync Microsoft OneDrive with Ubuntu 18.04](https://gist.github.com/starlinq/0f98c6d9339497bb8ac42d67f66f60eb)
