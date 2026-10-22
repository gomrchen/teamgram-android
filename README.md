# Teamgram Android 客户端

基于 [Telegram for Android](https://github.com/DrKLO/Telegram) 的 Teamgram 自建服客户端（Gradle + NDK）。

**文档** → [docs/文档索引.md](docs/文档索引.md) · 改配置打包 [docs/修改配置与打包.md](docs/修改配置与打包.md)

## 快速开始

```bash
cd teamgram-android

# 1. 改服务器 IP
#    TMessagesProj/jni/tgnet/ConnectionsManager.cpp → addAddressAndPort("你的IP", 10443, ...)

# 2. 改 API 凭证
#    TMessagesProj/src/main/java/org/telegram/messenger/BuildVars.java

# 3. 编译调试包
./gradlew :TMessagesProj_App:assembleAfatDebug
# APK: TMessagesProj_App/build/outputs/apk/afat/debug/app.apk
```

## 合规提醒

1. 在 [my.telegram.org](https://my.telegram.org) 申请自己的 `api_id` / `api_hash`
2. **不要**使用官方 Telegram 名称与 logo 作为你的应用品牌
3. 发布前替换占位 `release.keystore`、`google-services.json`
4. 遵守 GPL v2 开源义务

## 上游说明

英文原版编译说明见仓库历史与 [Telegram 官方仓库](https://github.com/DrKLO/Telegram)。Teamgram 网络与打包细节以 `docs/` 中文文档为准。
