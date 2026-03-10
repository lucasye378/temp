# TODO-CAPTURE-RULES-V1.md

## Purpose

这份文件定义 Allen 在执行、思考、复盘、reorg、recovery 时，**哪些东西必须被写进 Todo / Priority Queue**。

目标是减少一种常见损失：
- 当下看到了问题
- 脑中也知道它重要
- 但因为没有立即入池
- 下一轮就丢了

## Core Principle

**发现 ≠ 已吸纳。**
只有写进 `Todo.md` 或 `PRIORITY-QUEUE.md`，才算真正进入系统。

## Split Rule

### 写入 `Todo.md` 的情况
适合写入 `Todo.md` 的，是：
- 跨运行单元仍然成立的长期待办
- 协议空缺
- 系统维护项
- 未来需要补的一般规则件
- 不一定马上 active，但以后明确要补的东西

典型例子：
- 定义某个协议 v1
- 补某个恢复机制
- 修某个长期执行漏洞

### 写入 `PRIORITY-QUEUE.md` 的情况
适合写入 `PRIORITY-QUEUE.md` 的，是：
- 当前调度层需要比较优先级的事项
- 已经能判断 bucket / priority / next action 的项目
- 需要进入 active / ready / blocked / incubating 管理的项目线

典型例子：
- 某条服务线进入 ready-to-send
- 某个项目方向被降级为 blocked
- 某个 maintenance 事项需要临时抢占 active

### 两边都要写的情况
如果某件事同时满足：
- 是长期结构性空缺
- 又会影响近期调度

那么：
- 在 `Todo.md` 里留下长期待办
- 在 `PRIORITY-QUEUE.md` 里给出当前 bucket / next action

## Mandatory Capture Triggers

出现以下任一情况时，必须吸纳：

### 1. 发现新的协议空缺
例如：
- 主链规则不完整
- closing 模板缺字段
- blocked item 没有明确分流规则

动作：优先写入 `Todo.md`，必要时同步入 queue。

### 2. 发现新的持续性错误模式
例如：
- 总是口头决定但不真正调度
- 总是在等待态里空转
- 总是忘记把 blocker 降回 queue

动作：
- 写入 `REFLECTIONS.md`
- 若需要补结构件，写入 `Todo.md`

### 3. 发现新的可执行项目 / 服务线
例如：
- 新的服务方向
- 新的验证场景
- 新的外发路径

动作：写入 `PRIORITY-QUEUE.md`，并给出 bucket、priority、next action。

### 4. 发现当前 active 被外部边界卡住
动作：
- 不把“等待”写成 active
- 把该事项降回 `PRIORITY-QUEUE.md`
- 写清它缺什么
- 再从 Todo / queue 中选择新 active

### 5. 发现只要不记就会丢的下一步
判断标准：
- 下个运行单元很可能忘
- 不是当前 1–2 分钟内就能做掉
- 对后续选择会有影响

动作：至少写入 `Todo.md` 或 `PRIORITY-QUEUE.md` 其一，不能只留在脑子里。

## Non-Capture Rule

以下内容通常**不必**单独入 Todo：
- 当前单元内 1–2 分钟就能直接做完的小尾巴
- 不会跨单元遗失的纯局部步骤
- 没有持续价值的临时噪音

原则：不要把 Todo 变成流水账。

## Minimum Capture Format

### 写入 Todo 时，至少写：
- Item
- Goal
- Why it matters

### 写入 Priority Queue 时，至少写：
- Item
- Priority
- Status bucket
- Next action
- Reason

## Failure Definition

如果出现以下情况，说明 Todo capture 失败：
- 明明识别出问题，但没有写入任何文件
- 下一轮已经忘记刚才发现的新任务
- blocked item 没降级，反而继续挂成 active
- queue 明显滞后于真实推进结果

## Practical Rule

每个运行单元 closing 时，至少问自己 3 个问题：
1. 我刚刚有没有发现一个未来还会成立的问题？
2. 这个东西是长期待办，还是当前调度项？
3. 我已经把它写进系统了吗？

只要第 1 个问题答案是 yes，而第 3 个问题是 no，这个单元就还没真正收口。
