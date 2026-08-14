# Skill-to-Skill Collaboration

这是下一轮最小实验：不使用 Registry，不使用 `skill.yaml`，也不要求一个专门的 consumer Skill。

## 假设

一个普通 Skill 的 `SKILL.md` 本身可以同时承担：

- 能力声明：我能做什么
- 使用说明：别人应该如何使用我
- 协作边界：当它需要另一个能力时，通过公开入口发现并使用另一个 Skill

Agent 根据当前任务，自主发现能够完成任务的 Skill，并让 Skill 之间通过公开入口协作。

## 当前实验

本目录有三个普通 Skill：

- `skills/banana-helper/SKILL.md`：提供 `greeting`
- `skills/formal-language-helper/SKILL.md`：也提供 `greeting`
- `skills/weather-helper/SKILL.md`：提供 `weather-greeting`，并要求在执行时发现并使用一个提供 `greeting` 的 Skill

没有 Registry，也没有 machine-readable manifest。

## 测试

让 Codex / Cursor 类 Agent 执行：

> 请使用 `prototype/skill-native-capability` 中可用的 Skills 完成一次 weather greeting。

不要告诉 Agent 哪个 Skill 提供 `greeting`，也不要告诉它应该选择哪个 greeting provider。

## 观察重点

1. Agent 能否发现 `weather-greeting` 对应的 Skill？
2. Agent 能否理解 `weather-helper` 需要另一个 `greeting` 能力？
3. Agent 能否发现多个 `greeting` provider？
4. 面对多个同能力实现时，Agent 自然采用什么选择行为？
5. Agent 能否通过所选 Skill 的公开入口完成 Skill-to-Skill 协作？
6. 整个过程是否仍然不需要 Registry、manifest 或专门的 consumer Skill？

本实验不规定 Provider Selection 策略，也不引入新的协议字段。这里只观察 Agent 面对多个能力实现时的自然行为。
