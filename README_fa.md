# PeDitX Repository

[**English**](README.md) | [**فارسی**](README_fa.md) | [**中文**](README_zh.md) | [**Русский**](README_ru.md)

توزیع باینری از [PeDitX/openwrt-passwall](https://github.com/peditx/openwrt-passwall) که با استفاده از SDK رسمی OpenWRT ساخته شده است.

[![Build and Release](https://github.com/dianlujitao/openwrt-passwall-build/actions/workflows/build-release.yml/badge.svg)](https://github.com/peditx/passrepo/actions/workflows/autocomp.yml)  
[![Scan openwrt-passwall Version](https://github.com/dianlujitao/openwrt-passwall-build/actions/workflows/version-scan.yml/badge.svg)](https://github.com/peditx/passrepo/actions/workflows/version-scan.yml)

## نصب از طریق OPKG

1. کلید جدید opkg را اضافه کنید:

    ```sh
    wget -O passwall.pub https://repo.peditxdl.ir/passwall-packages/passwall.pub
    opkg-key add passwall.pub
    ```

2. مخزن opkg را اضافه کنید:

    ```sh
    read release arch << EOF
    $(. /etc/openwrt_release ; echo ${DISTRIB_RELEASE%.*} $DISTRIB_ARCH)
    EOF
    for feed in passwall_luci passwall_packages passwall2; do
      echo "src/gz $feed https://repo.peditxdl.ir/passwall-packages/releases/packages-$release/$arch/$feed" >> /etc/opkg/customfeeds.conf
    done
    ```

    یا در صورت استفاده از نسخه snapshot:

    ```sh
    read arch << EOF
    $(. /etc/openwrt_release ; echo $DISTRIB_ARCH)
    EOF
    for feed in passwall_luci passwall_packages passwall2; do
      echo "src/gz $feed https://repo.peditxdl.ir/passwall-packages/snapshots/packages/$arch/$feed" >> /etc/opkg/customfeeds.conf
    done
    ```

3. بسته را نصب کنید:

    ```sh
    opkg update
    opkg install luci-app-passwall
    ```

یا

    ```sh
    opkg update
    opkg install luci-app-passwall2
    ```

## نصب دستی

- فایل ipk پیش‌ساخته را از [مخزن PeDitX](https://repo.peditxdl.ir/passwall-packages/releases/) دانلود کنید.

- فایل را به روتر خود آپلود کرده و با دستور زیر نصب کنید:

    ```sh
    opkg install luci-app-passwall*.ipk
    ```

## تقدیر

این پروژه به شدت از [kuoruan/openwrt-v2ray](https://github.com/kuoruan/openwrt-v2ray) الهام گرفته شده است.

## تشکر ویژه:

- [PeDitX](https://github.com/peditx)  
- [PeDitXRT](https://github.com/peditx/peditxrt)  
- [OpenWrt](https://github.com/openwrt)  
- [ImmortalWrt](https://github.com/immortalwrt)  

© ۲۰۱۸–۲۰۲۴ PeDitX. تمامی حقوق محفوظ است.  
برای پشتیبانی یا پرسش‌ها، به [تلگرام](https://t.me/peditx) ما بپیوندید.
