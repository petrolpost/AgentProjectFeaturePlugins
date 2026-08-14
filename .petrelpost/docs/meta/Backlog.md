
# Backlog

待办事项的唯一权威来源。`README.md` 与 `SkillConventions.md` 中提到待办事项时，只做引用，不复制内容——避免同一份清单在多处维护导致不一致。

完成的事项直接删除或移到底部"已完成"区，不需要额外的归档流程；这份文件本身状态轻量，不接入 Rest 体系。

## 待处理

- [ ] **role-architecture**：路径迁移到 `.petrelpost/docs/collaboration/roles/`（目前可能仍在旧路径），entry-point marker 加 `petrelpost:` 命名空间前缀，补充"是否接入 Rest"的判断并在其 SKILL.md 中记录结论。
- [ ] **OKR+PDCA**：已存在但尚未接入总纲约定，需要逐条对齐。
- [ ] **skill-creator**：补充"Skill 完成基本功能后，判断是否接入 Rest"这一步提示，指向 `SkillConventions.md` 硬规则第 3 条。
- [ ] **Rest 体系**：目前只有概念设计，尚未实现（登记文件结构、触发逻辑、`runs/` 记录等均未落地）。decision-archivist 已声明"接入 Rest"，待 Rest 上线后需要完成它的实际登记（`staged-signals.yaml` 积压标记、`decisions.yaml` 待补全字段、⚠️ 潜在冲突三类）。

## 已完成

- [X] `SkillConventions.md` V1 版本写成并归档（`.petrelpost/docs/meta/`）。
- [X] 项目根 `README.md` 创建。
- [X] **decision-archivist**：命名空间拼写（petrolpost→petrelpost）与路径迁移（`.petrolpost/agent-decisions/` → `.petrelpost/docs/decisions/`）已核实完成，SKILL.md/README.md/references/*.md 均无残留。
- [X] **decision-archivist**：entry-point marker 接入逻辑已补齐（首次初始化时 patch 写入 `AGENTS.md`，每次全量梳理 Step 6 后刷新决策数/待补全数/潜在冲突数），见 SKILL.md「存储结构」一节。
- [X] **decision-archivist**：Rest 接入判断已在 SKILL.md 对齐声明中记录（结论：接入，待 Rest 体系落地后登记，见上方"待处理"区 Rest 体系条目）。
- [X] **decision-archivist**：存储格式（YAML + 渲染）经核实，`SkillConventions.md` 硬规则本身并未规定文件内部格式，不存在"申请例外"的问题；已在硬规则1后补一句范围说明（存储格式不属总纲管辖），避免以后再有 Skill 误读出不存在的冲突。
