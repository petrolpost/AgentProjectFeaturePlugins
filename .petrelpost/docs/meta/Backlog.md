
# Backlog

待办事项的唯一权威来源。`README.md` 与 `SkillConventions.md` 中提到待办事项时，只做引用，不复制内容——避免同一份清单在多处维护导致不一致。

完成的事项直接删除或移到底部"已完成"区，不需要额外的归档流程；这份文件本身状态轻量，不接入 Rest 体系。

## 待处理

- [ ] **role-architecture**：路径迁移到 `.petrelpost/docs/collaboration/roles/`（目前可能仍在旧路径），entry-point marker 加 `petrelpost:` 命名空间前缀，补充"是否接入 Rest"的判断并在其 SKILL.md 中记录结论。
- [ ] **决策归档**：已存在但尚未接入 `SkillConventions.md` 的任何约定，需要按硬规则 1-5 逐条对齐（命名空间路径、Canonical Owner 声明、是否接入 Rest 等）。
- [ ] **OKR+PDCA**：同上，已存在但尚未接入总纲约定，需要逐条对齐。
- [ ] **skill-creator**：补充"Skill 完成基本功能后，判断是否接入 Rest"这一步提示，指向 `SkillConventions.md` 硬规则第 3 条。
- [ ] **Rest 体系**：目前只有概念设计，尚未实现（登记文件结构、触发逻辑、`runs/` 记录等均未落地）。

## 已完成

- [X] `SkillConventions.md` V1 版本写成并归档（`.petrelpost/docs/meta/`）。
- [X] 项目根 `README.md` 创建。
