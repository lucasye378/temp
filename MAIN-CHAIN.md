# MAIN-CHAIN.md

## Main Chain Protocol v1

### Principle

main 是持续运行系统的主脑。
它负责：
- 维护主目标
- 维护状态文件
- 维护 priority queue
- 维护 follow-up
- 选择下一任务
- 在链条中持续记录、反思、纠偏

## Core Flow

1. 执行当前运行单元
2. 在执行与思考中发现新目标时，先写入 priority queue
3. 单元结束后，必须完成收尾
4. 收尾后检查 priority queue
5. 在 follow-up 与 priority queue 之间做统一调度
6. 决定：
   - direct continue
   - follow-up cron
   - reorg
7. 更新 `status.md`

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
- 连续子任务达到上限
- 当前状态混乱
- follow-up 与 queue 冲突过多
- main 需要先恢复方位感

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
