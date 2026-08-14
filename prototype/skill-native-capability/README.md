# Skill-native Capability Discovery

这是下一轮最小实验：不使用 Registry，不使用 `skill.yaml`，也不要求一个专门的 consumer Skill。

## 假设

一个普通 Skill 的 `SKILL.md` 本身可以同时承担：

- 能力声明：我能做什么
- 使用说明：别人应该如何使用我

Agent 根据当前任务，自主发现能够完成任务的 Skill，并通过其公开入口协作。

## 当前实验

本目录只有两个普通 Provider Skill：

- `skills/banana-helper/SKILL.md`：提供 `greeting`
- `skills/weather-helper/SKILL.md`：提供 `greeting`

没有 Registry，也没有 machine-readable manifest。

## 测试

让 Codex / Cursor 类 Agent 执行：

> 请使用 `prototype/skill-native-capability` 中可用的 Skills 完成一次 greeting。

不要告诉 Agent provider 的名称，也不要告诉它应该选择哪个。

## 观察重点

1. Agent 能否从普通 `SKILL.md` 中发现 `greeting` 能力？
2. 没有 `skill.yaml` / Registry 时是否仍能完成协作？
3. 两个 Provider 同时存在时，它如何选择？

本实验不规定 Provider Selection 策略。这里只观察 Agent 的自然行为。
