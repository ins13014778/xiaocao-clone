# xiaocao-clone

`xiaocao-clone` 是一个面向 `Codex / Claude Code / Trae` 的中文个人分身工程 skill，用来复刻小曹的工程协作方式、编码习惯、工具偏好、持续蒸馏规则，以及新增的用户记忆能力。

它不只是一个“人格提示词”，而是一套偏工程化、文档先行、功能逐步交付的开发 skill。

## 适用场景

这个 skill 适合这些场景：

- 写代码
- 接手和继续现有项目
- 嵌入式开发
- 网站开发
- 后端接口开发
- 管理后台开发
- 微信小程序开发
- UI 设计与实现
- Bug 排查
- 项目重构
- 部署与运维

## 核心能力

### 1. 中文小曹分身

默认使用中文协作，按“小曹分身”的方式推进工程任务：

- 能备份先备份
- 先看懂项目再改代码
- 先写项目理解文档
- 先沟通方案、接口、数据库、返回值、页面效果
- 先写文档，再实现代码
- 一次只做一个功能
- 一个功能一份 Markdown 交付文档

### 2. 更强的工程能力

已经内置的工程增强包括：

- 工程任务分流
- 编码规范
- 测试协议
- GitHub 参考项目筛选规则
- 数据库改动协议
- 嵌入式专项流程
- 项目理解模板
- 单功能交付模板

### 3. 用户记忆功能

这次新增的重点能力是“用户记忆”。

目标：

- 从长期协作中提取稳定偏好
- 先生成候选记忆
- 用户确认后再写入长期画像
- 真实用户记忆保存在本地，不直接提交到公开仓库

## 用户记忆方案

### 设计原则

- 本地优先
- 候选先行
- 确认后写入
- 隐私最小化

### 文件结构

仓库中新增了：

```text
memory/
|- .gitkeep
|- confirmed-profile.template.md
`- candidate-memory.template.md
```

说明：

- `confirmed-profile.template.md`
  长期画像模板
- `candidate-memory.template.md`
  候选记忆模板

真实使用时，建议你在本地自行创建私有文件，例如：

```text
memory/
|- confirmed-profile.private.md
`- memory-log.private.jsonl
```

这些私有文件不应推送到 GitHub。

### 记忆流程

建议流程：

1. 对话结束后提取候选记忆
2. 用候选模板输出结构化总结
3. 询问用户是否写入长期画像
4. 用户确认后再合并到本地长期画像

### 适合记的内容

- 工程流程偏好
- 测试偏好
- 工具偏好
- 文档结构偏好
- GitHub 选型偏好
- 表达风格偏好

### 不适合记的内容

- 密钥
- 密码
- Token
- 联系方式
- 明显敏感信息
- 一次性情绪
- 临时任务参数

## 仓库内容说明

- `SKILL.md`
  Skill 主入口，定义触发条件、硬规则、核心模式和引用说明
- `agents/openai.yaml`
  UI 元数据配置
- `references/persona.md`
  小曹的人设、语气、口头禅和模式差异
- `references/workflow.md`
  小曹的核心工程流程和交付规则
- `references/distillation.md`
  持续蒸馏和长期确认机制
- `references/user-memory-system.md`
  用户记忆系统设计
- `references/anti-patterns.md`
  分身需要避免的错误行为
- `references/tools.md`
  常用工具、模型偏好、嵌入式和 UI 工作流偏好
- `references/mcp-ecosystem.md`
  已验证的 Codex / Claude MCP 生态画像
- `references/plugins.md`
  已验证的 Claude 插件生态画像
- `references/platform-adapters.md`
  Claude Code、Codex、Trae 的适配说明
- `references/engineering-routing.md`
  不同工程任务的分流规则
- `references/coding-standards.md`
  编码规范
- `references/testing-protocol.md`
  测试协议
- `references/github-selection.md`
  GitHub 项目筛选口味
- `references/database-change-protocol.md`
  数据库改动协议
- `references/embedded-workflow.md`
  嵌入式专项流程
- `assets/project-understanding-template.md`
  项目理解文档模板
- `assets/feature-delivery-template.md`
  单功能交付模板
- `assets/spec-template.md`
  规格文档模板

## 安装方式

目标目录建议：

```text
~/.codex/skills/xiaocao-clone
```

Windows 下可参考：

```powershell
Copy-Item -Path .\xiaocao-clone -Destination "$HOME\\.codex\\skills" -Recurse
```

如果你想放到 `Trae` 里使用，建议把它作为显式调用 skill / prompt 包来用，不要完全依赖自动触发。

## 校验方式

如果本地已经装了 Codex 的 `skill-creator` 系统 skill，可以这样校验：

```powershell
$env:PYTHONUTF8='1'
python "$HOME\\.codex\\skills\\.system\\skill-creator\\scripts\\quick_validate.py" "<xiaocao-clone-路径>"
```

说明：

- Windows 下中文 skill 容易遇到默认编码问题
- 建议先设置 `PYTHONUTF8=1`

## 触发示例

下面这些请求都应该比较容易命中这个 skill：

- “按我的风格写这个功能”
- “先看懂项目再改”
- “先给我出方案文档，再写代码”
- “帮我修这个 bug，先看日志和配置”
- “写个后台接口，把数据库和返回值设计清楚”
- “做个网站功能，一次做一个模块”
- “写嵌入式代码，先把方案和接口写清楚”
- “先用 Figma MCP 看下 UI，再实现页面”
- “把这个偏好记住”
- “蒸馏我一下，更新长期画像”

## GitHub 仓库介绍建议

推荐 About 描述：

> 中文小曹分身工程 skill，支持写代码、做项目、嵌入式、UI、Bug 排查、持续蒸馏和本地用户记忆。

## 联系方式

- QQ：`478201690`
- 微信：`c115566771`

## License

本项目当前使用 `MIT License`。
