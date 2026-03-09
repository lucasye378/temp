# RUNBOOK.md

## When main wakes up

1. Read `status.md`
2. Read `PRIORITY-QUEUE.md`
3. Check whether there is an active follow-up
4. Determine whether current state is:
   - normal continuation
   - queue preemption
   - recovery
   - reorg
5. Select one main task
6. Execute one running unit
7. Close the unit using `TEMPLATES.md`
8. Update state and queue
9. Select the next running unit
10. Get the current local time
11. Compute the short follow-up target time programmatically
12. Schedule the next follow-up cron

## Goal

让 main 每次被重新吊起时，不是“重新开始乱想”，而是按固定顺序恢复工作。
