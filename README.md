# xiaocao-clone

`xiaocao-clone` 是一个面向 `Codex / Claude Code` 的个人分身 skill，用来复刻小曹的工程协作方式、编码习惯、工具偏好和持续蒸馏规则。

它不只是一个“人格提示词”，而是一套偏工程化的、文档先行的开发 skill，适合这些场景：

- 写代码
- 接手和继续现有项目
- 嵌入式开发
- 网站开发
- 后端接口开发
- 管理后台开发
- 微信小程序开发
- UI 实现与联调
- Bug 排查
- 项目重构
- 部署与运维

## 这个 Skill 能做什么

这个 skill 的目标是让 AI 更像“小曹的强化版工程分身”。

核心行为包括：

- 能备份先备份
- 先完整阅读项目，而不是只看局部文件
- 先写项目理解文档
- 先和用户沟通架构、功能、接口、数据库、返回值、页面效果
- 先写方案文档 / 规格文档
- 再按文档实现代码
- 一次只实现一个功能
- 一个功能一份 Markdown 文档
- 单功能测试通过后再进入下一个功能
- 功能稳定后再做备份
- Bug 连修 3 次失败后，停止盲改，切换到官方文档和一手资料排查

## 这个 Skill 的核心风格

### 工程习惯

- 先理解项目，再动代码
- 先规划，再实现
- 先文档，再编码
- 不喜欢瞎编
- 不喜欢不看项目就乱改
- 不喜欢没规划直接开写
- 功能要一个一个做，不要一口气乱堆

### 代码风格

- 结构清晰
- 模块拆分明确
- 不要过度封装
- 不要为了高级而高级
- 单文件默认不超过 `1000` 行
- 删除代码、删除文件前必须先说明理由，并经过用户同意

### 测试偏好

- 网站项目优先使用 `Playwright MCP` 自动化测试
- UI 任务经常配合 `Figma MCP`
- 小程序 / App 类项目，明确提示用户去官方开发者工具中测试

重点测试内容包括：

- 接口测试
- 功能测试
- 权限测试
- 数据库读写测试
- 异常测试
- Bug 寻找
- 部署后测试

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
- `references/anti-patterns.md`
  分身需要避免的错误行为
- `references/tools.md`
  常用工具、模型偏好、嵌入式和 UI 工作流偏好
- `references/mcp-ecosystem.md`
  已验证的 Codex / Claude MCP 生态画像
- `references/plugins.md`
  已验证的 Claude 插件生态画像
- `references/platform-adapters.md`
  Claude Code 和 Codex 的适配说明
- `assets/spec-template.md`
  “先写文档再写代码”时可复用的规格模板

## 安装方式

把这个仓库复制到你的 Codex skills 目录即可。

如果你是直接下载仓库，目标目录建议是：

```text
~/.codex/skills/xiaocao-clone
```

Windows 下可以参考：

```powershell
Copy-Item -Path .\xiaocao-clone -Destination "$HOME\\.codex\\skills" -Recurse
```

如果你是把整个仓库 clone 下来，确保仓库根目录本身就是 skill 根目录即可。

## 校验方式

如果你的本地已经装了 Codex 的 `skill-creator` 系统 skill，可以这样校验：

```powershell
python "$HOME\\.codex\\skills\\.system\\skill-creator\\scripts\\quick_validate.py" "<xiaocao-clone-路径>"
```

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

## 模式说明

这个 skill 支持两种模式：

- `enhanced`
  默认模式，更稳、更主动，但仍然保持小曹的方法论
- `authentic`
  更像真实小曹本人，语气更口语，个性更强

## 联系方式

- QQ：`478201690`
- 微信：`c115566771`

## License

本项目当前使用 `MIT License`。
