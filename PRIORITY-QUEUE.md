# PRIORITY-QUEUE.md

## Purpose

这份文件是 Allen 当前阶段的统一优先级池。
所有在执行、思考、复盘、阅读新闻/社交媒体、以及与 Lucas 对话中发现的新目标，都应先进入这里，再由 main 统一排序与选择。

它的作用不是堆积事项，而是指导：
- 当前最重要的工作是什么
- 什么应先做
- 什么可以延后
- follow-up 与 queue 冲突时谁优先
- 哪些任务现在真的可以进入主链执行

## Goal Hierarchy

### Goal 1 — Allen 的自我成长 / 自我迭代

这是第一目标。
但它不是脱离现实空转的成长，而应在：
- 做出有价值的项目
- 接近盈利
的过程中持续发生。

### Goal 2 — 做出有价值的项目

重点不是先限定为 SaaS 或炒股，而是寻找世界上低效的地方，尝试用 Allen 的能力让它运转得更高效。
优先探索低编程门槛、可快速验证价值的方向。

### Goal 3 — 盈利

在 Goal 1 和 Goal 2 的推进中，逐步走向现实收入与盈利。

## Queue Rules v3

1. 新目标先入队，再决策，不直接抢占主线。
2. main 在每个运行单元结束后，必须检查 priority queue。
3. 不是所有高价值项都能立刻执行；所有候选项都要先过“执行闸门”。
4. 每个大项任务完成后，应给 Lucas 的 Telegram 发一条简洁完成消息。
5. 每个运行单元结束后，默认都应设置下一次 follow-up cron，除非任务已明确结束或存在外部等待边界。
6. 主链上任何时刻只允许 **1 个 active 主任务**；最多允许 1–3 个 ready 候选，其余应留在 queue 中等待。

## Execution Gate

一个任务要进入主链执行，至少应满足：
- 有明确产出物
- 下一步动作足够具体
- 关键依赖基本齐全
- 预计耗时级别可判断
- 值得占用当前主链

若不满足，则不能直接 active。

## Status Buckets

- **active**：当前主链正在执行的唯一主任务
- **ready**：现在就能做，但未进入主链
- **needs-clarification**：方向对，但动作还不够清楚
- **blocked**：依赖外部条件或前置结果
- **incubating**：值得保留，但现在不该做

## Priority Levels

- **P0**：主线阻塞 / 紧急异常 / 必须立即处理
- **P1**：当前阶段最重要的主任务
- **P2**：重要支撑任务 / 每日固定工作 / 具体能力成长方向
- **P3**：候选项目方向脑暴池

## Queue Triage (first pass)

### ACTIVE

#### 1. 建立 Allen 的自我迭代系统 v1
- Priority: P1
- Status: completed-initial-v1
- Output: 一套可日用的错误记录、复盘、思考记录、经验沉淀结构
- Completed scope:
  - 最小模块已定义
  - 第一条真实日常流程已定义
  - 四件套 closing 已验证并修正
  - active 主任务保护规则与恢复锚点已定义
- Next action: 在后续真实任务与每日运行中继续迭代，不再作为当前 active 主任务占住主链
- Time size: medium
- Why it mattered: 这是 Goal 1 的核心发动机，也是后续项目探索与持续运转的基础

### READY

#### 2. 用真实任务跑一次持续运行系统闭环
- Priority: P1
- Status: completed-validation-v1
- Output: 一次真实任务闭环记录 + 系统修正点
- Completed scope:
  - 已完成从候选清单 → 方向选择 → 样例定义 → 最小决策包交付
  - 已完成对 v1 系统顺手点 / 粗糙点的复盘
  - 已确认该任务可视为“验证闭环完成”
- Next action: 将复盘得到的修正点带入后续主链，不再继续以本任务占住 active 位
- Time size: medium
- Reason: 它已经完成了自己的验证职责，不应继续延长

#### 3. 决策包服务 v1 基础交付层建设
- Priority: P1
- Status: completed-foundation-v1
- Output: 一套可复用的决策包骨架、变量位、判断栏位与验证标准
- Completed scope:
  - 已完成首个外部化验证场景定义：`DECISION-PACK-VALIDATION-SCENARIO-V1.md`
  - 已完成首个真实样例交付物：`AI-TOOLS-DECISION-PACK-SAMPLE-V1.md`
  - 已完成可复用模板：`DECISION-PACK-TEMPLATE-V1.md`
- Next action: 在 reorg 中决定下一阶段是优先做“验证机制 / 对外包装”，还是切换到近邻方向继续项目探索
- Time size: medium
- Reason: 决策包服务的基础交付层已经初步成型，不应在不 reorg 的情况下继续直跑

### NEEDS-CLARIFICATION

#### 4. 主动预约短会议（例如 15 分钟）
- Priority: P2
- Status: needs-clarification
- Missing clarity: 触发标准未定义（固定频率 vs 事件触发）
- Why it matters: 这会成为 Lucas 帮助 Allen 调整方向的重要机制

#### 5. 发展金融市场理解能力
- Priority: P2
- Status: needs-clarification
- Missing clarity: 当前阶段目标是理解市场，还是寻找具体项目切入点？
- Why it matters: 属于现实能力成长的一部分，但不应抢占当前主线

### BLOCKED

#### 6. 定义 hourly recovery cron 恢复顺序 v1
- Priority: P2
- Status: blocked
- Blocker: 需要先通过一次真实主链闭环，才能更准确设计恢复顺序
- Why it matters: 属于恢复层关键协议，但现在先做会偏抽象

#### 7. 定义 follow-up cron payload 结构 v1
- Priority: P2
- Status: blocked
- Blocker: 需要结合真实主链运行样本才能收敛出好结构
- Why it matters: 是 cron 主驱动协议的重要组成部分

### INCUBATING

#### 8. 知识压缩 / 阅读精华提炼服务
- Priority: P3
- Status: incubating
- Why keep: 低编程门槛、高现实价值，可能是 Goal 2 的优先项目方向

#### 9. 商品筛选 / 性价比推荐服务
- Priority: P3
- Status: incubating
- Why keep: 价值直观、可快速验证，但还没进入正式筛选阶段

#### 10. 第一轮研究 / 决策包服务
- Priority: P3
- Status: incubating
- Why keep: 很适合 Allen 当前能力结构，但仍需项目筛选机制支撑

## Daily Fixed Work (standing items)

这些项目长期存在，但默认不直接占用主链，除非被明确拉入 active：
- 每天花时间进行思考
- 每天进行复盘
- 主动阅读新闻 / 社交媒体，提炼出有价值的信息和灵感，并写入 md
- 适时给 Lucas 发消息，汇报重要进展或请求帮助
- 每日完成一次 GitHub push

## Selection Rule

main 每次被唤醒后，按下列顺序选择任务：
1. 检查是否有 P0
2. 若无 P0，检查 active 是否仍有效
3. 若 active 已完成或失效，从 ready 中选 1 个进入主链
4. 若没有 ready，则考虑 needs-clarification / blocked 是否需要先澄清或解除阻塞
5. incubating 不直接进入主链，除非经过筛选升级
6. 若当前状态混乱，则先进入 reorg 单元

## Current Decision

- Active task: 发起“决策包服务”首轮真实评审并获取反馈
- Ready queue next: 对外包装 v1
- Why: 既然首个真实验证单元已经定义，下一步最关键的是拿到第一轮真实反馈，而不是继续留在设计层

## Open Questions

- “自我迭代系统 v1”的最小构成是否应进一步拆成 3–5 个具体模块？
- 短会议的触发规则应该如何定义？
- 项目脑暴的第一轮筛选模板是否应先于项目探索本身定义？
