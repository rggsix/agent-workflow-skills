# 写入流程

一句话定位：定义 `project-memory` 在哪些时机落盘，以及每类文件的最小写入模板。

## 写入时机

1. 新任务接手且已完成意图对齐后，若现有记忆缺口明显，先补 `current.md` 的初始状态。
2. 完成规划后，更新 `current.md`，必要时向 `decisions.md` 追加本轮关键取舍。
3. 完成实质性编码后，向 `log/` 追加一次记录，并刷新 `current.md` 的实际进展与风险。
4. 完成验证、review 或复检后，把验证结论写入最近一条 `log/` 或追加新记录。
5. 收尾或准备切换会话前，刷新 `current.md`，确保下次能直接接管现场。

## 文件职责

- `project-profile.md`: 少量稳定事实，变化很少；只有项目画像变化时才更新。
- `collaboration-preferences.md`: 只有观察到稳定偏好并达到“下次值得继续沿用”时才更新。
- `current.md`: 覆盖式更新，永远表示“此刻现场”。
- `decisions.md`: 追加式更新，每条决策都要写明原因和影响范围。
- `log/YYYY-MM.md`: 追加式更新，按时间逆序或顺序保持一致即可。

## 最小模板

`current.md` 最少包含：

```md
# Current

- Date: 2026-03-14
- Repo: /abs/path/to/repo
- Cwd: /abs/path/to/repo/some/module
- Goal: 当前正在推进什么
- Focus: 当前主要文件、模块或子目录
- Recent: 最近一次实质性改动或验证
- Risks: 尚未闭环的问题
- Next: 下一步 1-3 条
```

`log/YYYY-MM.md` 的单条记录最少包含：

```md
## 14:30 task: 简短标题

- Goal: 本轮目标
- Actions: 实际执行了什么
- Files: 相关文件或目录
- Verify: 做了什么验证，结果如何
- Decision: 若有关键取舍，写明结论
- Risk: 留下的风险或未知项
- Next: 建议下次继续做什么
```

## 禁止事项

- 不在一次小改动后频繁重写所有记忆文件。
- 不把 [ToDo](../../todo/SKILL.md) 列表复制进 `current.md`。
- 不在 `log/` 里只写“已完成”“已处理”，必须带动作和结果。
