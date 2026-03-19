# 流程规则

一句话定位：定义 coding-workflow 的 6 步流程与执行边界。

## 6步流程

1. 意图对齐（技术返述，确认后再继续）
2. 规划（调用 `planning`，结果写入 `plan.md`）
3. ToDo 同步（规划后预置：风险项/后续项；执行前先做“入口暴露检查”）
4. 编码执行（按 `plan.md` 中的 planning 结果顺序推进；可调实现细节但需记录偏差；仅在需增删计划条目或越界时触发 human-in-loop）
5. AI review（自检闭环）
6. 项目记忆收尾（调用 `project-memory`，把当前状态、关键决策与最近进展写回持久记忆）

## 步骤与技能映射
**每一步都要开启单独的 subagent 执行, 你负责监督与验收**
1. 步骤1 意图对齐 -> `intent-align`
2. 步骤2 规划 -> `planning`
3. 步骤3 ToDo 同步（规划后） -> `precoding-todo`
4. 步骤4 编码执行 -> `execute-coding`（遇阻断走 `human-in-loop gate`）
5. 步骤5 AI review -> `ai-review`
6. 步骤6 项目记忆收尾 -> `project-memory`

## 边界

- 本 skill 的职责是维护 plan 并按步骤唤起对应 skill，不替代被唤起 skill 的细则。
- 涉及状态写入时必须遵守 workspace 路径映射。
- 默认不包含测试、日志沉淀、项目 skills 更新（可后置）。
- 规划阶段通过 `planning` 输出并写入 `plan.md`，后续步骤只读该文件。
- 步骤3前必须显式检查：本轮是否新增或暴露了用户可触发入口 / 状态入口，以及后续主链路是否完整。
- 若入口已暴露但主链路未闭合，不得直接给出“无 ToDo 候选”。
- 步骤6是 workflow 默认收尾步骤；完成步骤5后不得直接宣告结束，需先完成 `project-memory` 写回。

## 完成条件

- 每一步执行前自述: "我当前在 `coding-workflow` 的流程中, 目前在`步骤{步骤号} {步骤名}`"
- 当前 plan 全部打钩。
