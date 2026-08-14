# Skill-to-Skill Collaboration

这是下一轮最小实验：不使用 Registry，不使用 `skill.yaml`，也不要求一个专门的 consumer Skill。

## 假设

一个普通 Skill 的 `SKILL.md` 本身可以同时承担：

- 能力声明：我能做什么
- 使用说明：别人应该如何使用我
- 协作边界：当它需要另一个能力时，通过公开入口发现并使用另一个 Skill

Agent 根据当前任务，自主发现能够完成任务的 Skill，并让 Skill 之间通过公开入口协作。

## 当前实验

本目录只有两个普通 Skill：

- `skills/banana-helper/SKILL.md`：提供 `greeting`
- `skills/weather-helper/SKILL.md`：提供 `weather-greeting`，并要求在执行时发现并使用一个提供 `greeting` 的 Skill

没有 Registry，也没有 machine-readable manifest。

## 测试

让 Codex / Cursor 类 Agent 执行：

> 请使用 `prototype/skill-native-capability` 中可用的 Skills 完成一次 weather greeting。

不要告诉 Agent `banana-helper` 是 `greeting` provider，也不要告诉它应该如何完成协作。

## 观察重点

1. Agent 能否发现 `weather-greeting` 对应的 Skill？
2. Agent 能否理解 `weather-helper` 需要另一个 `greeting` 能力？
3. Agent 能否再次发现提供 `greeting` 的 Skill？
4. Agent 能否通过另一个 Skill 的公开入口完成 Skill-to-Skill 协作？
5. 整个过程是否仍然不需要 Registry、manifest 或专门的 consumer Skill？

本实验不规定 Provider Selection 策略，也不引入新的协议字段。这里只观察 Agent 是否能够根据普通 Skill 的自然语言定义完成协作。
