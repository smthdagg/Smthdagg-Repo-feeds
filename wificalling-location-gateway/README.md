# wificalling-location-gateway

## 中文

这是当前私有源中已发布的 Wi-Fi Calling + WLOC 整合包。它是 OpenWrt /
ImmortalWrt / iStoreOS 路由器软件包，不是普通 Linux 或 Docker 服务。

导入签名公钥并添加私有源：

```sh
wget -O /etc/opkg/keys/f7050198aa77cf15 \
  https://raw.githubusercontent.com/smthdagg/Smthdagg-Repo-feeds/main/wloc.pub
echo "src/gz wloc https://smthdagg.github.io/Smthdagg-Repo-feeds/wificalling-location-gateway" \
  >> /etc/opkg/customfeeds.conf
opkg update
opkg install wificalling-location-gateway
```

Standard 包依赖系统中的 `sing-box`；内存或存储受限时可安装
`wificalling-location-gateway-lite`。必须选择与路由器 CPU 架构匹配的包。
当前私有源发布的是 OpenWrt 24.10 / iStoreOS 24.10 的 IPK；OpenWrt 25.x
使用项目 Release 中对应的原生 APK，不要把 IPK 改名成 APK。

详细配置、证书、设备策略和回滚步骤请查看项目主仓库 README。

## English

This is the published Wi-Fi Calling + WLOC integrated package in the private
feed. It is an OpenWrt / ImmortalWrt / iStoreOS router package, not a regular
Linux or Docker service.

Import the signing key and add the private feed:

```sh
wget -O /etc/opkg/keys/f7050198aa77cf15 \
  https://raw.githubusercontent.com/smthdagg/Smthdagg-Repo-feeds/main/wloc.pub
echo "src/gz wloc https://smthdagg.github.io/Smthdagg-Repo-feeds/wificalling-location-gateway" \
  >> /etc/opkg/customfeeds.conf
opkg update
opkg install wificalling-location-gateway
```

The Standard package uses the system `sing-box`; use
`wificalling-location-gateway-lite` on constrained devices. Select the package
matching the router CPU architecture. The current private feed publishes IPK
packages for OpenWrt 24.10 / iStoreOS 24.10; OpenWrt 25.x uses the native APK
from the project Release. Never rename an IPK to APK.

See the main project repository README for configuration, certificate, device
policy, and rollback instructions.
