# PRIORITY-QUEUE.md

## Purpose

这份文件是主链条的统一优先级池。
所有运行单元在执行和思考中发现的新目标，不应直接各自决定命运，而应先进入这里。
然后由 main 统一整理、排序，并决定：
- 继续当前 follow-up
- 还是切换到更高优先级任务

## Queue Rules v1

1. 新目标先入队，再决策，不直接抢占主线。
2. 当前运行单元结束后，main 必须检查 priority queue。
3. 任务选择优先级：
   - P0: 主线阻塞 / 紧急异常 / 明显更高优先级事项
   - P1: 当前主线直接相关的关键任务
   - P2: 重要但不阻塞主线的建设任务
   - P3: 一般优化 / 未来任务 / 可延后事项
4. 如果 follow-up 与 queue 冲突：
   - 若 queue 中出现更高优先级任务，则 queue 优先
   - 否则 follow-up 优先
5. 若连续子任务达到 10 个，强制进入 reorg，不再直接续跑。

## Current Queue

### P1
- [ ] 定义 main 主链条协议 v1
- [ ] 定义运行单元收尾协议 v1
- [ ] 定义 priority queue 与任务选择规则 v1

### P2
- [ ] 定义 hourly recovery cron 恢复顺序 v1
- [ ] 定义 follow-up cron payload 结构 v1
- [ ] 定义链条计数器更新规则 v1

### P3
- [ ] 设计 subagent 作为辅助工具的接入边界
- [ ] 设计更长期的 Agent 组织结构

## Selection Rule

每次 main 被唤醒后，选择任务顺序如下：
1. 检查是否有 P0
2. 若无 P0，比较当前 follow-up 与 P1 队列
3. 若当前 follow-up 仍是最合理主任务，则继续 follow-up
4. 否则切换到 queue 中最高优先级任务
5. 若当前状态混乱，则先进入 reorg 单元，而不是盲做任务
