# luci-app-wificalling-gateway

Standalone Wi-Fi Calling Gateway 1.10.0 private feed (architecture-independent
packages).  With 1.10.0 this feed is live: packages, opkg index and usign
signatures are published here.

## 中文

导入签名公钥（长生命周期，各版本通用），添加源并安装：

```sh
wget -O /etc/opkg/keys/f7050198aa77cf15 \
  https://raw.githubusercontent.com/smthdagg/Smthdagg-Repo-feeds/gh-pages/wloc.pub
echo "src/gz luci-app-wificalling-gateway https://smthdagg.github.io/Smthdagg-Repo-feeds/luci-app-wificalling-gateway" \
  >> /etc/opkg/customfeeds.conf
opkg update
opkg install luci-app-wificalling-gateway
```

本目录包含：

- `luci-app-wificalling-gateway_1.10.0-1_all.ipk`（24.10 / iStoreOS 等 opkg 平台）；
- `18.06/luci-app-wificalling-gateway_1.10.0-1_18.06_all.ipk`（18.06/Lede，无 LuCI 菜单注册，用 UCI 配置）；
- `luci-app-wificalling-gateway_1.10.0-r1_noarch.apk`（25.x，`apk add --allow-untrusted` 直接安装）；
- `Packages` / `Packages.gz` 及其 `Packages.sig` 签名，`SHA256SUMS` 供校验。

## English

Import the signing key once, add the source, and install:

```sh
wget -O /etc/opkg/keys/f7050198aa77cf15 \
  https://raw.githubusercontent.com/smthdagg/Smthdagg-Repo-feeds/gh-pages/wloc.pub
echo "src/gz luci-app-wificalling-gateway https://smthdagg.github.io/Smthdagg-Repo-feeds/luci-app-wificalling-gateway" \
  >> /etc/opkg/customfeeds.conf
opkg update
opkg install luci-app-wificalling-gateway
```

Contents: the 1.10.0 architecture-independent packages (24.10 ipk, 18.06 ipk
without the LuCI menu registration, 25.x noarch apk), the signed
`Packages`/`Packages.gz` opkg index, and `SHA256SUMS` for verification.
