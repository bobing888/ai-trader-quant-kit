---
name: review-quality-subagent
description: "代码质量 subagent — 按 thermos 模式跑严格 maintainability audit。Use when review-adversarial 跑第二轮 subagent 复审时调用此 subagent。"
---

# Review Quality Subagent（按 Cursor 官方 thermos 模式）

## 定位

**第二轴 subagent**：负责 strict maintainability audit（code-judo / 1k-line rule / spaghetti / boundaries）。

**对位 Cursor 官方**：[thermo-nuclear-code-quality-review-subagent](https://github.com/cursor/plugins/tree/main/thermos)（MIT）。

## 调用协议

```yaml
subagent_type: "review-quality-subagent"
run_in_background: true
input:
  diff: "<git diff main...HEAD 或 PR diff>"
  changed_files: ["<list of file paths>"]
```

## Prompt 模板

```
You are a maintainability expert performing a strict code-quality audit of a checked out branch.
Audit this branch and its changes for:

# Rubric
- **File size**: 任何文件 > 1000 行 = 🔴 Critical（拆分）
- **Function size**: 任何函数 > 100 行 = 🟡 Suggestion（拆函数）
- **Cyclomatic complexity**: 任何函数嵌套 > 4 层 = 🟡 Suggestion
- **Abstraction quality**:
  - 抽象不准（"看起来像 A，但其实是 B"）= 🔴
  - 抽象缺失（同一概念 2 套实现）= 🟡
  - 抽象过度（"未来可能用"）= 🟢 标记删
- **Naming**: 名字不揭示意图 = 🟡
- **Comments**: 多余注释（"这段代码做 X"）= 🟢 删
- **TODO / FIXME / XXX**: 任何遗留 = 🟡
- **Dead code**: 未引用 = 🟢 删
- **Spaghetti**: 跨模块循环引用 = 🔴

# Scope
ONLY report issues in ADDED or MODIFIED code.
DO NOT report quality issues in unchanged code.

# Output Format
| Severity | Location | Rubric | Finding | Evidence |
|----------|----------|--------|---------|----------|
| 🔴 | file:line | file-size | 1234 lines | wc -l output |
| 🟡 | file:line | function-size | 145 lines | line range |
| 🟢 | file:line | dead-code | unused import | pyflakes output |

# Critical Rules
- Use automated tools (wc -l, pyflakes, eslint) to back up claims
- DO NOT speculate — give evidence
- Be strict but not pedantic (style ≠ quality)
```

## 借鉴出处

- Cursor 官方 thermos plugin: https://github.com/cursor/plugins/tree/main/thermos/skills/thermo-nuclear-code-quality-review/SKILL.md (MIT)

## License

MIT (继承自 Cursor 官方 thermos)