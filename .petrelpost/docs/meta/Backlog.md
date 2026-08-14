# Backlog

待办事项的唯一权威来源。`README.md` 与 `SkillConventions.md` 中提到待办事项时，只做引用，不复制内容——避免同一份清单在多处维护导致不一致。

完成的事项直接删除或移到底部"已完成"区，不需要额外的归档流程；这份文件本身状态轻量，不接入 Rest 体系。

## 待处理

- [ ] **role-architecture**：路径迁移到 `.petrelpost/docs/collaboration/roles/`（目前可能仍在旧路径），entry-point marker 加 `petrelpost:` 命名空间前缀，补充"是否接入 Rest"的判断并在其 SKILL.md 中记录结论。
- [ ] **决策归档（decision-archivist）**：已读取 SKILL.md 全文，发现待对齐点：
  - ✅ **已确认**：`decision-archivist` 中命名空间 `.petrolpost/` 为笔误（GitHub 注册时打错），正确应为 `.petrelpost/`，迁移时需全文替换（`SKILL.md`、`README.md`、`references/*.md` 均涉及）
  - 路径需从 `.petrolpost/agent-decisions/` 迁移到 `.petrelpost/docs/decisions/`
  - 存储格式为 YAML（`decisions.yaml`/`staged-signals.yaml`/`config.yaml`）+ 渲染出 `DECISION_LOG.md`，与总纲设想的纯 Markdown 条目文件（`ADR-XXX.md`）路线不同，需专门讨论是否为此 skill 破例保留 YAML 方案
  - 状态枚举 `confirmed/pending/superseded/abandoned` 风格与 role-architecture 不同，V1 不强制统一，仅记录
  - 未见 entry-point marker 接入逻辑，需判断是否需要
  - 未做 Rest 集成评估；`pending` 状态长期未处理属于典型"随时间腐化"场景，初步判断应接入 Rest
- [ ] **OKR+PDCA**：同上，已存在但尚未接入总纲约定，需要逐条对齐。
- [ ] **skill-creator**：补充"Skill 完成基本功能后，判断是否接入 Rest"这一步提示，指向 `SkillConventions.md` 硬规则第 3 条。
- [ ] **Rest 体系**：目前只有概念设计，尚未实现（登记文件结构、触发逻辑、`runs/` 记录等均未落地）。

## 已完成

- [X] `SkillConventions.md` V1 版本写成并归档（`.petrelpost/docs/meta/`）。
- [X] 项目根 `README.md` 创建。
