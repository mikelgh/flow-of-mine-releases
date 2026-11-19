# 心流手记 (flow-of-mine) 发行产物仓

本仓仅存放由 GitHub Actions 自动构建的**已签名发行包**与**应用内更新清单**，不含源码，也不含任何用户数据。源码位于私有仓 `mikelgh/flow-of-mine`。

## 发行包
- Android：`fom-android-arm64-v8a.apk`、`fom-android-armeabi-v7a.apk`、`fom-android-x86_64.apk`
- Windows：`fom-windows-x64.zip`（便携版，解压即用）
- 更新清单：`latest.json`

每个版本对应一个 Release tag（如 `v0.1.1`），请到本仓 **Releases** 页下载。

## 完整性校验
`latest.json` 为每个产物记录了 `sha256` 与 `size`。下载后请核对：

- Linux / macOS / Git Bash：`sha256sum <文件>`
- Windows PowerShell：`Get-FileHash <文件> -Algorithm SHA256`

校验值与 `latest.json` 一致即为官方产物。

## 应用内自动更新
客户端会读取本仓 `latest.json`，比对 sha256 后再安装。**该检查默认关闭，需你在应用「设置 → 关于与更新」中主动开启**；关闭时应用完全不出网。

## 签名
所有 Android 包使用同一长期正式证书签名，以保证覆盖升级不丢数据；构建时若证书不符会直接拦截，绝不回退到调试签名。
