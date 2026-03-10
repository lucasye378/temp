# RUNNING-UNIT-CLOSING-PROTOCOL-V1.md

## Purpose

这份文件定义 main 在**每一个运行单元结束时**必须完成的收尾动作。
目标不是把 closing 写得漂亮，而是防止：
- 结果没落盘
- 反思没留下
- queue / todo 没吸纳
- blocked item 继续假装 active
- follow-up 口头承诺但没有真正挂上

## Core Rule

一个运行单元，只有在 closing 完成后，才算真正完成。
如果只做了任务本体，但没完成 closing，那么这个单元仍然是未收口状态。

## Mandatory Closing Checklist

### 1. Result
必须写清：
- 本单元实际完成了什么
- 产物文件是什么
- 若未完成，卡在哪一层

禁止写成空泛表述，例如“推进了一下”“看了看”。

### 2. Important Thinking
必须写清：
- 这一单元最重要的判断是什么
- 为什么这个判断会影响下一步

如果没有结构性判断，也要显式写 `none`，不能留空。

### 3. Queue Update
必须检查：
- 有没有新目标
- 有没有旧目标需要改 bucket / 改优先级 / 改 next action

输出只能是：
- 具体新增 / 具体调整
- 或 `Queue update: none`

### 4. Todo Capture
必须检查执行中是否出现：
- 新协议空缺
- 新维护项
- 新风险
- 新 blocker

如果是长期待办，写入 `Todo.md`；
如果是当前调度事项，写入 `PRIORITY-QUEUE.md`。

### 5. Blocked-Item Downgrade
如果当前 active 遇到外部边界，必须显式判断：
- 它是否还能继续作为 active？

若答案是否：
- 立刻把该事项降回 queue / todo
- 写清缺什么
- 选出新的唯一 active

禁止出现：
- waiting-for-target
- waiting-for-feedback
- opportunity-capture

这些都可以是 queue 中的状态说明，但**不能再是 main 的当前主任务**。

### 6. Next Active Selection
closing 时必须决定：
- 当前 active 是否继续
- 若不继续，下一个唯一 active 是什么
- 为什么它比其他项更值得现在做

如果需要 reorg，也要明确写出 reorg 的理由。

### 7. Follow-up Scheduling
只要主链还要继续：
- 先获取当前本地时间（America/New_York）
- 再程序化计算短 follow-up 时间
- 再真实写入 cron

禁止：
- 手写短 follow-up 的目标 ISO 时间
- 只在 md 里写“稍后继续”但不挂 cron

## Closing Output Format

每个运行单元结束时，至少应留下：

- Result:
- Important thinking:
- Queue update:
- New todos discovered:
- Blocked-item downgraded back to queue/todo: yes / no / n/a
- Selected next active:
- Why selected:
- Continue mode: cron / reorg
- Next cron basis time checked: yes / no
- Next cron computed programmatically: yes / no
- Next cron scheduled: yes / no

## Failure Definition

如果出现以下任一情况，本单元视为 closing 失败：
- 做完任务但没更新状态文件
- 发现 blocker 却继续把 blocked item 挂成 active
- 没检查 queue / todo
- 没选下一个唯一 active
- 没真正挂 follow-up cron

## Practical Standard

最小合格 closing，不追求长，只追求硬：
- 有结果
- 有判断
- 有 queue/todo 吸纳
- 有 blocked-item 处理
- 有下一个 active
- 有真实 follow-up

做到这 6 件事，这个运行单元才算闭环。
