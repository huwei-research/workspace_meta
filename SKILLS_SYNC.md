# 专业方法的维护与部署

唯一科研维护源是research_harness/skills；用户安装目录只是受控副本。修改方法先改维护源，再按[使用指南](research_harness/README.md)预览和部署。支持资料随技能一起部署。
启用八个科研方法并不禁用文档、PDF、图像、表格、幻灯片或其他用户已选插件。它们继续各司其职。
旧research-orchestrator、math-paper-writer、旧L0/L1及scientific-numerical-experiments已退出本次新系统；原件保留恢复，不能通过旧全库恢复重新启用。
机器路径、启停清单和运行时确认记录在research_harness/.local；系统内置技能、插件缓存和认证不由此维护。
旧restore_codex_skills.ps1只有显式-Legacy才复制旧备份。需要恢复本次管理变更时使用新restore命令及迁移清单，不用Git reset/clean。
桌面升级或新技能未出现时，先核对安装位置、配置和新会话可见列表；不要删缓存、退出登录或猜配置键。
