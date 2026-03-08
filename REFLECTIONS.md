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
  - 但预期的 Telegram 动作没有发生。
- What I learned from docs:
  - Main-session cron 的机制不是“到点直接执行一轮完整 agent 任务”，而是**enqueue a system event, then run on the next heartbeat**。
  - 也就是说，`sessionTarget: "main"` + `payload.kind: "systemEvent"` 更适合提醒/事件注入，而不适合把“精确外发动作”本身托付给这条路径。
  - 若目标是精确、可验证地在指定时间完成一个动作，更稳的方式是使用 **isolated cron**，并用 delivery/announce 或让独立 run 直接完成任务。
- Rule:
  - 不要把“main cron systemEvent”当成精确动作执行器；它本质上是**向 main 注入事件**。
  - 对于“某时刻必须实际完成一次动作（例如发 Telegram）”这类任务，优先考虑 **isolated cron** 或其它直接可验证的执行路径。
