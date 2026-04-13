# 用户记忆功能使用说明

## 目标

这份说明用于告诉使用者，怎样在 `Codex`、`Claude Code`、`Trae` 中手动触发 `xiaocao-clone` 的用户记忆功能。

## 记忆写入总原则

不直接让 AI 把任何内容写进长期记忆。

统一流程：

1. 先提取候选记忆
2. 先给用户看候选总结
3. 用户确认后再写入长期画像
4. 真正的长期记忆保存在本地私有文件

## 本地文件说明

本地建议使用这两个文件：

- `memory/confirmed-profile.private.md`
  已确认的长期画像
- `memory/memory-log.private.jsonl`
  每次记忆写入的日志

## 在 Codex 中怎么用

### 场景 1：对话结束后更新偏好

可以直接这样说：

```md
使用 xiaocao-clone 的用户记忆流程，先提取本轮候选记忆，不要直接写入长期画像。
请按候选模板总结 workflow、tools、likes、dislikes、language_style、decision_rules，
然后问我是否写入长期画像。
```

### 场景 2：确认写入长期画像

当你确认后，可以这样说：

```md
我确认这轮候选记忆可以写入长期画像。
请把确认后的内容合并到 memory/confirmed-profile.private.md，
并在 memory/memory-log.private.jsonl 追加一条写入记录。
```

### 场景 3：只记住，不写入

```md
这轮先保留候选记忆，不要写入长期画像。
```

## 在 Claude Code 中怎么用

建议每次显式点名 skill，不要完全依赖自动触发。

### 建议开场白

```md
先使用 xiaocao-clone skill。
如果这轮对话里出现新的稳定偏好，请走用户记忆流程：
先输出候选记忆，再等我确认，不能直接写入长期画像。
```

### 写入时的明确说法

```md
请把这轮已确认的偏好写入本地长期画像，并追加一条记忆日志。
```

## 在 Trae 中怎么用

因为 `Trae` 更适合显式提示，所以建议你每次手动说。

### Trae 推荐提示词

```md
先按 xiaocao-clone 的流程执行。
如果这轮出现新的稳定偏好，请先生成候选记忆，不要直接写入。
等我确认后，再把内容写入本地长期画像文件。
```

### Trae 简短版

```md
使用 xiaocao-clone 用户记忆模式：
先候选，后确认，再写入长期画像。
```

## 推荐记忆触发语

下面这些话都适合触发记忆流程：

- “蒸馏我一下”
- “把这个记住”
- “以后按这个来”
- “更新我的长期画像”
- “写入我的偏好”
- “这条规则以后默认照做”

## 推荐候选记忆输出格式

```md
本轮候选记忆更新：

- workflow:
  - ...
- tools:
  - ...
- likes:
  - ...
- dislikes:
  - ...
- language_style:
  - ...
- decision_rules:
  - ...

是否写入长期画像？
```

## 写入日志建议格式

`memory/memory-log.private.jsonl` 每行一条 JSON，建议结构：

```json
{"date":"2026-04-13","type":"memory_write","confirmed":true,"categories":["workflow","tools","language_style"],"summary":"更新了工程流程、工具偏好和表达风格"}
```

## 注意事项

- 不要把密钥、密码、Token、联系方式写进长期记忆
- 不要把一次性情绪写进长期记忆
- 不要没确认就自动合并到长期画像
- 私有记忆文件不要提交到 GitHub
