# 软件-网盘-OneDrive-Ubuntu 18.04（skilion）

**备注**：针对 abraunegg 仓库版本的 OneDrive

## OneDrive 的安装

1. 安装依赖

    ```bash
    sudo apt install git libcurl4-openssl-dev libsqlite3-dev
    sudo snap install --classic dmd
    ```

2. 编译安装

    ```bash
    git clone https://github.com/skilion/onedrive.git
    cd onedrive
    make
    sudo make install
    ```

    注意：需要将下载的 Onedrive 移动到自己装软件的文件夹下进行编译（`make`）等操作

3. 首次运行 OneDrive，进行用户绑定

    ```sh
    onedrive
    ```

   - 启动以后，出现 `Authorize this app visiting:`，打开链接进行授权
   - 授权以后，复制授权以后的网址到 `Enter the response uri:`
   - 等待 OneDrive 成功连接

4. 复制设置

    ```bash
    mkdir -p ~/.config/onedrive
    cp ./config ~/.config/onedrive/config
    ```

    `config` 文件：

    - `sync_dir`：同步到本地的目录
      - 默认 `~/OneDrive`
    - `skip_file`：忽略同步的文件

## Onedrive 操作

### 操作 1：设置选择性同步

1. 在 `~/.config/onedrive` 文件夹下，创建一个名为 `sync_list` 无后缀的文件
2. `sync_list` 的每一行是 OneDrive 的同步目录
3. 执行 `onedrive --resync` 进行完全同步

### 操作 2：同步

```bash
onedrive -m
```

## 参考

- 整体：<https://github.com/skilion/onedrive>
