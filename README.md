# Smthdagg Repo feeds — private project distribution

## 中文说明

这是多个私有项目的分发索引。只有 Wi-Fi Calling + WLOC 整合项目当前发布
OpenWrt 软件包；独立 Wi-Fi Calling 项目仍是预留目录，其他项目都是源码项目。
源码项目应从各自私有 GitHub 仓库安装，不能使用 `opkg`。

下面是 English documentation and the complete distribution status.

## English

This repository contains separate distribution areas for several private
projects. The WLOC integrated project currently publishes OpenWrt packages.
The standalone Wi-Fi Calling directory is reserved for a future package
release; the other directories are source-project placeholders and must not be
installed with `opkg` or treated as OpenWrt feeds.

The directory name matches the corresponding project repository name. An
OpenWrt package directory has its own `Packages` index and signature; a
source-only directory contains documentation only.

## Layout

| Directory | Project | Status |
|---|---|---|
| `wificalling-location-gateway/` | smthdagg/wificalling-location-gateway | publishing (Standard + Lite, aarch64 + x86_64) |
| `luci-app-wificalling-gateway/` | smthdagg/luci-app-wificalling-gateway | reserved; no package published yet |
| `wificalling-location-gateway-beta/` | *private repository* | withheld — will be published when the project goes public again |
| `ALL-VideoDownload-Plus/` | smthdagg/ALL-VideoDownload-Plus | source-only; install from the repository README |
| `SalesCRM/` | smthdagg/SalesCRM | source-only; install from the repository README |
| `Investment-Ann-List/` | smthdagg/Investment-Ann-List | source-only; install from the repository README |
| `rsstt-app/` | smthdagg/rsstt-app | source-only; install from the repository README |
| `XShield/` | smthdagg/XShield | source-only; install from the repository README |
| `RSSTT-360News/` | smthdagg/RSSTT-360News | source-only; install from the repository README |

`wloc.pub` at the root is the signing public key (key ID
`f7050198aa77cf15`, long-lived, does not change between releases).

## OpenWrt package update procedure

This procedure applies only to a directory with published OpenWrt packages,
currently `wificalling-location-gateway/`. Do not copy source code or
non-OpenWrt projects into this feed.

Work in a checkout of this repository's `gh-pages` branch. The index generator
is `scripts/gen-feed-index.sh` on this repository's `main` branch.

1. Copy the project's new `.ipk` files into `<project>/` (and remove
   superseded versions of the same package).
2. Regenerate **only that project's** index:
   `/tmp/wloc-feed-main/scripts/gen-feed-index.sh <project-dir>`
3. Sign it (macOS has no usign; the pinned OpenWrt rootfs runs it):
   `<product-repo>/scripts/openwrt/sign-feed.sh <project-dir>`
   **Never sign without regenerating the index first.**
4. Append a row to `UPDATES.md` (date, project, version, action).
5. Run `scripts/feed-verify.sh <project-parent-dir>` — it must pass before
   pushing. It verifies: `Packages.gz` matches `Packages`, both signatures
   are valid for the long-lived key, every indexed package exists with a
   matching SHA256, and `UPDATES.md` covers every project whose index changed
   after the log was last updated.
6. Commit and push `gh-pages`.

## Router configuration

Use an `opkg` source line only for a project that publishes OpenWrt packages.
Currently that is the integrated WLOC project:

```sh
src/gz wloc https://smthdagg.github.io/Smthdagg-Repo-feeds/wificalling-location-gateway
```

Import the signing key once (never changes):

```sh
wget -O /etc/opkg/keys/f7050198aa77cf15 \
  https://raw.githubusercontent.com/smthdagg/Smthdagg-Repo-feeds/main/wloc.pub
```

OpenWrt 25.x uses the APK format: download the `.apk` asset from the
project’s GitHub Release and `apk add --allow-untrusted` (the apk channel is
not separately signed).

Do not add source-only projects such as `ALL-VideoDownload-Plus`, `SalesCRM`,
`Investment-Ann-List`, `rsstt-app`, `XShield`, or `RSSTT-360News` to
`customfeeds.conf`. Install those projects from their private GitHub
repository using the installation instructions in that project's README.

## Repository rename note

This repository was renamed from `wificalling-location-gateway-feed` to
`Smthdagg-Repo-feeds` on 2026-08-30. The Pages URL changed accordingly; the
signing key and index format did not.
