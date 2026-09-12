# luci-app-wificalling-gateway

## 中文

这是独立 Wi-Fi Calling LuCI 项目的私有源预留目录。目前这里尚未发布
`.ipk` 或 `.apk` 包，因此不能从本目录执行 `opkg install` 或 `apk add`。

当前安装方式：请从项目 GitHub Releases 下载对应版本，按照项目仓库中的
安装说明安装。该插件也已包含在已发布的
`wificalling-location-gateway` 整合包中。

私有源目录只有在实际发布包、生成 `Packages` 索引并完成签名后，才会增加
可执行的私有源安装命令。

## English

This is the reserved private-feed directory for the standalone Wi-Fi Calling
LuCI project. No `.ipk` or `.apk` package is published here yet, so do not run
`opkg install` or `apk add` against this directory.

For now, download the matching release asset from the project's GitHub Releases
page and follow the installation guide in that repository. The plugin is also
included in the published `wificalling-location-gateway` integrated package.

This directory will receive usable private-feed commands only after packages
are published, indexed in `Packages`, and signed.
