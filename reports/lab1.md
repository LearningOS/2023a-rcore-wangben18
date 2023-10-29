# 功能总结
为保存 task info 所需信息，TaskControlBlock 新增字段：
- task_start_time（第一次调度开始时间）
- task_syscall_times（系统调用次数记录）

在 TaskManager 方法中为 task_start_time 赋值，记录调度开始时间
- run_first_task（初始运行任务，直接赋值）
- run_next_task（调度时运行任务，先判断为 0 再赋值）

task mod 中新增 log_syscall 函数记录当前 task syscall 信息，然后在 syscall 分发函数中调用 log_syscall

task mod 中新增函数 get_current_task_control_block 暴露当前 task 的 TaskControlBlock，随后在 sys_task_info 函数中调用 get_current_task_control_block 并构造 TaskInfo




# 荣誉准则
1. 在完成本次实验的过程（含此前学习的过程）中，我曾分别与 以下各位 就（与本次实验相关的）以下方面做过交流，还在代码中对应的位置以注释形式记录了具体的交流对象及内容：

无

2. 此外，我也参考了 以下资料 ，还在代码中对应的位置以注释形式记录了具体的参考来源及内容：

无

3. 我独立完成了本次实验除以上方面之外的所有工作，包括代码与文档。 我清楚地知道，从以上方面获得的信息在一定程度上降低了实验难度，可能会影响起评分。

4. 我从未使用过他人的代码，不管是原封不动地复制，还是经过了某些等价转换。 我未曾也不会向他人（含此后各届同学）复制或公开我的实验代码，我有义务妥善保管好它们。 我提交至本实验的评测系统的代码，均无意于破坏或妨碍任何计算机系统的正常运转。 我清楚地知道，以上情况均为本课程纪律所禁止，若违反，对应的实验成绩将按“-100”分计。