# active 格式

一句话定位：规定 `active.md` 的固定格式，保证简单可读。

## 固定模板

```md
# P0
- [ ] [需求标签] 待办事项简述 (YYYY-MM-DD) @path:src/foo/bar.ts @task-id:xxx @todo-id:xxx

# P1
- [ ] [需求标签] 待办事项简述 (YYYY-MM-DD)

# P2
- [ ] [需求标签] 待办事项简述 (YYYY-MM-DD) @path:src/baz/qux.ts
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
7. 如果关联文件, 且能关联到具体行, 需要在代码中标记todo注释, 用于todo反向追踪
   1. 如 `// todo {todo完整内容, 与active.md一致, 并忽略@path}`

## 优先级

- `P0`: 阻塞问题或当前核心任务。
- `P1`: 重要改进，建议近期处理。
- `P2`: 可选优化，不影响主流程。
