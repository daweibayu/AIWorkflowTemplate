## 目标

明确多系统场景下的 AI 工作流工程组织方式。


## 共识

1. 使用多 repo
2. 使用 workspace 聚合支撑同一个 EP 下的跨 repo 协同开发
3. 不使用 submodule
4. 各 repo 可以有自己的 `.ai/`，但 `.ai/` 只承载该 repo 的 rules / constraints / workflow
5. 业务需求、UI 规范、领域定义等正式业务内容统一放在 SoT repo 中，并视为 SoT 的版本化资产
6. workspace 采用 `template + personal instance` 模式


## 结论

1. 多 repo 负责发布边界、版本边界、职责边界
2. workspace 负责开发期协同，不改变各 repo 自身独立的 Git 历史与发布方式
3. SoT 是业务真源；repo 内 `.ai/` 是执行约束，不承担 SoT 职责
4. Git 中保留 workspace template；每个人在本地维护自己的 personal workspace instance，默认不直接入库


## Workspace 基础结构

```text
workspace/
  workspace.yaml
  repos/
    sot/
    app/
    web/
    admin/
    server/
  scripts/
```


## workspace.yaml

`workspace.yaml` 记录各 repo 的 `ref`，而不是只记录 branch 或只记录 version。

`ref` 可以是：

1. branch
2. tag / version
3. commit

这样才能同时覆盖开发态与发布态。

建议的最小字段集合：

```yaml
name: project-name
repos:
  sot:
    path: repos/sot
    remote: git@github.com:org/sot.git
    ref: main
  app:
    path: repos/app
    remote: git@github.com:org/app.git
    ref: main
scripts:
  bootstrap: scripts/bootstrap.sh
  check: scripts/check.sh
```


## 建议方向

1. 跨 repo context 采用两层加载：先加载 `SoT repo + 目标 repo .ai/`，再按任务补充相关 repo
2. workspace 先进入跨 repo CI 校验，不进入统一发布
3. EP 采用“一个 EP ID + 多 repo 分支 / PR”的关联方式


## 下一步

1. 定义 workspace template 的最小结构
2. 定义 EP 在多 repo 下的分支与 PR 关联规则
3. 定义 AI 的跨 repo context 加载顺序
4. 定义 workspace 级 CI 校验范围
