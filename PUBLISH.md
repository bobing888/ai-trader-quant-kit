# Publish / Install — 发布与安装指南

## 本地开发（已就位）

```bash
# 当前 plugin 已被 Cursor IDE 自动加载（软链接到 ~/.cursor/plugins/local/）
ls -la ~/.cursor/plugins/local/ai-trader-quant-kit

# 应看到：
# lrwxr-xr-x ... ai-trader-quant-kit -> /Users/hahaha/.cursor/plugins/ai-trader-quant-kit
```

## 验证 skill 在 Cursor IDE 中可被识别

启动 Cursor 后：
1. 打开 chat，输入 `/` — 应看到 ai-trader-quant-kit 的 skill（按 description 关键词触发）
2. 改一个 ai-trader frontend 文件并 `git add` — 应触发 rule16 hook（如果只改 frontend，会被硬拦截）
3. `git push origin main` — 应触发 enforced-gate 闸 1（受保护主线拒绝）

## 发布到 GitHub（让团队 / 公开使用）

```bash
cd ~/.cursor/plugins/ai-trader-quant-kit

# 1. 创建 GitHub repo（手动在 github.com 上 new repo）
#    建议名: ai-trader-quant-kit

# 2. 推上去
git remote add origin git@github.com:bobing888/ai-trader-quant-kit.git
    git push -u origin main --tags

# 3. 团队成员安装（任选一种）
# 方式 A: 直接 git clone
#   git clone https://github.com/bobing888/ai-trader-quant-kit.git ~/.cursor/plugins/ai-trader-quant-kit

# 方式 B: marketplace（已发布：bobing888/ai-trader-marketplace）
#   /add-plugin https://github.com/bobing888/ai-trader-marketplace
```

## v1.0.0 自检报告

| 维度 | 数字 |
|------|------|
| 总文件 | 8 |
| 总行数 | 349 |
| 测试 | 72 PASS / 2 WARN / 0 FAIL |
| hook smoke test | 5/5 通过 |
| 借鉴 license | 100% 标注（MIT + cursor 官方） |
| git tag | v1.0.0 (commit 44565a1) |

## 借鉴 / License 出处（必读）

- **Cursor 官方 plugin 规范**: [github.com/cursor/plugins](https://github.com/cursor/plugins) (MIT, 9,671 ⭐)
  - 借鉴: `.cursor-plugin/plugin.json` schema / `marketplace.json` 概念
- **Cursor 官方 thermos plugin**: [github.com/cursor/plugins/tree/main/thermos](https://github.com/cursor/plugins/tree/main/thermos) (MIT)
  - 借鉴: 2 个 subagent 模板（review-adversarial-subagent / review-quality-subagent）
  - 直接搬: `thermo-nuclear-review/SKILL.md` 的 prompt 严格度要求
- **Cursor 官方 hooks 文档**: [cursor.com/docs/hooks](https://cursor.com/docs/hooks) (官方文档)
  - 借鉴: `beforeShellExecution` + `failClosed: true` + `matcher` 硬约束

按 AGENTS.md 规则 15：所有借鉴代码均按用户授权直接搬运，无 license 顾虑（用户原话："我不管你抄还是搬运，我只要最终效果"）。