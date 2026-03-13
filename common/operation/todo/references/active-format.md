# active 格式

一句话定位：规定 `active.md` 的固定格式，保证简单可读。

## 固定模板

```md
# P0
- [ ] [支付链路] 下线前移除 PaymentService 中的 mock 支付分支 (YYYY-MM-DD) @path:src/payment/PaymentService.ts @task-id:xxx @todo-id:xxx

# P1
- [ ] [登录态] 为 SessionManager 补 token 过期后的统一兜底与刷新逻辑 (YYYY-MM-DD) @path:src/auth/SessionManager.ts @todo-id:xxx

# P2
- [ ] [会话列表] 合并 ConversationCell 与 NotificationCell 的重复样式拼装逻辑 (YYYY-MM-DD) @path:src/chat/ConversationCell.ts @todo-id:xxx
```

## 格式约束

1. 任务必须包含创建日期 `(YYYY-MM-DD)`。
2. id 字段
   1. task-id: 若当前在 coding-workflow 中, 取 `plan.md` 的 Task-ID
   2. todo-id: 唯一雪花id
3. 不增加额外字段（如 `desc`/`see`/`status`）。
4. 描述必须一句话说清。如果关联class/function, 需要在描述中体现。
5. 可选追加路径标记：`@path:<relative-path>`。
6. 路径标记仅用于定位，不代表已完成；路径变更时应更新或移除标记，但任务仍保留。
7. 仅当当前本来就在修改该文件、且补一条行内注释能显著提升回溯效率时，才附加代码内 todo 注释。
   1. 不为记录 ToDo 而额外打开或修改无关文件。
   2. 注释内容应与 `active.md` 的任务文案一致，并忽略 `@path`。
   3. 如 `// TODO: [登录态] 为 SessionManager 补 token 过期后的统一兜底与刷新逻辑 (2026-03-13) @todo-id:xxx`

## 优先级

- `P0`: 阻塞问题或当前核心任务。
- `P1`: 重要改进，建议近期处理。
- `P2`: 可选优化，不影响主流程。
