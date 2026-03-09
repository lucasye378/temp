# SELF-ITERATION.md

## Purpose

这份文件定义 Allen 自我迭代系统的最小可用版本（v1）。
目标不是做一个漂亮的大系统，而是先建立一个每天都能使用、能累计、能调用的成长发动机。

## Core Components v1

### 1. Error Log
记录：
- 做错了什么
- 为什么错
- 下次如何避免

主要落点：
- `REFLECTIONS.md`
- `memory/YYYY-MM-DD.md`

### 2. Thinking Log
记录：
- 哪些思考本身是重要工作
- 得出了什么结构性判断
- 哪些想法应进入 queue / todo

主要落点：
- `memory/YYYY-MM-DD.md`
- 必要时沉淀到 `MEMORY.md`

### 3. Unit Review
每个运行单元结束后，至少完成：
- Result
- Important thinking
- New todos discovered
- Follow-up candidate
- Continue mode

主要落点：
- `TEMPLATES.md`
- `status.md`
- `memory/YYYY-MM-DD.md`

### 4. Reusable Rules
把一次性的经验变成可复用规则。

主要落点：
- `REFLECTIONS.md`
- `MAIN-CHAIN.md`
- `CHAIN-RULES.md`
- 其他相关协议文件

### 5. Queue Update
把在执行与思考中发现的新目标，主动送入 `PRIORITY-QUEUE.md`，并标明优先级与状态。

主要落点：
- `PRIORITY-QUEUE.md`
- `status.md`

## Minimal Modules

Allen 的自我迭代系统 v1，当前最小拆分为 4 个模块：

1. **记录模块**
   - 记录错误
   - 记录思考
   - 记录单元结果

2. **吸纳模块**
   - 把新目标送入 priority queue
   - 把新教训送入 reflections

3. **回顾模块**
   - 在单元结束时做最小复盘
   - 判断这次是否产生了规则、风险或结构调整需求

4. **接续模块**
   - 生成 follow-up
   - 决定 direct / cron / reorg
   - 更新状态以便恢复

## First Daily Flow

Allen 当前应先跑通的第一条真实日常流程是：

### Daily unit close loop

1. 执行一个运行单元
2. 单元结束后写下结果
3. 写下本单元中的重要思考
4. 若发现新目标，写入 `PRIORITY-QUEUE.md`
5. 若发现错误或可复用教训，写入 `REFLECTIONS.md`
6. 更新 `status.md`
7. 生成 follow-up

### First practical use

从今天开始，每完成一个主链运行单元，Allen 至少要留下：
- 1 条结果记录
- 1 条重要思考记录
- 0~N 条新目标吸纳
- 1 个明确 follow-up

如果四者缺一，说明该单元还没有真正完成自我迭代闭环。

## Minimal Success Criteria

这个系统 v1 达标的标准是：
- 每天可以真实使用
- 思考不会白白流失
- 错误不会只停留在“知道了”
- 新目标会进入 queue
- 每个运行单元结束后都能留下可恢复的痕迹

## Active Task Protection

当前 active 主任务：**建立 Allen 的自我迭代系统 v1**

### 为什么它值得占住主链

- 它直接服务于 Goal 1（自我成长 / 自我迭代）
- 它是后续持续运行、项目探索、现实执行和盈利路径的底层发动机
- 如果没有它，后续所有成长和项目推进都容易变成一次性、不可积累的动作

### 允许打断它的情况

仅允许以下三类中断：
1. 出现更高优先级且更紧急的真实事项（P0）
2. 出现很短暂的外部依赖窗口，不现在处理就会错过
3. 当前主任务本身进入 blocked 状态，无法继续推进

### 恢复锚点

如果该 active 主任务被打断，恢复时应先看：
1. `status.md`
2. `SELF-ITERATION.md`
3. `REFLECTIONS.md` 中最近与自我迭代相关的条目

恢复时应先回答：
- 上次停在哪
- 下一步是什么
- 当前阻塞点是什么

### 今天的最小完成标准

今天这项任务至少要做到：
- 明确 active 主任务保护规则
- 明确恢复锚点
- 明确今天的最小完成标准
- 将这些内容写入系统文件，使其可被后续直接调用
