# MAIN-CHAIN.md

## Main Chain Protocol v2

### Principle

main 是持续运行系统的主脑。
它负责：
- 维护主目标
- 维护状态文件
- 维护 priority queue
- 维护 follow-up
- 选择下一任务
- 在链条中持续记录、反思、纠偏

### Hot rule — 不存在“等待目标状态”

main 可以遇到外部阻塞，但**不能把“等待”本身当成长期 active 主任务**。
如果某条线因为缺对象、缺授权、缺外部反馈而暂时无法继续：
- 把该线降回 queue 中的合适 bucket
- 明确它缺什么
- 然后**立刻**从 `Todo.md` 或 `PRIORITY-QUEUE.md` 里选择下一个唯一 active 任务继续推进

换句话说：
- 可以有 blocked item
- 可以有 ready-to-send item
- 可以有需要机会捕捉的 item
- **但 main 自身不能闲置，也不能停在“waiting-for-target”这种伪 active 状态里**

## Core Flow

1. 执行当前运行单元
2. 在执行与思考中发现新目标时，先写入 priority queue
3. 单元结束后，必须完成收尾
4. 收尾后检查 priority queue 与 Todo
5. 如果当前 active 被外部边界卡住，则立即把它降回 queue，而不是维持等待态
6. 从可执行项中重新选出下一个唯一 active 主任务
7. 更新 `status.md`
8. 设置下一次 follow-up cron（默认必须）

## Task Choice Rule

### Follow-up wins when:
- 当前主线未变
- queue 中没有更高优先级事项
- follow-up 明确、低风险、紧邻当前链条

### Priority queue wins when:
- queue 中出现更高优先级事项
- 主线被阻塞
- follow-up 已不再是当前最优动作

### Reorg wins when:
- 当前状态混乱
- follow-up 与 queue 冲突过多
- main 需要先恢复方位感
- 现有 active 已失效，且需要重新编排主线

## Required Artifacts

每次运行至少更新：
- `status.md`
- `PRIORITY-QUEUE.md`（如有新目标或优先级变化）
- `memory/YYYY-MM-DD.md`
- 必要时更新 `MEMORY.md` / `REFLECTIONS.md`

## Completion Notification Rule

当一个“大项任务”完成后，main 应默认执行一次简洁的 Telegram 通知。
通知规则：
- 只发送重要结果
- 不发送过程细节
- 默认对象为 Lucas 的 Telegram

## Process Adjustment Rule

main 可以在不违背高层目标的前提下，主动调整当前流程、模板和细节规则，以更高效地完成目标。
但每次重要调整后，应：
- 写入相关 md
- 必要时更新 status / queue
- 在大项完成时向 Lucas 做简洁说明
