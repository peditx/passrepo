# PeDitX Repository

Binary distribution of [PeDitX/openwrt-passwall](https://github.com/peditx/openwrt-passwall) built with official OpenWRT SDK.

[![Build and Release](https://github.com/dianlujitao/openwrt-passwall-build/actions/workflows/build-release.yml/badge.svg)](https://github.com/peditx/passrepo/actions/workflows/autocomp.yml)
[![Scan openwrt-passwall Version](https://github.com/dianlujitao/openwrt-passwall-build/actions/workflows/version-scan.yml/badge.svg)](https://github.com/peditx/passrepo/actions/workflows/version-scan.yml)

## Install via OPKG

1. Add new opkg key:

    ```sh
    wget -O passwall.pub https://repo.peditxdl.ir/passwall-packages/passwall.pub
    opkg-key add passwall.pub
    ```

2. Add opkg repository:

    ```sh
    read release arch << EOF
    $(. /etc/openwrt_release ; echo ${DISTRIB_RELEASE%.*} $DISTRIB_ARCH)
    EOF
    for feed in passwall_luci passwall_packages passwall2; do
      echo "src/gz $feed https://repo.peditxdl.ir/passwall-packages/releases/packages-$release/$arch/$feed" >> /etc/opkg/customfeeds.conf
    done
    ```

    OR

    ```sh
    read arch << EOF
    $(. /etc/openwrt_release ; echo $DISTRIB_ARCH)
    EOF
    for feed in passwall_luci passwall_packages passwall2; do
      echo "src/gz $feed https://repo.peditxdl.ir/passwall-packages/snapshots/packages/$arch/$feed" >> /etc/opkg/customfeeds.conf
    done
    ```

    in case you use a snapshot build.

3. Install package:

    ```sh
    opkg update
    opkg install luci-app-passwall
    ```

## Manual Install

- Download prebuilt ipk file from [PeDitX Repo](https://repo.peditxdl.ir/passwall-packages/releases/).

- Upload file to your router, install it with shell command.

  ```sh
  opkg install luci-app-passwall*.ipk
  ```

## Acknowledgement

This project is heavily inspired by [kuoruan/openwrt-v2ray](https://github.com/kuoruan/openwrt-v2ray).


## Special Thanks:

- [PeDitX](https://github.com/peditx)
- [PeDitXRT](https://github.com/peditx/peditxrt)
- [OpenWrt](https://github.com/openwrt)
- [ImmortalWrt](https://github.com/immortalwrt)



© 2018–2024 PeDitX. All rights reserved.  
For support or inquiries, join us on [Telegram](https://t.me/peditx).
