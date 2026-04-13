# User Memory System

## 目标

让 `xiaocao-clone` 具备真正可落地的“用户记忆”能力，而不是只会口头总结。

这个系统的目标是：

- 从长期协作中提取稳定偏好
- 通过候选记忆机制避免误记
- 只把确认后的内容写入长期画像
- 把真实个人记忆保留在本地，不推送到公开仓库

## 设计原则

### 1. 本地优先

真实用户记忆应保存在本地 `memory/` 目录，不应默认进入 GitHub 仓库历史。

### 2. 候选先行

任何新记忆先进入候选区，再经用户确认后进入长期画像。

### 3. 稳定优先

只记录长期稳定的偏好、流程、表达方式、决策规则。

### 4. 隐私最小化

不要记录：

- 密钥
- 密码
- Token
- 联系方式
- 精确住址
- 其他明显敏感信息

## 文件结构建议

```text
memory/
|- .gitkeep
|- confirmed-profile.template.md
`- candidate-memory.template.md
```

真实使用时，建议本地额外创建：

```text
memory/
|- confirmed-profile.private.md
`- memory-log.private.jsonl
```

其中：

- `confirmed-profile.private.md`
  存已经确认的长期画像
- `memory-log.private.jsonl`
  存每轮候选更新记录，方便回溯

## 标准流程

### 第一步：提取候选记忆

在一次有价值的对话结束后，提取：

- workflow
- tools
- likes
- dislikes
- language_style
- decision_rules

### 第二步：生成候选总结

使用 `memory/candidate-memory.template.md` 的结构输出候选更新。

### 第三步：等待确认

必须问用户：

- 是否写入长期画像
- 是否只保留本轮候选，不写入

### 第四步：合并到长期画像

只有确认通过，才写入 `confirmed-profile.private.md`。

## 与 Skill 的关系

这个记忆系统不应该替代 `persona.md`。

职责划分：

- `persona.md`
  写公开、稳定、默认的人设与风格
- `user-memory-system.md`
  写“如何记忆用户”的机制
- `confirmed-profile.private.md`
  写真实用户自己的长期画像

## 适合记什么

适合长期记忆的内容：

- 工程流程偏好
- 测试偏好
- 工具偏好
- GitHub 选型口味
- 文档结构偏好
- 语气偏好

## 不适合记什么

- 一次性情绪
- 单次口误
- 临时任务参数
- 不稳定偏好

## 推荐触发语

当用户说这些话时，应该考虑启用记忆流程：

- “蒸馏我一下”
- “把这个记住”
- “更新我的偏好”
- “写入长期画像”
- “这以后按这个来”
