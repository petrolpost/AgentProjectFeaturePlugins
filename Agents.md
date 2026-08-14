
# AGENTS.md

给进入本项目工作的 Agent（Claude 或其他）的入口说明。人类协作者请看 `README.md`。

## 开始工作前，必须先做的事

1. **读 [`.petrelpost/docs/meta/SkillConventions.md`](.petrelpost/docs/meta/SkillConventions.md)**。这是本项目所有 Skill 共同遵守的总纲（V1，只包含已验证必要的硬规则）。任何涉及跨 Skill 协作、目录结构、状态归属、Rest 接入判断的改动，都必须符合这份总纲，不要在总纲之外自行发明规则。
2. **待办事项只看 [`.petrelpost/docs/meta/Backlog.md`](.petrelpost/docs/meta/Backlog.md)**。这是唯一权威来源，不要在别处（包括本文件、README）寻找或记录待办项，也不要重复维护第二份清单。

## 本项目是什么（一句话）

一组可插拔 Skill 的元设计项目：定义角色、决策归档、OKR+PDCA、Rest（空闲维护）等 Skill 如何在同一个 Agent Project 里共存、不互相冲突。详细介绍见 `README.md`。

## 硬约束（摘要，完整定义见 SkillConventions.md）

- 所有持久化内容放在 `.petrelpost/` 命名空间下，不要直接写入项目原有目录。
- 不要直接改写不属于自己的 Skill 的权威状态；需要修改时调用对方提供的命令。
- 不要在没有真实需求验证的情况下，把 `SkillConventions.md` 里"当前理解"部分的草案直接固化为新硬规则。

## Entry-point marker 区块

各 Skill 完成对齐总纲后，会在下方追加自己的 marker 区块（格式 `petrelpost:<skill-name>:start/end`）。**修改时只能改写自己名下的区块，不能touch其他区块。**

<!-- petrelpost:meta:start -->

（本区块由总纲/待办体系使用，如需变更 AGENTS.md 本身的入口说明，改这里）

<!-- petrelpost:meta:end -->
