# 2026Projects 科研工作区

从[项目导航](PROJECTS.md)进入研究、论文或代码项目；每个项目的AGENTS说明实际入口，当前状态说明已经得到什么和下一项工作。
科研先充分探索，管理结构负责让资料容易找到、方法按需使用、结果可以追溯。普通任务无需先运行整套审计。

- [科研与管理使用指南](research_harness/README.md)
- [工作区职责](AGENTS.md)与[规范入口](CONVENTIONS.md)
- [逻辑项目清单](projects.json)：项目及仓库角色；PROJECTS.md由它生成。
- [仓库登记](workspace-repos.json)：已有仓库、远端、分支；不记录科研结论。
- [技能部署说明](SKILLS_SYNC.md)：新规则和专业方法的维护、部署与旧入口停用。

Research、Publish、Public、Experimental、LiteratureLibrary分别保存研究、论文生产、发布代码、原型和文献服务。Personal与Archive保留独立隐私和历史边界。

## 已有同步与迁移工具

setup.ps1用于明确的新机器恢复；sync_all.ps1默认Status，Fetch/Pull/Push是不同操作。先阅读实际参数和目标，日常研究不自动调用同步。
audit_workspace.ps1是可选管理检查；其DeepNaming不是所有项目的日常前置要求。inventory_transfer/export_workspace/verify_transfer用于明确的可信介质转移任务，不等于云备份。
旧restore_codex_skills.ps1仅保留显式Legacy恢复；新科研能力从research_harness维护源部署，不整库恢复旧技能。

子项目各有独立Git根，不从workspace-meta递归暂存项目内容。详细同步/转移历史说明仍在SYNC_GUIDE.md和TRANSFER_GUIDE.md；其中旧科研入口不覆盖现行AGENTS和SKILLS_SYNC。
