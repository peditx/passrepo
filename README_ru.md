# Репозиторий PeDitX

[**English**](README.md) | [**فارسی**](README_fa.md) | [**中文**](README_zh.md) | [**Русский**](README_ru.md)

Бинарное распределение [PeDitX/openwrt-passwall](https://github.com/peditx/openwrt-passwall), созданное с использованием официального SDK OpenWRT.

[![Build and Release](https://github.com/dianlujitao/openwrt-passwall-build/actions/workflows/build-release.yml/badge.svg)](https://github.com/peditx/passrepo/actions/workflows/autocomp.yml)  
[![Scan openwrt-passwall Version](https://github.com/dianlujitao/openwrt-passwall-build/actions/workflows/version-scan.yml/badge.svg)](https://github.com/peditx/passrepo/actions/workflows/version-scan.yml)

## Установка через OPKG

1. Добавьте новый ключ opkg:

    ```sh
    wget -O passwall.pub https://repo.peditxdl.ir/passwall-packages/passwall.pub
    opkg-key add passwall.pub
    ```

2. Добавьте репозиторий opkg:

    ```sh
    read release arch << EOF
    $(. /etc/openwrt_release ; echo ${DISTRIB_RELEASE%.*} $DISTRIB_ARCH)
    EOF
    for feed in passwall_luci passwall_packages passwall2; do
      echo "src/gz $feed https://repo.peditxdl.ir/passwall-packages/releases/packages-$release/$arch/$feed" >> /etc/opkg/customfeeds.conf
    done
    ```

    Или, если вы используете версию snapshot:

    ```sh
    read arch << EOF
    $(. /etc/openwrt_release ; echo $DISTRIB_ARCH)
    EOF
    for feed in passwall_luci passwall_packages passwall2; do
      echo "src/gz $feed https://repo.peditxdl.ir/passwall-packages/snapshots/packages/$arch/$feed" >> /etc/opkg/customfeeds.conf
    done
    ```

3. Установите пакет:

    ```sh
    opkg update
    opkg install luci-app-passwall
    ```

или

```sh
    opkg update
    opkg install luci-app-passwall2
```

## Ручная установка

- Скачайте предварительно собранный файл ipk из [репозитория PeDitX](https://repo.peditxdl.ir/passwall-packages/releases/).

- Загрузите файл на ваш роутер и установите его с помощью команды:

    ```sh
    opkg install luci-app-passwall*.ipk
    ```

## Благодарности

Этот проект был вдохновлен [kuoruan/openwrt-v2ray](https://github.com/kuoruan/openwrt-v2ray).

## Особая благодарность:

- [PeDitX](https://github.com/peditx)  
- [PeDitXRT](https://github.com/peditx/peditxrt)  
- [OpenWrt](https://github.com/openwrt)  
- [ImmortalWrt](https://github.com/immortalwrt)  

© 2018–2024 PeDitX. Все права защищены.  
Для поддержки или вопросов присоединяйтесь к нашему [Telegram](https://t.me/peditx).
