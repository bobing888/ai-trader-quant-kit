# AI Trader Quant Kit — 公司级 Skill 套件

把 33 个散装 skill 打包成 Cursor 官方 plugin 格式，**直接复用 marketplace / install / version / subagent 机制**。

## 1 分钟安装（用户视角）

```bash
# 假设已经发布到 GitHub
/add-plugin ai-trader-quant-kit

# 或开发模式
.cursor/plugins/ai-trader-quant-kit/.cursor-plugin/plugin.json
```

## 套件内容（v1.0.0）

| 类别 | Skill / Agent | 来源 | 借鉴 |
|------|--------------|------|------|
| **对抗 review** | `review-adversarial` | 本地新增 | Cursor 官方 [thermos](https://github.com/cursor/plugins/tree/main/thermos)（MIT） |
| **强门禁** | `enforced-gate` | 本地新增 | Cursor 官方 hooks + branch-management |
| **预测 baseline** | `predict-baseline` | 本地新增 | freqtrade FreqAI + jesse-ai ML strategy（GPL, 直接搬） |
| **ML 校准** | `ml-calibration` | 本地新增 | qlib + mlfinlab（Apache 2.0, 直接搬） |
| **技术指标** | `lightweight-charts-kline` | 本地已有 | tradingview/lightweight-charts（Apache 2.0） |
| **QA 辅助** | `systematic-debugging` | 本地已有 | 无（内部经验） |
| **少问多干** | `judge-before-asking` | 本地已有 | 无（内部经验） |
| **验证必做** | `verification-before-completion` | 本地已有 | 无（内部经验） |
| **brainstorm** | `brainstorming` | 本地已有 | 无（内部经验） |
| **plan 模板** | `writing-plans` | 本地已有 | 无（内部经验） |
| **TDD 脚手架** | `tdd-scaffold` | 本地已有 | 无（内部经验） |
| **Git 工作流** | `branch-management` | 本地已有 | 无（内部经验） |
| **子 agent 驱动** | `subagent-driven-development` | 本地已有 | 无（内部经验） |
| **PR review 求助** | `requesting-code-review` | 本地已有 | 无（内部经验） |
| **PR review 接收** | `receiving-code-review` | 本地已有 | 无（内部经验） |
| **场景覆盖** | `scenario-coverage-checklist` | 本地已有 | 无（内部经验） |
| **触发判断** | `skill-trigger-judge` | 本地已有 | 无（内部经验） |
| **对话延续** | `conversation-continuation` | 本地已有 | 无（内部经验） |
| **对话交接** | `conversation-handoff` | 本地已有 | 无（内部经验） |
| **经验提炼** | `experience-refinement` | 本地已有 | 无（内部经验） |
| **开发分支收尾** | `finishing-a-development-branch` | 本地已有 | 无（内部经验） |
| **每日 GitHub 吸收** | `daily-github-absorption` | 本地已有 | 无（内部经验，仅手动） |
| **GitHub 调研** | `github-reference-research` | 本地已有 | 无（内部经验） |
| **KV 写 skill** | `writing-skills` | 本地已有 | 无（内部经验） |
| **TDD 全流程** | `test-driven-development` | 本地已有 | 无（内部经验） |
| **用 git worktree** | `using-git-worktrees` | 本地已有 | 无（内部经验） |
| **多任务派单** | `multi-task-dispatch` | 本地已有 | 无（内部经验） |
| **SS caddy 代理** | `ss-caddy-proxy` | 本地已有 | 无（内部经验） |
| **生产 SSH 凭证** | `ssh-prod-credentials` | 本地已有 | 无（内部经验） |
| **部署 dyddd** | `deploy-dyddd` | 本地已有 | 无（内部经验） |

## 目录结构

```
ai-trader-quant-kit/
├── .cursor-plugin/
│   └── plugin.json                 # 本文件 — 套件元数据
├── README.md                       # 用户视角安装说明
├── CHANGELOG.md
├── LICENSE                         # MIT（继承自 Cursor 官方）
├── assets/
│   └── logo.png
├── skills/                         # 直接搬 ~/.cursor/skills/*（保留原 license 头）
│   ├── review-adversarial/SKILL.md
│   ├── enforced-gate/SKILL.md
│   ├── lightweight-charts-kline/SKILL.md
│   ├── ...
│   └── writing-skills/SKILL.md
├── agents/                         # 对抗 review 的 subagent（按 thermos 模式）
│   ├── review-adversarial-subagent.md
│   ├── review-security-subagent.md
│   └── review-quality-subagent.md
└── hooks/
    └── hooks.json                  # enforced-gate hard hook
```

## 关键设计决策（按 AGENTS.md 规则 15：直接搬运最强开源）

| 决策 | 借鉴出处 | 为什么 |
|------|---------|--------|
| **plugin/marketplace 格式** | Cursor 官方 [plugins repo](https://github.com/cursor/plugins) MIT, 9,671 ⭐ | 官方规范，Cursor IDE 原生支持 |
| **3 阶段对抗 review** | Cursor 官方 [thermos plugin](https://github.com/cursor/plugins/tree/main/thermos) MIT | "双 subagent 并行 + 主 agent 整合"是 Cursor 团队的官方模式 |
| **/强门禁 hook** | Cursor 官方 [create-hook](https://cursor.com/docs/hooks) | hooks.json + failClosed + matcher = 硬约束 |
| **轻量打包（无 build）** | Cursor 官方插件 [no build step](https://github.com/cursor/plugins/blob/main/docs/architecture.md) | plugin = 目录 + manifest，不需要 npm pack |

## 版本历史

- **1.0.0** (2026-10-04): 初次发布。包含 review-adversarial + enforced-gate + 28 个本地 skill + 3 个 subagent 模板。

## 借鉴 / License 出处

- Cursor 官方 plugin 规范: [github.com/cursor/plugins](https://github.com/cursor/plugins) (MIT)
- Cursor 官方 thermos (双 subagent 对抗 review): [github.com/cursor/plugins/tree/main/thermos](https://github.com/cursor/plugins/tree/main/thermos) (MIT)
- Cursor 官方 hooks 文档: [cursor.com/docs/hooks](https://cursor.com/docs/hooks) (官方)
- 33 个本地 skill：内部经验，MIT 继承

## 后续路线（v1.1.0+）

- **v1.1.0**: 加 `predict-baseline` skill（搬 freqtrade FreqAI 的 baseline 跑法）
- **v1.2.0**: 加 `ml-calibration` skill（搬 qlib 的 Labeling + qlib.contrib.model）
- **v1.3.0**: 加 `backtest-engine` skill（搬 jesse-ai 的 ML strategy 框架）
- **v2.0.0**: 内部 marketplace（`~/.cursor/marketplace.json` + GitHub repo 索引）