# Checklist

一句话定位：确保 project-review 按项目规范复查闭环执行，且输出结构完整。

## 执行前

1. 已确定本轮 diff 范围。
2. 已确认相关文件清单。
3. 已检查 `project` 相关 skill 是否存在。
4. 若存在 `project` skill，已读取 `project/SKILL.md`。
5. 若存在 `project` skill，已读取与本次改动相关的必读引用。

## 执行后

1. 若无 `project` skill，已输出"无相关skill, 跳过此步骤, 流程继续进行"。
2. 若有 `project` skill，已输出 `Reviewed References`，且内容与实际读取文件一致。
3. 若有 `project` skill，已输出检查清单与 review 结论。
4. 检查清单已覆盖 `文件 - 类 - 方法`。
5. 未在缺少 `project` 规范阅读证据的情况下输出 `Project Review OK`。
6. 轮次未超过上限，或已触发 human-in-loop。
