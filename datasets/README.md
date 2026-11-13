# 测试数据说明

这些是供学生上手测试的**示例数据，不是标准答案**。可以自行修改节点数、任务数和数据值。**请保证同一实验中不同算法使用相同输入。**

## 任务A

- [`task_a/nodes.csv`](task_a/nodes.csv)：`node_id`, `compute_gops_per_s`（计算能力，GOp/s）。
- [`task_a/tasks.csv`](task_a/tasks.csv)：`task_id`, `workload_gop`（计算量，GOp），任务按文件行序依次分配。
- 示例计算时长：`workload_gop / compute_gops_per_s`（秒）。
- 默认所有任务在时刻0就绪，各节点独立、内部串行、无抢占；每个节点的完成时间为分配到该节点任务的执行时间之和，Makespan为最大节点完成时间。

## 任务B

- [`task_b/nodes.csv`](task_b/nodes.csv)：`node_id`, `compute_gops_per_s`。
- [`task_b/tasks.csv`](task_b/tasks.csv)：`task_id`, `source_node`, `data_mb`, `workload_gop`。
- [`task_b/bandwidth_mbps.csv`](task_b/bandwidth_mbps.csv)：`source_node`, `target_node`, `bandwidth_mbps`。样例给出所有异节点方向的单跳带宽。
- 传输时间（秒）：`data_mb * 8 / bandwidth_mbps`（其中MB按10^6字节、Mbps按10^6 bit/s计算）。
- 计算时间（秒）：`workload_gop / compute_gops_per_s`。
- 任务在其来源节点本地执行时，传输时间=0。不同任务独立评价，基础版本不需要建立计算排队与链路竞争模型。
- 为了观察网络开销的影响，可以固定任务计算量和来源节点，分别测试**较小的数据大小**和**较大的数据大小**；也可使用数据文件中的多组任务。

以上公式仅用于统一基本模型与单位，不规定程序组织方式或最终算法实现。
