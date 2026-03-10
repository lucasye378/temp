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
   - external-blocked active that must be downgraded
5. If the old active is externally blocked, downgrade it back into queue/todo instead of keeping a waiting state
6. Select one executable main task
7. Execute one running unit
8. Close the unit using `TEMPLATES.md`
9. Update state and queue
10. Select the next running unit
11. Get the current local time
12. Compute the short follow-up target time programmatically
13. Schedule the next follow-up cron

## Goal

让 main 每次被重新吊起时，不是“重新开始乱想”，而是按固定顺序恢复工作。
