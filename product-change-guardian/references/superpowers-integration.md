# Superpowers Integration

## 角色边界

将 Guardian 作为产品变更约束层：维护业务语义、影响范围、设计依据、有效授权与产品验收。不要复制通用调试、TDD、计划、代码审查的完整流程。

只使用当前环境实际提供且适用的 Skill。未安装 Superpowers 不阻塞 Guardian 独立工作，也不需要擅自安装、联网或修改全局配置。

## 组合规则

先读取当前已安装版本的规则，再协调流程。不要假设网上最新版本与用户本地相同，也不要把本文件视为覆盖其他 Skill 的优先级声明。

| 阶段 | 组合方式 |
|---|---|
| 需求与方案 | 适用时复用 brainstorming；将 Requirement Brief、Impact Map、Design Provenance 融入同一方案 |
| 缺陷定位 | 适用时复用 systematic-debugging；Guardian 约束实际影响与修改范围 |
| 复杂实现计划 | 复用 writing-plans 或现有项目计划；避免生成两份重复计划 |
| 实现 | 复用 test-driven-development 和代码审查；产品批准不等于跳过这些独立要求 |
| 交付 | 复用 verification-before-completion；补上 Reset、回显、请求参数及范围外回归证据 |

已有批准只有在指向同一方案版本、范围和行为，并满足所有适用 Gate 时才能复用。不同 Skill 不应对同一个已满足的条件反复索要同一批准；也不能拿某个宽松条件跳过另一个尚未满足的要求。

## “直接改”与设计确认

Guardian 的直接授权分支保留自原压力测试 Scenario 2，不是对 Superpowers 所有版本的兼容性保证。

明确区分“用户允许不制作原型”和“所有适用的实现前 Gate 都已满足”。如果当前流程要求先展示具体设计再获得确认，尚未满足时就完成那一步；如果用户的明确指令依当前优先级允许跳过相应步骤，则记录该指令与范围，不重复确认。

不要因为规则存在疑问而无限循环：说明唯一尚未满足的条件，完成它即可；不重新启动整套流程。纯读取任务也不应被 Guardian 强制转为产品开发任务。

## 版本与外部参考

以下公开文件于 2026-09-09 用于本次设计对照；`main` 是可变分支，运行时以实际安装版本和当前有效指令为准。本包并未安装或执行 Superpowers。

- [writing-skills](https://github.com/obra/superpowers/blob/main/skills/writing-skills/SKILL.md)：参考按失败类型设计规则、基线与启用后对照测试的思路。
- [brainstorming](https://github.com/obra/superpowers/blob/main/skills/brainstorming/SKILL.md)：参考按任务规模调整设计产物的思路；其设计批准要求不能被 Guardian 默默取消。
- [verification-before-completion](https://github.com/obra/superpowers/blob/main/skills/verification-before-completion/SKILL.md)：参考让成功声明对应当前证据的思路。
- [using-superpowers](https://github.com/obra/superpowers/blob/main/skills/using-superpowers/SKILL.md)：对照流程组合与用户指令处理方式。

本次新增的范围绑定、原型隔离、证据字段和测试场景属于 Guardian 的设计修改，不宣称来自上游或已经经上游验证。