
# PetrelPost Skill 生态

一组可插拔的 Skill，用于给 Agent Project 提供统一的组织能力——角色定义、决策归档、OKR+PDCA、空闲维护（Rest）等。每个 Skill 可以独立接入不同项目，同时通过一份共同的总纲保持风格一致、数据不互相冲突。

## 这是什么

传统意义上的 Skill 往往是孤立的：各自定义目录、命令、状态命名，装得越多，风格越乱，数据也容易互相踩。PetrelPost 把这些 Skill 当作同一个生态里的成员，用一份共享约定（而不是每个 Skill 各写一遍）来解决：

- 放在哪：统一的目录 / 命名空间，避免和其他团队或其他 Agent 体系共用项目时产生冲突
- 谁说了算：每种事实只有一个权威归属 Skill，其他 Skill 只能引用、不能直接改写
- 谁来维护健康度：具有时间性的状态（会腐化、堆积、偏离的），可以选择接入 Rest 体系，由它做周期性观察和留痕

## 项目结构

```
.petrelpost/
└── docs/
    ├── collaboration/roles/   ← role-architecture（角色定义，已存在）
    ├── decisions/             ← decision-archivist（决策归档，已对齐总纲）
    ├── okr/                   ← OKR+PDCA（待接入）
    ├── maintenance/           ← Rest 体系（空闲维护，待接入）
    └── meta/
        ├── SkillConventions.md ← 生态总纲，所有 Skill 共同遵循
        └── Backlog.md           ← 待办事项，唯一权威来源
```

## 现有 Skill

| Skill                  | 说明                                                        | 状态                               |
| ---------------------- | ----------------------------------------------------------- | ---------------------------------- |
| `role-architecture`  | 角色定义、任务登记、entry-point 接入                        | 已存在，尚未对齐总纲（见待整改项） |
| `decision-archivist` | 决策记录与归档，标记/精读两阶段工作流                       | 已对齐总纲                         |
| OKR+PDCA               | 目标与周期性 Plan-Do-Check-Act                              | 已存在，尚未接入总纲               |
| Rest                   | 空闲时对具有时间性的状态做巡检与维护，供其他 Skill 按需接入 | 概念设计完成，尚未实现             |

## 给 Agent 的入口

如果你是被派去处理这个项目的 Agent（Claude 或其他），先读 [`AGENTS.md`](AGENTS.md)，不要跳过直接改文件。

## 生态总纲

所有跨 Skill 的共同约定（命名空间、状态归属原则、Rest 接入判断标准等）都写在：

[`.petrelpost/docs/meta/SkillConventions.md`](.petrelpost/docs/meta/SkillConventions.md)

这是一份 **V1** 文档，只固化目前已验证必要、且不定下来就会冲突的规则；其余讨论过但尚未验证的方向记录在文末"当前理解"部分，供未来遇到瓶颈时参考，不作为硬性规范。新建或修改任何 Skill 前，建议先读这份总纲。

## 待办

见 [`.petrelpost/docs/meta/Backlog.md`](.petrelpost/docs/meta/Backlog.md)（唯一权威来源）。具体改动分别在各自的对话/任务里处理，不在此直接执行。

## 设计原则

> Convention should describe proven constraints, not anticipated complexity.
> 总纲约束已被实践证明必要的东西，而不是提前解决所有可能的问题。

这是一个会随实际使用不断演化的 Agent 组织体系，而不是一次性定型的软件架构。宁可先跑起来，用真实反馈暴露设计缺陷，再迭代规则。
