# Checklist

一句话定位：确保 project-review 按项目规范复查闭环执行，且输出结构完整。

## 执行前

1. 已确定本轮 diff 范围。
2. 已确认相关文件清单。
3. 已检查 `project` 相关 skill 是否存在。

## 执行后

1. 若无 `project` skill，已输出"无相关skill, 跳过此步骤, 流程继续进行"。
2. 若有 `project` skill，已输出检查清单与 review 结论。
3. 检查清单已覆盖 `文件 - 类 - 方法`。
4. 轮次未超过上限，或已触发 human-in-loop。
