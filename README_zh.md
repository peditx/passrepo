# PeDitX 仓库

[**English**](README.md) | [**فارسی**](README_fa.md) | [**中文**](README_zh.md) | [**Русский**](README_ru.md)

使用官方 OpenWRT SDK 构建的 [PeDitX/openwrt-passwall](https://github.com/peditx/openwrt-passwall) 的二进制分发版本。

[![Build and Release](https://github.com/dianlujitao/openwrt-passwall-build/actions/workflows/build-release.yml/badge.svg)](https://github.com/peditx/passrepo/actions/workflows/autocomp.yml)  
[![Scan openwrt-passwall Version](https://github.com/dianlujitao/openwrt-passwall-build/actions/workflows/version-scan.yml/badge.svg)](https://github.com/peditx/passrepo/actions/workflows/version-scan.yml)

## 通过 OPKG 安装

1. 添加新的 opkg 密钥：

    ```sh
    wget -O passwall.pub https://repo.peditxdl.ir/passwall-packages/passwall.pub
    opkg-key add passwall.pub
    ```

2. 添加 opkg 仓库：

    ```sh
    read release arch << EOF
    $(. /etc/openwrt_release ; echo ${DISTRIB_RELEASE%.*} $DISTRIB_ARCH)
    EOF
    for feed in passwall_luci passwall_packages passwall2; do
      echo "src/gz $feed https://repo.peditxdl.ir/passwall-packages/releases/packages-$release/$arch/$feed" >> /etc/opkg/customfeeds.conf
    done
    ```

    或者如果您使用的是 snapshot 版本：

    ```sh
    read arch << EOF
    $(. /etc/openwrt_release ; echo $DISTRIB_ARCH)
    EOF
    for feed in passwall_luci passwall_packages passwall2; do
      echo "src/gz $feed https://repo.peditxdl.ir/passwall-packages/snapshots/packages/$arch/$feed" >> /etc/opkg/customfeeds.conf
    done
    ```

3. 安装软件包：

    ```sh
    opkg update
    opkg install luci-app-passwall
    ```

或者

```sh
    opkg update
    opkg install luci-app-passwall2
```

## 手动安装

- 从 [PeDitX 仓库](https://repo.peditxdl.ir/passwall-packages/releases/) 下载预构建的 ipk 文件。

- 将文件上传到您的路由器，并通过以下命令安装：

    ```sh
    opkg install luci-app-passwall*.ipk
    ```

## 致谢

本项目深受 [kuoruan/openwrt-v2ray](https://github.com/kuoruan/openwrt-v2ray) 的启发。

## 特别感谢：

- [PeDitX](https://github.com/peditx)  
- [PeDitXRT](https://github.com/peditx/peditxrt)  
- [OpenWrt](https://github.com/openwrt)  
- [ImmortalWrt](https://github.com/immortalwrt)  

© 2018–2024 PeDitX. 保留所有权利。  
如需支持或有任何问题，请加入我们的 [Telegram](https://t.me/peditx)。
