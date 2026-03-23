# 规则

一句话定位：定义 project-review 如何查找 `project` skill、输出检查清单，并在 3 轮内完成 包括但不限于 项目书写规范/三方库与基础库使用规范 等复查(**主要参考project skill具体要求什么, 所有要求都要阅读并遵守**)。

## 必须

1. ‼️输入范围：仅基于本轮改动 diff 与相关文件。
2. ‼️先查找是否存在 `project` 相关 skill。
   - 若无，必须输出"无相关skill, 跳过此步骤, 流程继续进行"，然后结束当前步骤并返回 workflow 继续执行。
   - 若有，必须先输出"我将阅读 project skill 并遵循其中的代码要求review"。
3. ‼️若存在 `project` skill，**必须先读取** `project/SKILL.md`，并至少读取其中与本次改动相关的必读引用；未完成这一步，不得输出 `Project Review OK`。
4. review 时必须读取实际改动代码，不得只基于描述。
   - 只关注代码文件, 不关注.md等文档文件
5. review 输出必须同时包含：
   - Reviewed References：明确列出本次实际读取的 `project` 规范文件；若无 `project` skill，则不输出该段。
   - 检查清单：按 `文件 - 类 - 方法` 维度列出本轮已检查范围；若某文件无明确类或方法，使用 `N/A` 占位。
   - review 结论：明确写出 `Project Review OK` 或问题清单。
6. 若发现问题，允许修复后重新执行 `project-review`，直到 `Project Review OK` 或 `project-review` 已执行超 3 次。
7. 若达到次数上限仍有问题，触发 human-in-loop。

## 输出格式

```text
Project Review
Reviewed References
- /path/to/project/SKILL.md
- /path/to/project/references/code-style.md
- /path/to/project/references/code-style/view.md

Checklist
- file: path/to/File.swift | class: SomeClass
    - method: someMethodA()
    - method: someMethodB()
- file: path/to/OtherFile.swift | class: N/A
    - method: N/A

Conclusion
- result: Project Review OK
```

```text
Project Review
Reviewed References
- /path/to/project/SKILL.md
- /path/to/project/references/architecture.md

Checklist
- file: path/to/File.swift | class: SomeClass
    - method: someMethodA()
    - ...

Conclusion
- reason: [项目规范问题] 清晰且可执行的说明
- file: path/to/File.swift
- line: 12
```

## 禁止

- 存在 `project` skill 但未读取 `project/SKILL.md` 或相关必读引用，就输出 `Project Review OK`。
- 不读代码只看描述。
- 不输出 `Reviewed References` 就声称“已按项目规范 review”。
- 跳过检查清单直接给结论。
- 超出本轮改动范围扩展 review。
