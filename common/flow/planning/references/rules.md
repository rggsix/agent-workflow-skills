# 规则

一句话定位：定义规划的最小产出与边界。

## 必须

1. 只做规划，不执行修改。
2. 产出必须是 spec-lite（可执行步骤）。
3. 规划结果必须写入 `coding-workflow` 的 `plan.md`。
4. 规划包含最小观察：目标位置 + 约束要点。
5. `plan.md` 必须包含“人类输入原文”和“AI返述确认”。
6. 规划默认精确到 文件 / 模块 / 方法 / 修改动作，不默认细化到变量或具体代码实现，除非该命名本身属于关键设计决策。
7. 规划前必须检查仓库 `AGENTS.md` 中是否存在与项目规范、代码规范、style guide、project rules、architecture constraints 相关的 project 级 skills。
8. 规划前必须先读取一次 `project-memory`；若记忆文件存在，至少读取 `current.md` 与 `project-profile.md`，用于恢复当前现场与长期稳定事实。
9. 若存在相关 project 级 skills，必须读取与本次任务相关的 skill / references，并把这些内容视为规划约束来源。
10. 在进入正式规划前，必须显式自述类似：
   - `我将先读取 project-memory 的 current.md 与 project-profile.md`
   - `我将检查是否有 project 相关 skills`
   - `我将阅读并尝试在本环节应用 xxx project skill`
11. 若未找到相关 project 级 skills，也要显式说明“已检查但未发现适用的 project 相关 skills”。

## 禁止

- 写长篇背景解释。
- 产出不可执行的抽象描述。
- 在未确认代码事实前，臆造变量名、方法签名或具体实现细节。
