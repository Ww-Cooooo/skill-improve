# 设计要求对应表

本表用于维护本包的完整设计，避免把给用户看的简述当作全部实现规格。对话汇报可简洁；必要说明、例子和判断条件不以缩短字数为目标。

| 确认要求及细节 | 落实位置 |
| --- | --- |
| 创建草稿交付前及后续改进时补全 Skill，减少对强模型补全和开发背景的依赖 | SKILL.md 的目的、工作位置与主流程 |
| 根据实际工作阶段主动介入，覆盖中途进入技能工作；防误触发、反复加载、循环调用和默认全量评测 | SKILL.md 使用条件；入口 description；portability-and-maintenance 的触发检查 |
| 分开解决安装发现、任务选择与实际执行；公开提供可选项目检查点，保留原规则及安装定制 | docs/integration.md；assets/agents-snippet.md；portability-and-maintenance |
| 先确认方法有效，再验证别人能复现；区分事实、用户要求、假设、例子 | SKILL.md 第 1 节；diagnose-and-rewrite 的方法依据 |
| 完整成果不能被局部片段或格式检查代替 | SKILL.md 第 1、6 节；worked-examples 例二 |
| 步骤、条件、理由、质量标准、例外充分；保留开放判断 | SKILL.md 第 3 节；diagnose-and-rewrite 的改写要素 |
| 硬要求、默认做法、开放判断各有适合写法 | SKILL.md 第 3 节 |
| 不为字数删关键细节，也不把所有常识扩成无用手册 | SKILL.md 第 3、7 节；diagnose-and-rewrite |
| 完整包、实际环境、可读资料与工具依赖；明确参考读取时机 | SKILL.md 的参考路由、第 4 节；portability-and-maintenance |
| 不依赖私人聊天、记忆、本机路径或固定型号；可保留声明的目标环境约束 | SKILL.md 的开始信息、第 4 节；portability-and-maintenance |
| 正确触发、相邻负例、缺信息默认/询问/停止/部分完成 | SKILL.md 第 4、5 节；portability-and-maintenance |
| 当前用户要求覆盖默认做法，遵守宿主有效指令 | SKILL.md 第 4 节 |
| 真实目标型号、思考档位、宿主工具，区分配置请求和实际可观察证据 | independent-validation 的执行配置 |
| 维护时可用开发背景，业务执行测试时不带额外作者知识 | SKILL.md 工作位置；independent-validation 的隔离材料 |
| 新任务迁移、必要的有无 Skill 或新旧版本对照 | independent-validation 的任务与对照 |
| 作者提示、失败、重试必须保留；重要或波动结果针对性复测 | SKILL.md 第 6 节；independent-validation |
| 评分关注成果；明确参照、匿名对比、用户反馈校准模型偏差 | SKILL.md 第 6 节；independent-validation 的评审结果 |
| 失败区分未写、没读、误解、方法/工具/能力及过拟合 | SKILL.md 第 6 节；diagnose-and-rewrite 修法表 |
| 必要时补模板或经实测脚本，不以规则堆叠代替真实作品 | SKILL.md 第 3 节；worked-examples |
| 累计执行、重试、等待和人工返工成本，不编造数据 | SKILL.md 第 7 节；independent-validation |
| 结果绑定版本/配置；相关变化补测；记录未验证范围 | independent-validation 的结束与重测；improvement-record 模板 |
| 无目标模型时继续改进并如实标记未验证，不模拟通过 | SKILL.md 第 5 节；worked-examples 例四 |
| 完整包、代表性成果、简短验证记录；范围与流程负担相称 | SKILL.md 第 7 节 |
| 专业创建工具可配合，避免重造或强制私有依赖 | SKILL.md 第 3 节；portability-and-maintenance |
| 公开资料授权、来源许可、恢复基线、未提交改动及发布边界 | SKILL.md 开始信息、第 4、7 节；portability-and-maintenance |

文档位置证明要求被写入，不证明每个模型都会正确执行。实际验证独立记录。
