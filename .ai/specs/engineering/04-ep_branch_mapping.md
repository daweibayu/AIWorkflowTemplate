# EP 与分支的映射规范

本项目支持人类主导的标准 Git 流与 AI 主导的 **EP (Execution Pack, 执行包)** 工作流。

## 1. 映射原则 (One EP = One Branch = One Folder)
- **人类开发者**：可按需直接使用 `feature/*` 分支，无需强制绑定。
- **AI 助手默认行为**：处理复杂任务时，AI 默认将任务编号、分支和文件夹进行绑定：
  - 分支名：`feature/ep-login`
  - 瞬态工作目录：`.ep/ep-login/`

## 2. EP 目录结构 (`.ep/`)
```text
.ep/ep-login/
  ├── steps.md       # 【核心】任务拆解步骤与清单
  ├── context.md     # 【选填】依赖上下文与冲突记录
  └── evidence.md    # 【选填】测试用例与验证证据
```

## 3. AI 驱动协同流
1. **Plan (计划)**: 检出分支，创建 `.ep/` 对应目录与 `steps.md` 拆解步骤。
2. **Execute (执行)**: 依据 `steps.md` 编码并更新进度。
3. **Verify (验证 & 反哺)**: 收集测试证据。若发现原有设计文档（SoT）不合理，**必须在 PR 前反哺更新源文档**。
4. **Merge (合并 & 清理)**: PR 合并后，清理或归档对应的 `.ep/` 瞬态目录。