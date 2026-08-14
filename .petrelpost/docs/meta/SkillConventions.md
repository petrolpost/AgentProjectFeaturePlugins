
# Skill Conventions (V1)

> Convention should describe proven constraints, not anticipated complexity.
> 总纲约束已被实践证明必要、且不固化就会互相冲突的东西；其余作为"当前理解"记录，不作硬规则。

这是 V1。它不追求理论闭合，只固化目前已达成共识、且**修改成本高**或**不固化就会互相冲突**的约束。其余内容放在文末"当前理解"部分，仅供未来遇到瓶颈时参考，不具约束力，随时可以推翻重写。

本文件是所有接入此生态的 Skill（`role-architecture`、未来的决策归档、OKR+PDCA、Rest 体系等）共同引用的总纲。任何 Skill 的 `SKILL.md` 在涉及跨 Skill 协作、状态归属、目录/命名规则时，应指向本文件，而不是各自重复定义。

---

## Skill 是什么

Skill 是一个可独立接入项目的能力模块。它可以拥有自己的状态、文档、命令和生命周期，并通过约定与其他 Skill 协作。

---

## 硬规则（V1，共 5 条）

### 1. `.petrelpost/` 命名空间

所有此生态产生的持久化内容，统一放在项目根目录下的 `.petrelpost/` 下，不直接写入项目原有的 `docs/`、`README` 等目录，避免与其他团队 / 其他 Agent 体系共用项目时产生路径冲突。

```
.petrelpost/
└── docs/
    ├── collaboration/roles/   ← role-architecture（历史路径例外，见下方"已知待整改项"）
    ├── decisions/             ← 决策归档（已对齐，见下方"已知待整改项"）
    ├── okr/                   ← OKR+PDCA（待接入）
    ├── maintenance/           ← Rest 体系
    └── meta/
        ├── SkillConventions.md ← 本文件（规则）
        └── Backlog.md          ← 待办事项（状态，唯一权威来源）
```

新建 Skill 一律遵循 `.petrelpost/docs/<domain>/` 的路径规则。**注意拼写是 `petrelpost`（petrel=海燕），不是 `petrolpost`（petrol=汽油）**——decision-archivist 曾在注册时误写成后者，新建/迁移 Skill 时留意核对，避免同一项目里出现两个几乎同名但实际不同的命名空间。

**本条只约束持久化内容的路径归属，不约束文件内部的存储格式**（YAML/JSON/纯 Markdown 等由各 Skill 自行决定，只要落在自己的目录内即可；例如 decision-archivist 用 YAML 存源真值、渲染出 Markdown 展示，这不是对本条的例外，而是本条本来就没管到这一层）。

**Entry-point marker 同样要套命名空间**，格式为 `petrelpost:<skill-name>:start` / `petrelpost:<skill-name>:end`，写入 `CLAUDE.md` / `AGENTS.md` 等文件时使用，避免与其他体系的 marker 撞名：

```markdown
<!-- petrelpost:role-architecture:start -->
...
<!-- petrelpost:role-architecture:end -->
```

Patch 时遵循幂等原则：marker 已存在则只替换区间内内容，不存在则追加，且**每个 Skill 只能改写自己名下的 marker 区块**，不能touch别的 Skill 的区块。

### 2. Canonical Owner（数据不互相踩）

每一种领域事实只能有一个权威归属 Skill（Canonical Owner）。例如：

- Task 的状态 → 权威来源是 role-architecture（或未来独立的任务体系）
- Decision 的状态 → 权威来源是决策归档
- OKR 的状态 → 权威来源是 OKR+PDCA
- 维护执行记录 → 权威来源是 Rest

**任何 Skill（包括 Rest）都不能直接改写不属于自己的权威状态字段。** 需要改变别的 Skill 的状态时，调用该 Skill 提供的公开命令（例如 `/role-task`），而不是直接改写对方的文件内容。

其他 Skill 若在自己的文档里引用了别的领域的事实（例如 Rest 的执行记录里提到某个 Task 的状态），应明确标注这是**引用/快照，非权威值**，避免出现两处记录同一事实但不同步的情况。

### 3. Rest 是可选的时间性能力

Rest 不是一个普通功能模块的对等物，而是这个生态里对"随时间可能变得不健康的状态"进行观察的机制。它不强制所有 Skill 接入。

判断标准只有一句话：**这个 Skill 维护的状态，会不会随时间变得不健康（腐化、堆积、偏离、长期未处理）？**

- 会 → 可以接入 Rest
- 不会 → 不接入

不需要展开成评估流程、检查清单或打分表——就用这一句话判断即可。判断结果（接入或不接入）建议在该 Skill 自己的 SKILL.md 里留一句话说明，避免以后被重复问一遍。

### 4. Rest 的最小学习闭环

Rest 的规则会演进，其他 Skill 需要一个了解"现在该怎么向 Rest 登记"的方式。V1 只约定最简流程：

```
Skill 判断需要接入 Rest
        ↓
检查 .petrelpost/docs/maintenance/ 是否存在（Rest 是否已装）
        ↓ 存在
读取 Rest 当前的登记说明，按当前格式直接写入登记条目
        ↓
后续由 Rest 自身的触发逻辑接管，无需该 Skill 再关心
```

V1 不预先设计 Schema 版本号、ChangeLog、`/rest-sync` 这类协议化机制——这些留到真正遇到"已登记的内容和新规则对不上"的问题时再按需引入（见文末"当前理解"）。

### 5. 自动行为必须留痕

Rest 或任何自动执行的检查/维护动作，执行后必须写一条记录（`.petrelpost/docs/maintenance/runs/Run-XXX.md`），哪怕只是简单几行"做了什么、发现了什么"。

理由很朴素：一个会自动修改或检查项目状态的系统，如果不留痕，出问题时无法追溯发生过什么。V1 不要求这条记录有精细的分类体系，先把"有没有记录"作为唯一门槛。

---

## 已知待整改项

具体清单见 [`Backlog.md`](./Backlog.md)（唯一权威来源，本文件不重复列出，避免多处维护导致不一致）。

---

## 当前理解（非规范，仅供未来参考）

以下内容是讨论过程中出现过、但 V1 有意不固化的方向。如果未来实践中确实遇到瓶颈，可以回来参考，但不应不经验证就直接照搬。

**Skill 的七维模型（草案）**：Capability / State / Protocol / Persistence / Lifecycle / Time Behavior / Rest Capability。可以用来理解一个 Skill 大致由哪些部分构成，但不作为每个 Skill 必须显式声明的规范结构。

**Rest 的三层拆分（草案）**：Protocol（规则本身，可能进一步分 Schema 格式与 Policy 行为哲学）/ Runtime（何时触发）/ Registry（登记与执行数据）。V1 只有 Registry 落地为文件，Protocol 和 Runtime 目前只是行为约定，没有独立文档。

**Finding 分级（草案）**：Rest 发现的问题可以分 Observation → Finding → Recommendation → Action 几个阶段，也可以进一步区分"无需行动 / 建议行动（转 Task/Decision/OKR Review/继续观察）"。V1 不做这个区分，统一先记为"发现"，要不要升级成 Task 或 Decision，由执行时随手判断即可。

**跨域操作的四级权限模型（草案）**：区分"改变权威状态 / 生成建议性产物 / 记录观察 / 调用其他 Skill 的公开命令"，比硬规则第 2 条更细。V1 只用第 2 条那一句话（不直接改别人的权威状态，需要时调用对方命令）覆盖，细分模型留作未来参考。

**状态枚举风格统一（草案）**：曾讨论过统一成驼峰无空格（如 `InProgress`），但 `role-architecture` 已用带空格写法（`In Progress`）。V1 不强制回改，新 Skill 可以自行选择风格，等真正因为风格不统一造成显示或解析问题时再回来处理。

**Rest 学习机制的协议化（草案）**：Schema 版本号 + ChangeLog + `/rest-sync` 命令这套机制曾被详细设计过，用于处理"Rest 规则更新后，已登记的旧内容如何跟上"。V1 判断这是提前解决尚未发生的问题，暂不引入，留到真的出现版本不兼容的实际案例后再决定要不要做、怎么做。

---

## 修订原则

本文件本身也遵循"只固化已验证必要的约束"的原则。新增硬规则前，先问：

1. 这是不是已经在实践中反复遇到、不定下来就会冲突的问题？
2. 现在不定，成本是不是会显著升高（比如涉及路径迁移、命名空间这类改动成本高的东西）？

两个问题都是"是"，才升级进硬规则；否则放进"当前理解"，继续观察。
