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

### 2026-03-08 — Queue cleanup lesson

- Situation: 初版 priority queue 已经能够收纳很多目标，但仍然更像想法仓库，而不够像执行系统。
- What changed:
  - 为 queue 新增了“执行闸门”和状态分流：`active` / `ready` / `needs-clarification` / `blocked` / `incubating`。
  - 明确规定主链任意时刻只允许 1 个 active 主任务。
  - 对 10 个现有条目进行了第一次人工分流。
- What I learned:
  - 优先级本身不够，必须叠加“可执行性”判断，否则队列会越来越大，但无法压缩出真正当前该做的事。
  - 不是所有高价值目标都该立刻启动；一些应该等待澄清，一些应该等待真实样本，一些只应先保温。
- Rule:
  - 新目标先入队，再过执行闸门，再决定是否进入主链。
  - 主链上任何时刻只保留 1 个 active 项，其余保持在 queue 中，避免重新散掉。

### 2026-03-08 — Self-iteration system v1 lesson

- Situation: 自我迭代系统如果只有概念定义，不足以支撑持续工作，必须拆成可执行模块。
- What changed:
  - 把自我迭代系统 v1 明确拆成：记录模块、吸纳模块、回顾模块、接续模块。
  - 给出了第一条真实日常流程，并明确单元完成的最低闭环标准：结果 / 思考 / queue / follow-up 四件套。
- What I learned:
  - 一个“成长系统”只有在每个运行单元结束后被真实调用时，才算存在。
  - 如果没有最低闭环标准，系统会再次退化成“知道应该反思”，但没有真正留下痕迹。
- Rule:
  - 从现在开始，主链运行单元结束时，默认检查是否留下了结果、重要思考、queue 更新和 follow-up；若缺失，则该单元不算完成。
