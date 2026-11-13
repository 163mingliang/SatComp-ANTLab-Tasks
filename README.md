# SatComp-ANTLab-Tasks

**ANTLab 本科生项目考核任务**

本次考核设置三个方向，请根据兴趣和基础**选择一项**完成。各任务分为基础任务和进阶任务：基础任务必做，进阶任务选做。

| 任务 | 方向 | 任务说明 |
| --- | --- | --- |
| A | 计算任务调度算法设计与仿真 | [Task-A-TaskScheduling](Task-A-TaskScheduling/README.md) |
| B | 算网协同任务处理建模与仿真 | [Task-B-ComputeNetworkModeling](Task-B-ComputeNetworkModeling/README.md) |
| C | FPGA 网络数据处理模块设计与验证 | [Task-C-FPGADataPlane](Task-C-FPGADataPlane/README.md) |

## 考核与提交

- **周期：**5—7天；具体截止时间以群内正式通知为准。
- **选择：**三项任务任选一项；任务C的两个基础方案也任选其一。
- **提交：**Fork本仓库，在自己的仓库中完成所选方向的代码、测试、结果及说明，并推送到GitHub。无需向原仓库提交Pull Request。
- **说明：**请在Fork仓库根目录填写 `SUBMISSION.md`（可以复制 [提交模板](templates/SUBMISSION_TEMPLATE.md)），写明方向、完成内容、运行或仿真方法、测试结果。提交个人Fork仓库链接及收集表所需信息，收集表以群内通知为准。
- **交流：**提交后酌情安排简短交流，介绍实现思路、代码、实验结果及遇到的问题。

第一批考核表现良好的同学可免考，自愿完成新题可作为额外表现参考；第一批尚未通过的同学和新加入的同学均可参加本次考核。

允许参考教材、技术资料、开源代码及使用AI工具辅助学习和开发，但应理解所提交的内容，能够解释核心代码、算法原理和实验结果。重点考察编程与硬件开发能力、独立学习能力、问题分析能力和实验验证能力。

## 目录说明

```text
SatComp-ANTLab-Tasks/
├── README.md
├── Task-A-TaskScheduling/README.md
├── Task-B-ComputeNetworkModeling/README.md
├── Task-C-FPGADataPlane/README.md
├── datasets/
│   ├── README.md
│   ├── task_a/{nodes.csv,tasks.csv}
│   └── task_b/{nodes.csv,tasks.csv,bandwidth_mbps.csv}
├── examples/fpga/{README.md,ipv6_header_example.txt}
├── templates/SUBMISSION_TEMPLATE.md
└── .gitignore
```

提供的样例数据、协议字段说明与测试场景是辅助材料，不构成额外必做要求；可以使用自行设计的数据和接口，但须说明假设与测试方法。
