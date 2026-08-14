# Capability Discovery Prototype

用于在 Codex / Cursor 类 Agent 中验证 PetrelPost 可插拔性的最小闭环：

`Skill → 声明/注册能力 → 能力发现 → 通过公开入口协作`

本实验不实现 Python runtime，也不预设一个正式的插件框架。让 Agent 自己通过 Skill 描述完成发现与协作。

## 实验目标

1. Consumer 只依赖 capability，不依赖 provider 的名字。
2. Provider 通过 Skill 的公开入口提供能力。
3. Agent 能从当前可见的 Skills 中发现 capability provider。
4. 替换 capability provider 时，consumer 不需要修改。

## 当前实验

- `skills/greeter/SKILL.md`：声明 `greeting` 能力及公开入口。
- `skills/consumer/SKILL.md`：只声明需要 `greeting`，并规定发现规则。
- `registry/capabilities.yaml`：暂作为实验观察用的显式登记，不要求 Agent 必须依赖它。

## 如何测试

将本目录中的两个 Skill 放入一个 Codex / Cursor 类 Agent 可发现的 Skill 目录，然后给 Agent 一个简单任务，例如：

> 请使用 capability-consumer 完成一次 greeting。

观察 Agent 是否能够：

1. 识别 consumer 需要 `greeting`；
2. 找到提供 `greeting` 的 Skill；
3. 阅读 provider 的公开入口；
4. 完成 greeting；
5. 全程不依赖 provider 的固定名称。

## 第二轮实验

复制 `greeter` 为另一个 provider，提供同一个 `greeting` 能力，然后移除原 provider。再次执行相同任务。

如果 consumer 无需修改仍能完成任务，说明 capability 确实成为了协作边界。

## 暂不验证

- 自动注册机制
- 正式 Registry 协议
- 版本协商
- 依赖解析
- 动态加载
- 权限模型
- 分布式发现

这些问题等最小闭环被实际验证后再决定是否需要。
