# Tasks

- [x] Task 1: 起草 DSH 修复智能体描述文本
  - [x] SubTask 1.1: 按 `dsh.md` 逐条提炼规则：红线（Never touch）、修复落点（Where fixes may land）、流程（Procedure）、修复循环（Repair Is a Loop）、守则（Guard rails）、汇报要求；`/goal` 在无该命令的环境中以显式目标声明替代
  - [x] SubTask 1.2: 组织为结构化中文描述：角色定位、适用场景、职责、红线、修复落点、操作流程、修复循环、汇报格式
  - [x] SubTask 1.3: 控制总长 ≤10000 字符（Unicode 口径，含空白与换行），路径与文件名保留英文原文
- [x] Task 2: 一致性校验
  - [x] SubTask 2.1: 逐条比对描述与 `dsh.md`，产出条目级映射清单（`dsh.md` 条目 → 描述条目，bullet/句子级粒度），确认无空项、无弱化、无矛盾
  - [x] SubTask 2.2: 按 Unicode 字符口径（含空白与换行）校验字符数 ≤10000
- [x] Task 3: 交付
  - [x] SubTask 3.1: 在最终回复中以代码框提供完整描述
  - [x] SubTask 3.2: 附"复制到 设置 > 智能体 > 创建智能体"的使用引导
  - [x] SubTask 3.3: 确认未改动 `/workspace` 仓库其他文件

# Task Dependencies

- Task 2 depends on Task 1
- Task 3 depends on Task 2
