# Ddddd · Android 应用

Ddddd 是一款基于 Kotlin、Jetpack Compose 的 Android Root 工具应用，基于原始项目源码进行品牌重命名，当前应用版本为 1.0.0 Beta。

## 版本与平台
- 应用名称：**Ddddd**
- 应用版本：**1.0.0 Beta**
- 平台：Android 8.0（API 26）及以上
- 编译 SDK：35；Java/Kotlin 目标版本：17

## 功能
- Root 权限检测及工作状态切换。
- 通过配套 SukiSU 模块启动和守护 Root 系统窗口。
- 应用白名单管理。
- 点击 Root 窗口、通知操作或快捷设置磁贴触发启动脚本。

## 重要行为说明
触发执行操作时，程序会通过 Root 权限结束**所有未加入白名单的第三方用户应用**，随后运行 `/data/local/tmp/launch_killapp.sh`。这可能导致未保存的数据丢失。请先配置白名单，并确认理解该行为后再启用。不要将系统应用加入批量结束目标；当前实现只枚举第三方应用包。

## 配套模块
模块目录：`module/killsuoji-overlay/`。模块 ID、安装路径、Android applicationId 和内部 action 标识保留原值，以兼容既有安装流程及模块守护脚本；这些是内部兼容标识，不影响桌面显示名称 Ddddd。

模块采用 SukiSU 模块管理器格式。安装模块并在 Root 管理器中授予 Ddddd Root 权限后，才可启用相关 Root 功能。

## 构建
使用 Android Studio 打开本目录，等待 Gradle 同步后选择 `app` 的 debug 构建变体并构建 APK。当前交付为重命名后的源码；构建环境未提供 Android SDK/Gradle Wrapper，因此本次未生成或验证 APK。
