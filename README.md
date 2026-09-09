# Ripple

[中文](#中文) | [English](#english)

Ripple is a Codex skill for keeping product changes aligned with their intended scope, evidence, authorization, and acceptance criteria.

<a id="中文"></a>

## 中文

### 简介

Ripple 用于处理已有产品中的 UI、筛选、表单、文案、默认值、状态流转和业务规则变更，也适用于产品侧缺陷修复。它会先理解业务语义和现有实现，再约束修改范围、设计依据、实现授权和验证证据。

它不会授予额外的文件、网络、提交、部署或生产环境权限，也不会自动安装 Superpowers。

### 仓库结构

本仓库参考 [obra/superpowers](https://github.com/obra/superpowers) 的组织方式，将可安装 Skill 放在 `skills/` 下：

```text
ripple/
├── README.md
└── skills/
    └── ripple/
        ├── SKILL.md
        ├── agents/
        │   └── openai.yaml
        └── references/
            ├── authorization-and-isolation.md
            ├── evidence-contracts.md
            ├── superpowers-integration.md
            └── verification.md
```

### 安装

#### 方法一：使用 Skill Installer（推荐）

在 Codex 中输入：

```text
使用 $skill-installer 从 https://github.com/Itkeytome/ripple/tree/master/skills/ripple 安装 ripple
```

#### 方法二：手动安装

macOS 或 Linux：

```bash
git clone https://github.com/Itkeytome/ripple.git
mkdir -p ~/.agents/skills
cp -R ripple/skills/ripple ~/.agents/skills/ripple
```

Windows PowerShell：

```powershell
git clone https://github.com/Itkeytome/ripple.git
New-Item -ItemType Directory -Force "$HOME/.agents/skills"
Copy-Item -Recurse "ripple/skills/ripple" "$HOME/.agents/skills/ripple"
```

Codex 通常会自动发现新增 Skill；如果没有出现，请重启 Codex。

### 使用

显式调用：

```text
使用 $ripple 修改订单筛选：只调整首页，沿用后台已有字段规则，先给我原型确认。
```

```text
使用 $ripple 修复编辑表单的默认值和回显问题，不要影响新建流程。
```

Ripple 也允许隐式调用：当请求与 `SKILL.md` 中的适用范围匹配时，Codex 可以自动选择它。

### 使用效果

Ripple 会根据任务规模提供相称的约束和证据，通常包括：

- 建立需求边界和可验证的验收条件。
- 按业务语义检查同类入口、共享组件和请求参数。
- 区分已验证事实、推断、冲突和不可访问的信息。
- 在需要时先提供隔离原型，并把批准绑定到明确范围。
- 实现后验证目标行为和范围外不变条件，如实报告未运行或受阻项目。

它的目标不是增加流程数量，而是减少漏改、越权修改、设计漂移和缺少证据的完成声明。

### 适用边界

Ripple 不用于纯只读解释、通用代码审查或不影响产品行为的基础设施变更。用户只要求分析时，它不会自行进入实现、提交或部署阶段。

---

<a id="english"></a>

## English

### Overview

Ripple is designed for changes to an existing product's UI, filters, forms, labels, defaults, state transitions, and business rules, including product-facing bug fixes. It first establishes the business meaning and current implementation, then keeps scope, design provenance, implementation authorization, and verification evidence aligned.

Ripple does not grant additional file, network, commit, deployment, or production permissions, and it does not install Superpowers automatically.

### Repository layout

Inspired by the organization of [obra/superpowers](https://github.com/obra/superpowers), installable skills live under `skills/`:

```text
ripple/
├── README.md
└── skills/
    └── ripple/
        ├── SKILL.md
        ├── agents/
        │   └── openai.yaml
        └── references/
            ├── authorization-and-isolation.md
            ├── evidence-contracts.md
            ├── superpowers-integration.md
            └── verification.md
```

### Installation

#### Option 1: Skill Installer (recommended)

Enter this prompt in Codex:

```text
Use $skill-installer to install ripple from https://github.com/Itkeytome/ripple/tree/master/skills/ripple
```

#### Option 2: Manual installation

macOS or Linux:

```bash
git clone https://github.com/Itkeytome/ripple.git
mkdir -p ~/.agents/skills
cp -R ripple/skills/ripple ~/.agents/skills/ripple
```

Windows PowerShell:

```powershell
git clone https://github.com/Itkeytome/ripple.git
New-Item -ItemType Directory -Force "$HOME/.agents/skills"
Copy-Item -Recurse "ripple/skills/ripple" "$HOME/.agents/skills/ripple"
```

Codex normally detects newly installed skills automatically. Restart Codex if the skill does not appear.

### Usage

Explicit invocation:

```text
Use $ripple to change the order filters. Limit the change to the home page, reuse the existing admin rules, and show me a prototype first.
```

```text
Use $ripple to fix default values and state restoration in the edit form without changing the create flow.
```

Ripple can also be invoked implicitly when a request matches the scope described in `SKILL.md`.

### Expected effect

Depending on the size and risk of the request, Ripple typically helps the agent:

- Establish clear scope and observable acceptance criteria.
- Inspect equivalent entry points, shared components, and request parameters by business meaning.
- Separate verified facts from inference, conflicts, and inaccessible evidence.
- Present an isolated prototype when needed and bind approval to an explicit scope.
- Verify target behavior and out-of-scope invariants, reporting skipped or blocked checks honestly.

The goal is not to add ceremony. It is to reduce missed surfaces, unauthorized changes, design drift, and unsupported completion claims.

### Scope boundaries

Ripple is not intended for read-only explanations, generic code reviews, or infrastructure-only work without product behavior impact. When the user asks only for analysis, it does not independently proceed to implementation, commits, or deployment.

## References

- [OpenAI: Build skills](https://developers.openai.com/codex/skills)
- [obra/superpowers](https://github.com/obra/superpowers)
