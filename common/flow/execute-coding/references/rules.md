# 规则

一句话定位：按 `plan.md` 执行编码，保持顺序与边界。

## 必须

1. 读取 `coding-workflow` 的 `plan.md` 并按顺序执行。
2. 不得跳过或删除计划条目。
3. 允许实现细节调整，但必须输出“偏差说明”（一句话）。
4. 仅当需要增删计划条目或影响范围越界时触发 `human-in-loop gate`。
5. 执行前必须再次检查仓库 `AGENTS.md` 中是否存在与项目规范、代码规范、style guide、project rules、architecture constraints 相关的 project 级 skills。
6. 若 `plan.md` 已标记相关 project 级 skills 或约束来源，执行阶段必须读取并尝试应用对应 skill / references，而不是只依赖 planning 的摘要。
7. 在进入正式编码前，必须显式自述类似：
   - `我将检查是否有 project 相关 skills`
   - `我将阅读并尝试在本环节应用 xxx project skill`
8. 若未找到相关 project 级 skills，也要显式说明“已检查但未发现适用的 project 相关 skills”。

## 禁止

- 修改 `plan.md`。
- 擅自扩展需求。
- 改变计划顺序。
- 跳过 project 级规范检查后直接编码。
