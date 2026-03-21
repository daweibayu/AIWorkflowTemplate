## AI Workflow Template

这是一个 `workspace template` 仓库，不是实际运行中的 workspace instance。

template-managed 的源文件统一位于 `.workflow/`：

- `.workflow/scaffold/workspace/`：workspace 根骨架
- `.workflow/scaffold/repos/sot/`：SoT 初始结构
- `.workflow/bin/workflow`：命令入口

## 初始化

### 开发态

1. `git clone` 当前 template repo
2. 运行：

```bash
.workflow/bin/workflow init ~/aiworkspace/tongpin-workspace --name tongpin-workspace
```

### 发布态目标

后续发布后，初始化体验会收敛成类似：

```bash
uvx workflow-template init ~/aiworkspace/tongpin-workspace --name tongpin-workspace
```

### 添加子仓库

```bash
.workflow/bin/workflow repo add app --workspace ~/aiworkspace/tongpin-workspace \
  --git-url https://github.com/your-org/your-app.git

.workflow/bin/workflow repo sync --all --workspace ~/aiworkspace/tongpin-workspace
```

## 生成结果

初始化后的 workspace instance 将生成：

- 根目录 `.ai/`
- 根目录 `.ep/`
- `workspace.yaml`
- `workspace.lock.yaml`
- `repos/sot/` 初始结构，并初始化为独立 git repo
- 后续通过 `workflow repo add/sync` 管理外部子仓库，并将 repo 声明写回 `workspace.yaml`

## 说明

- template 使用 `.workflow/`
- 生成结果与子仓库使用 `.ai/`
- 开发期的 linked 模式只作为内部兼容，不作为公开初始化文档的一部分
