---
date: 2023-09-29T09:17:53.000Z
updated: 2024-01-27T09:18:15.751Z
title: 在家自建nas,摆脱限速网盘
slug: self-nas
oid: 65b4ca4160dc4a15ba7abf00
categories: 学习
type: post
---

# [写在前面]你为什么需要 nas

首先，你需要明确一点：你是否存在 nas 的需求。

毕竟，就算是捡二手 x86 垃圾组 nas，性能稍好的价格则至少在 100 上下

而全新的 arm 开发板，便宜且体积小的 (如香橙派的 zero3 1g 内存，创客价 109) 也许要 100 左右

更别说硬盘之类的，100 一下的硬盘 (注意是硬盘) 基本上也是定时炸弹

所以说**一定一定**要先确定自己的需求

否则，还不如把钱省着做公益

# 你需要的

一台设备 (本文以 FriendlyElec NanoPi R2S 作为示范)

一台电脑

一张 sd 卡和相应的读卡器

其他必要物品 (尤其是脑子)

# 安装基础系统

## 疑难解答

### 为什么？

因为本文介绍的是 OMV(全称是**O**pen**M**edia**V**ault) 系统的安装，而 OMV 又是基于 Debian 开发的，所以需要先安装 Debian

### 我可以使用 Ubuntu 吗？

这边建议自己动手丰衣足食

----------

## 下载 armbian

armbian 是基于 Debian/Ubuntu 为 arm 开发板量身定制的发行版，包含了原版系统所不包含的功能

在[清华大学镜像站][1]寻找适合你的发行版本，比如 r2s 就是在这里：[看我看我][2]

(小贴士：为了节省空间，我个人建议使用 minimal 版本)

截至 2023/9/29,Debian 的最新发行代号为 Bookworm(书虫)

## 刷写系统

我推荐[rufus][3],因为他操作简单，且含有官方中文

下载完后，打开软件，并且插入插有内存卡的读卡器

如果你只插了读卡器，那软件只会显示你插入的内存卡

**请注意!!!**

**如果您同时插有其他存储设备，请务必确认哪一个是内存卡!!!**

**数据无价!!! 谨慎操作!!!**

**本站不会因您的操作失误而赔偿一分钱!!!**

选择你下载好的镜像后，点击开始，确认是需要刷写的内存卡后，根据提示刷写内存卡

## 连接服务器

通常，你需要在自己的路由器管理界面查找带有设备名的设备 (比如 nanopi-r2s)
记下 ip 地址后，使用常用的 ssh 工具连接至服务器

系统默认账号一般为 root/1234

登录成功后，按照需要进行初始化

接下来，请参照[本页][4],配置服务器本地化

注意：修改镜像源后一般需要使用`apt update`刷新缓存

## 部署 OMV

依次执行命令
---

date: 2023-09-29T07:56:58.000Z
updated: 2023-09-29T07:56:58.000Z
title: 在家自建 nas，摆脱限速网盘
slug: 在家自建 nas，摆脱限速网盘
categories: 学习
type: post
permalink: posts/在家自建nas,摆脱限速网盘

---

# [写在前面]你为什么需要 nas

首先，你需要明确一点：你是否存在 nas 的需求。
毕竟，就算是捡二手 x86 垃圾组 nas，性能稍好的价格则至少在 100 上下
而全新的 arm 开发板，便宜且体积小的 (如香橙派的 zero3 1g 内存，创客价 109) 也许要 100 左右
更别说硬盘之类的，100 一下的硬盘 (注意是硬盘) 基本上也是定时炸弹
所以说**一定一定**要先确定自己的需求
否则，还不如把钱省着做公益

# 你需要的

一台设备 (本文以 FriendlyElec NanoPi R2S 作为示范)
一台电脑
一张 sd 卡和相应的读卡器
其他必要物品 (尤其是脑子)

# 安装基础系统

## 疑难解答

### 为什么？

因为本文介绍的是 OMV(全称是**O**pen**M**edia**V**ault) 系统的安装，而 OMV 又是基于 Debian 开发的，所以需要先安装 Debian

### 我可以使用 Ubuntu 吗？

这边建议自己动手丰衣足食

----------

## 下载 armbian

armbian 是基于 Debian/Ubuntu 为 arm 开发板量身定制的发行版，包含了原版系统所不包含的功能
在[清华大学镜像站][1]寻找适合你的发行版本，比如 r2s 就是在这里：[看我看我][2]
(小贴士：为了节省空间，我个人建议使用 minimal 版本)
截至 2023/9/29,Debian 的最新发行代号为 Bookworm(书虫)

## 刷写系统

我推荐[rufus][3],因为他操作简单，且含有官方中文
下载完后，打开软件，并且插入插有内存卡的读卡器
如果你只插了读卡器，那软件只会显示你插入的内存卡

**请注意!!!**
**如果您同时插有其他存储设备，请务必确认哪一个是内存卡!!!**
**数据无价!!! 谨慎操作!!!**
**本站不会因您的操作失误而赔偿一分钱!!!**

选择你下载好的镜像后，点击开始，确认是需要刷写的内存卡后，根据提示刷写内存卡

## 连接服务器

通常，你需要在自己的路由器管理界面查找带有设备名的设备 (比如 nanopi-r2s)
记下 ip 地址后，使用常用的 ssh 工具连接至服务器
系统默认账号一般为 root/1234
登录成功后，按照需要进行初始化
接下来，请参照[本页][4],配置服务器本地化
注意：修改镜像源后一般需要使用`apt update`刷新缓存

## 部署 OMV

依次执行命令

```bash
    apt-get install --yes gnupg
    wget --quiet --output-document=- https://packages.openmediavault.org/public/archive.key | gpg --dearmor | tee "/etc/apt/trusted.gpg.d/openmediavault-archive-keyring.gpg"
    cat <<EOF > /etc/apt/sources.list.d/openmediavault.list
    deb https://mirrors.tuna.tsinghua.edu.cn/OpenMediaVault/public shaitan main
    deb https://mirrors.tuna.tsinghua.edu.cn/OpenMediaVault/packages shaitan main
    ## Uncomment the following line to add software from the proposed repository.
    # deb https://mirrors.tuna.tsinghua.edu.cn/OpenMediaVault/public shaitan-proposed main
    # deb https://mirrors.tuna.tsinghua.edu.cn/OpenMediaVault/packages shaitan-proposed main
    ## This software is not part of OpenMediaVault, but is offered by third-party
    ## developers as a service to OpenMediaVault users.
    # deb https://mirrors.tuna.tsinghua.edu.cn/OpenMediaVault/public shaitan partner
    # deb https://mirrors.tuna.tsinghua.edu.cn/OpenMediaVault/packages shaitan partner
    EOF
```

然后

```bash
    export LANG=C.UTF-8
    export DEBIAN_FRONTEND=noninteractive
    export APT_LISTCHANGES_FRONTEND=none
    apt-get update
    apt-get --yes --auto-remove --show-upgraded \
        --allow-downgrades --allow-change-held-packages \
        --no-install-recommends \
        --option DPkg::Options::="--force-confdef" \
        --option DPkg::Options::="--force-confold" \
        install openmediavault-keyring openmediavault
```

接着，使用`omv-confdbadm populate`以使用本机网络配置覆盖 omv 原配置

# 使用

后台地址：服务器 ip

默认账号密码:admin/openmediavault

  [1]: https://mirrors.tuna.tsinghua.edu.cn/armbian-releases/

  [2]: https://mirrors.tuna.tsinghua.edu.cn/armbian-releases/nanopi-r2s/archive/

  [3]: https://rufus.ie/zh/

  [4]: https://mirrors.tuna.tsinghua.edu.cn/help/debian/
