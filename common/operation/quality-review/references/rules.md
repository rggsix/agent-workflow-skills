# 规则

一句话定位：只检查代码质量，不讨论需求匹配。

## 必须

1. 仅在 spec-review 通过后执行。
2. 读取实际改动代码（diff 或文件），不得只基于描述。
3. 检查维度：结构/文件路径/命名/可维护性/测试/风险点 等代码质量相关。
4. 检查是否有 project 相关 skill
    - 如果有, 输出"我将阅读 project skill 并遵循其中的代码要求review", 然后遵循该 skill 要求进行review 
    - 如果没有, 输出"我已检查当前无project相关skills"
5. 若无问题，输出“Quality OK”。

## 输出格式

```text
Quality Review
- reason: [质量问题] 清晰且可执行的说明
- file: path/to/file
- line: 12
```

## 禁止

- 不讨论需求是否实现（交给 spec-review）。
- 不扩展范围到未改动代码。
