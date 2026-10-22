# Android 客户端技术文档

`teamgram-android` 基于 Telegram for Android（Gradle + NDK），对接自建 **Teamgram** 服务端。

## 工程结构

| 路径 | 说明 |
|------|------|
| `TMessagesProj/` | 核心库：Java/Kotlin UI、JNI、`tgnet` 网络层 |
| `TMessagesProj_App/` | **默认主应用**（`settings.gradle` 已启用） |
| `TMessagesProj_AppHuawei/` | 华为推送变体（默认未 include） |
| `TMessagesProj_AppHockeyApp/` | 内测更新变体 |
| `TMessagesProj_AppStandalone/` | 独立 Web 变体 |
| `gradle.properties` | 包名、版本号、签名密码 |
| `TMessagesProj/config/` | keystore、debug/release Manifest |

## 关键配置

| 用途 | 文件 |
|------|------|
| 服务器 IP / 端口 | `TMessagesProj/jni/tgnet/ConnectionsManager.cpp` |
| API ID / Hash | `TMessagesProj/.../BuildVars.java` |
| 包名与版本 | `gradle.properties` |
| 签名 | `TMessagesProj/config/release.keystore` + `gradle.properties` |
| 推送 | `TMessagesProj/google-services.json` |

## 工具链

| 项 | 版本 |
|----|------|
| Android Gradle Plugin | 8.4.2 |
| compileSdk / targetSdk | 34 |
| NDK | 21.4.7075529 |
| CMake | 3.10.2 |
| minSdk | 19（`afat` flavor 使用 SDK 23 Manifest） |

## 编译场景

| 场景 | 文档 |
|------|------|
| 改配置并打 APK / AAB | [修改配置与打包.md](修改配置与打包.md) |
| 服务端 IP、端口、API | [服务端对接配置.md](服务端对接配置.md) |

## 默认 Build Variant

日常开发使用 **`afatDebug`**（仅 arm64-v8a，包名带 `.beta` 后缀）。

```bash
./gradlew :TMessagesProj_App:assembleAfatDebug
```

## 关联文档

| 路径 | 说明 |
|------|------|
| `../teamgram/docs/文档索引.md` | 后端部署与编译 |
| `../teamgram-ios/docs/文档索引.md` | iOS 客户端 |
| `../teamgram.io/enterprise/docs/企业版技术文档.md` | 企业版架构 §17 客户端对齐 |

---

上游 README（英文编译说明）：`../README.md`。
