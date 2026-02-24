# Commit 规范

遵循 [Conventional Commits](https://www.conventionalcommits.org/) 规范。

## 1. 格式
`<type>(<scope>): <subject>`

## 2. 常用 Type
- `feat`: 新功能
- `fix`: 缺陷修复
- `docs`: 文档/规范/架构更新
- `refactor`: 代码重构
- `test`: 测试用例
- `chore`: 构建/配置/依赖变动

## 3. 规范要求
- **Subject**: 简明扼要，使用祈使句（如 "add" 而非 "added"）。
- **Body & Footer**: 如变更复杂，需在 Body 说明“为什么”。如关联 Issue 或对源文档（SoT）有反馈修正，必须在 Footer 备注（如 `Fixes #123`, `Relates to #456`）。