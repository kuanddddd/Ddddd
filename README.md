# Ddddd

**Ddddd 1.0.0 Beta** —— Android 应用项目。

## 项目简介

本仓库用于保存 Ddddd Android 应用的完整源码，并通过 GitHub Actions 自动编译 Debug APK、发布 GitHub Release。

## 仓库目录

- `Ddddd/`：已解压的 Android 项目源码，包含 Gradle 配置、应用代码、资源文件及相关模块。
- `Ddddd-1.0.0-Beta-source.zip`：项目原始源码压缩包。
- `.github/workflows/build-apk.yml`：自动编译 APK 并发布到 GitHub Releases 的工作流配置。

以后修改项目时，可以直接使用仓库中的 `Ddddd/` 源码目录，不需要重新上传 ZIP 压缩包。

## 编译环境

- JDK 21
- Gradle（项目使用 Gradle 构建）

## 本地编译

在仓库根目录执行：

```bash
cd Ddddd
gradle --no-daemon :app:assembleDebug
```

编译成功后，APK 位于：

```
Ddddd/app/build/outputs/apk/debug/app-debug.apk
```

## 下载 APK

前往 [GitHub Releases 下载页面](https://github.com/kuanddddd/Ddddd/releases)，选择最新发布版本下载 APK。

## 自动构建说明

推送符合工作流触发条件的代码后，GitHub Actions 会自动执行编译，并在构建成功后发布 APK。

当前发布工作流会移除应用内的更新检测功能后再进行编译。

## SukiSU Ultra 管理器（独立构建）

仓库已添加官方 SukiSU Ultra 源码仓库作为 Git 子模块（固定到一个明确的上游提交），位于 `vendor/SukiSU-Ultra/`；管理器完整工程位于 `vendor/SukiSU-Ultra/manager/`。Ddddd 原有 `Ddddd/` 核心源码没有改动。

独立 GitHub Actions 工作流会初始化该子模块并构建管理器 APK：

- 官方源码： https://github.com/SukiSU-Ultra/SukiSU-Ultra
- 上游固定提交：`645ef9860b9b7f900bb5d1b27e224f2c311d39c0`
- 管理器版本名：`9.9.9 beta`
- 工作流：`.github/workflows/build-sukisu-manager.yml`
- 构建方式：GitHub Actions 中手动运行 **Build SukiSU Ultra Manager**
- 构建产物：Actions 运行页面中的 `sukisu-ultra-manager-debug` Artifact

该流程不会修改或替换 `Ddddd/` 原有应用源码，也不会把 SukiSU 内核代码混入 Ddddd APK。SukiSU 管理器以独立应用构建，使用独立的应用 ID。首次构建需在 Actions 中检查构建日志；官方项目更新或 Android SDK/Gradle 版本变化时，可能需要同步调整构建环境。

源码版权及许可证以 SukiSU Ultra 官方仓库中的文件为准。
