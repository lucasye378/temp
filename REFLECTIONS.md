# REFLECTIONS.md

## Reusable Lessons

### 2026-03-08 — C-Test-001

- Situation: Allen 在初始化阶段开始系统性测试自身能力，并进入持续工作系统建设前置阶段。
- What worked:
  - 先测试单项能力，再写入能力日志，这种节奏清晰且可验证。
  - 使用 `CAPABILITIES.md` 记录通过/未通过状态，便于长期追踪。
  - 使用 `Todo.md` 承接未完成问题，有助于把测试暴露的问题转成后续行动。
- What to improve:
  - 还需要把“目标 → 执行 → 结果 → 反思”的闭环进一步模板化。
  - 还需要建立更明确的每日/阶段性回顾机制。
- Rule:
  - 如果一个问题没有被写成目标、结果或反思，它很容易在后续工作中丢失。
  - 对于未完成事项，应优先写入 `Todo.md`，而不是只在对话中提及。

### 2026-03-08 — Cron main-session wake test

- Situation: Allen 尝试创建一个 `sessionTarget: "main"` 的一次性 cron，期望 1 分钟后唤醒 main，并让 main 给 Lucas 的 Telegram 发消息。
- What happened:
  - 任务按计划到时后已不在 cron 列表中，说明 one-shot job 已被调度消费。
  - 但第一次预期的 Telegram 动作没有发生。
- What I learned from docs:
  - Main-session cron 的机制不是“到点直接执行一轮完整 agent 任务”，而是**enqueue a system event, then run on the next heartbeat**。
  - 也就是说，`sessionTarget: "main"` + `payload.kind: "systemEvent"` 的本质是：把 follow-up 带回 main，并通过 heartbeat 语义处理。
- Correction:
  - heartbeat 不能默认直接投递到 Telegram，否则内部链条记录会缺失在当前 webchat 里。
  - 更合理的做法是：heartbeat 目标回到 webchat（`target: "last"`），然后由被唤醒的 main 在当前会话留下可见记录，再执行给 Telegram 发消息这类后续动作。
- Verified outcome:
  - 修正 heartbeat 目标后，Allen 成功验证了这条链：`cron(main)` → `systemEvent` → `wakeMode: now` → main/webchat 被唤醒 → main 执行后续动作 → Telegram 收到消息。
- Rule:
  - `cron(main)` 不应被理解为 isolated worker，而应被理解为 **main 的精确定时唤醒器**。
  - 若主链条要求“所有消息记录都留在 webchat 中”，则 heartbeat 输出应先回到 webchat，再由 main 执行外发动作。
