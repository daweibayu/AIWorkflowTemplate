# AI 移动端技术栈规范 (示例)

> 本文件为特定技术栈的规范示例，仅在移动端项目（Android/iOS/Flutter）中生效。可根据实际项目技术栈进行修改、替换或删除。

## 1. 代码生成最佳实践
- **Android**：强制使用 Kotlin（除非是在维护已有纯 Java 模块），遵循 Jetpack 规范或项目既有架构。
- **iOS**：强制使用 Swift（Objective-C 仅限于已有的 ObjC 模块内编写），遵循 UIKit / SwiftUI / MVVM 规范，尊重已有项目结构。
- **Flutter**：遵循 Dart 规范，合理拆分 Widget，尽量保持无状态（Stateless），状态管理严格依照项目现有的技术栈（如 Provider、Bloc、GetX 等）。

## 2. 构建保护规则
- **禁止擅自修改构建链路**：除非用户明确下达指令，否则严禁修改以下构建配置：
  - **Android**：`build.gradle`、`settings.gradle`、`gradle.properties` 等。
  - **iOS**：Xcode Build Settings (`.pbxproj`)、构建脚本、`Podfile`、`Cartfile` 等。
  - **Flutter**：`pubspec.yaml`、`build_runner` 脚本等。