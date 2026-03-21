# AI Context Index 发现规则

## 1. 固定文件名

每个作用域的 AI 上下文索引文件名固定为：

`AI_CONTEXT_INDEX.yaml`


## 2. 固定位置

每个作用域根目录的 AI 上下文索引文件位置固定为：

`<scope-root>/.ai/AI_CONTEXT_INDEX.yaml`

这条规则适用于：

1. workspace repo
2. SoT repo
3. sub repo
4. repo 内部需要继续分层的 module / 子域 / 子树


## 3. 发现机制

workspace 或更高层作用域在需要组合上下文时，应优先通过固定路径递归发现子作用域的 index 文件，而不是依赖人工配置临时路径。

默认发现方式：

1. 确定候选作用域根目录
2. 查找 `<scope-root>/.ai/AI_CONTEXT_INDEX.yaml`
3. 读取该文件的 `scope / id / compatibility / context / external_context`
4. 将其加入候选作用域集合
5. 按递归顺序组合上下文


## 4. 加载原则

1. 当前任务默认加载当前作用域自己的 index
2. 默认按祖先链 `outer_to_inner` 递归补充上层作用域
3. SoT 与相关 repo 作为外部作用域按声明补充
4. 没有 `AI_CONTEXT_INDEX.yaml` 的目录，不应被视为可自动组合的 AI 作用域
