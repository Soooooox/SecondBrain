# 软件-网盘-OneDrive-Ubuntu 20.04 (abraunegg)

## OneDrive 安装

1. 添加 OpenSuSE Build Service 存储库发布密钥

    ```sh
    wget -qO - https://download.opensuse.org/repositories/home:/npreining:/debian-ubuntu-onedrive/xUbuntu_20.04/Release.key | sudo apt-key add -
    ```

2. 添加 OpenSuSE Build Service 存储库

    ```sh
    echo 'deb https://download.opensuse.org/repositories/home:/npreining:/debian-ubuntu-onedrive/xUbuntu_20.04/ ./' | sudo tee /etc/apt/sources.list.d/onedrive.list
    ```

3. 更新 apt 包

    ```sh
    sudo apt-get update
    ```

4. 安装 OneDrive

    ``` sh
    sudo apt install --no-install-recommends --no-install-suggests onedrive
    ```

    有 BUG 使用以下链接：[issues](https://github.com/abraunegg/onedrive/blob/master/docs/ubuntu-package-install.md#known-issues-with-installing-from-the-above-packages)

5. 首次启动 OneDrive，进行用户绑定

    ```sh
    onedrive
    ```

   - 启动以后，出现 `Authorize this app visiting:`，打开链接进行授权（建议关闭梯子进行授权）
   - 授权以后，复制授权以后的网址到 `Enter the response uri:`
   - 等待 OneDrive 成功连接

注意：

- 同步位置：`~/OneDrive`

## Onedrive 操作

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
onedrive --sync --single-directory '<dir_name>'
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
    onedrive --sync --single-directory Documents/Note/SecondBrain
    ```

    以上脚本是同步特定文件夹下的文件

## 参考

- 整体：<https://github.com/abraunegg/>
