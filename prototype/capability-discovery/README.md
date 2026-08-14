# Capability Discovery Prototype

用于验证 PetrelPost 可插拔性的最小闭环：

`Skill → 注册能力 → 能力发现 → 通过公开入口协作`

本原型刻意不解决版本、依赖、生命周期、自动安装等问题。

## 实验目标

1. Consumer 只依赖 capability，不依赖 provider 的名字。
2. Provider 通过公开入口提供能力。
3. Capability registry 可以被发现。
4. 替换 capability provider 时，consumer 不需要修改。

## 当前实验

- `greeter`：提供 `greeting` 能力。
- `consumer`：发现 `greeting`，并通过公开入口调用它。
- `registry/capabilities.yaml`：实验用的最小能力登记表。

## 暂不验证

- 自动注册
- 版本协商
- 依赖解析
- 动态加载
- 权限模型
- 分布式发现

这些问题等最小闭环被实际验证后再决定是否需要。
