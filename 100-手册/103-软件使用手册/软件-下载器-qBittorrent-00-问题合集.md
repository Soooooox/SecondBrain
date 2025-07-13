# 软件-下载器-qBittorrent-00-问题合集

## 问题 1：RSS 订阅无法刷新

**原因**：可能是订阅网站被 ban、RSS 订阅被墙 ban

**解决方法**：qBittorrent 设置代理

<img src="https://raw.githubusercontent.com/Soooooox/Image-Hosting-Service/main/20230810162246.png" alt="20230810162246" width=600>

- 飞机场端口：clash 默认为 7890
- 主机 ip：127.0.0.1
- 类型：一般选择 SOCK5

**注意**：此方法只针对 4.6（不包含 4.6 ）以前的版本，4.6 以后的版本RSS订阅不能使用（**存疑**）

**其他方法**：

- 可以使用没有污染的梯子节点（有概率成功）
- 使用没有被 BAN 的 RSS 网站

## 问题 2：qBittorrent 软件进入有卡顿

**原因**：UI 查询网络时发生堵塞

**解决方法**：提前设置好网络接口，减少 UI 查询网络

<img src="https://raw.githubusercontent.com/Soooooox/Image-Hosting-Service/main/20230810163023.png" alt="20230810163023" width=600>

1. 网络接口设置

    <img src="https://raw.githubusercontent.com/Soooooox/Image-Hosting-Service/main/20230810163244.png" alt="20230810163244" width=400>

   - 网线连接：以太网
   - 无线连接：本地连接

2. IP 地址设置

    <img src="https://raw.githubusercontent.com/Soooooox/Image-Hosting-Service/main/20230810163235.png" alt="20230810163235" width=400>

   - 电脑使用 IPV4 就用 IPV4
   - 电脑使用 IPV6 就用IPV6
   - 一般选用 IPV4

## 问题 3：tracker 一直在更新中或未工作，并且种子加载不出做种数和用户

**原因**：网络接口可能不是以太网或者本地连接

**解决办法**：

1. 进入选项
2. 进入高级
3. 将网络接口更改为当前网络连接方式：以太网（有线）、WLAN（无线）

## 问题 4：用户数多，但做种数少，没有速度

**原因**：做种人有意切断传输，说明此种子里的文件可能有错误，可能做种人有发布新的种子文件，常发生在最新种子里

**解决办法**：找到做种人发布的新的修改种子（含有此文件）

## 参考

- `问题 1：RSS 订阅无法刷新`：
  - [rss订阅下载失败](https://tiebac.baidu.com/p/9016817501?lp=5028&mo_device=1&is_jingpost=0)
  - [更新v4.6.0.10版本后，RSS订阅无法正确获取](https://github.com/c0re100/qBittorrent-Enhanced-Edition/issues/506)
  - [rss订阅下载出错什么情况](https://tiebac.baidu.com/p/8764480462?lp=home_main_thread_pb&mo_device=1)
- `问题 2：qBittorrent 软件进入有卡顿`：[关于qBittorrent UI界面卡死的解决方法](https://zhuanlan.zhihu.com/p/546219568)
