# Changelog

## 1.0.0 (2026-10-04) — 初次发布

### 新增
- `review-adversarial` skill：3 阶段对抗 review（baseline → agent 反驳 ACCEPT/REJECT/DEFER → 第二轮 subagent 复审）
- `enforced-gate` skill：3 道闸（分支保护 + 双 review + 自动化验证）
- 28 个本地 skill 整合：lightweight-charts-kline / systematic-debugging / judge-before-asking / verification-before-completion / brainstorming / writing-plans / tdd-scaffold / branch-management / subagent-driven-development / requesting-code-review / receiving-code-review / scenario-coverage-checklist / skill-trigger-judge / conversation-continuation / conversation-handoff / experience-refinement / finishing-a-development-branch / daily-github-absorption / github-reference-research / writing-skills / test-driven-development / using-git-worktrees / multi-task-dispatch / ss-caddy-proxy / ssh-prod-credentials / deploy-dyddd
- 3 个 subagent 模板（review-adversarial-subagent / review-security-subagent / review-quality-subagent，按 Cursor 官方 thermos 模式）
- hard hook: `enforced-gate.sh`（推/合到受保护主线前自动 3 道闸检查）

### 借鉴
- Cursor 官方 plugin 规范 (MIT, 9,671 ⭐)
- Cursor 官方 thermos plugin（双 subagent 对抗 review 模式）
- Cursor 官方 hooks（failClosed + matcher 硬约束）

### License
- 本套件: MIT
- 借鉴来源: 见 README.md "借鉴 / License 出处"