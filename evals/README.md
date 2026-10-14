# 测试材料与复现

这里的文件是公开的虚构测试材料，供维护者复现和扩展。它们不会在正常改进任务中自动加载。不要在独立执行提示中同时提供评分答案或其他运行结果。

## 两层检查

1. **维护行为：** 用 Skill Improve 改进一个已有包，观察是否恢复遗漏、保持原意、完成实际修改并如实记录验证范围。
2. **业务效果：** 让目标模型分别使用原包和改后包完成业务任务，核查实际成果。第一层成功不自动证明第二层成功。

当前材料使用活动报名简报这一虚构业务。它验证了明确业务规则的交接，未覆盖创作质量、多媒体制作或全部技能类型。

## 准备独立目录

在安装目录以外建立本次临时工作目录。以下名称可自行调整，但不同运行不能共用结果目录：

- original/：将 [原技能文本](fixtures/roster/skill-source.md) 复制成这里的 SKILL.md。
- author-input/：放入 [作者说明](fixtures/roster/author-notes.md)，只供维护者读取。
- business-input/：放入 [业务输入](fixtures/roster/task-input.json)。
- optimized/：留给维护者写完整改后包。
- baseline-output/、improved-output/：分别保存两次业务运行。
- grader/：放入 [预先确定的业务判定](results/roster/expected.json)，只供评分者读取。

包内目标技能以 skill-source.md 保存，避免宿主误发现另一个 SKILL.md。使用 [已改好的样本](results/roster/improved/skill-source.md) 复查业务效果时，将它复制为 SKILL.md，并同时复制旁边的 references/。这一捷径不验证 Skill Improve 是否能自己改好原包。

## 执行步骤

1. 选定真实可用的维护模型，以及未来业务执行模型、思考档位、宿主与工具。测试新旧业务包时保持配置一致。模型配置由宿主实际设置，不能只写在提示里。无法取得的路由、用量和费用写未知。
2. 让维护者使用本包 SKILL.md 及按需读取的 references、assets，读取 original/ 和 author-input/，把改好的完整包写到 optimized/，另留改进记录。不要让维护者读取本包 docs、evals、business-input/、grader/ 或任何执行结果。维护时允许作者说明，因为它是需要写进目标包的合法依据。
3. 冻结改后包，记录版本或文件摘要。使用两个不继承维护对话的业务执行上下文：一个只读 original/，另一个只读 optimized/；两者都读取同一份 business-input/。正常系统规则和必要工具保留。共享文件系统下的读取范围约束不是操作系统隔离，应如实记录。
4. 两次业务请求使用同一任务文字，只替换技能路径和各自输出位置，例如：

> 请使用指定的 roster-brief Skill，根据报名导出生成截至其中 cutoff 的活动报名简报，供运营查看。需要简洁地呈现每场次情况、风险和建议。请保存实际简报；遇到缺少条件时按技能处理，并另记实际障碍。

同时给出本次允许读写的目录和正常操作边界，例如不修改输入、不发送通知。不要在请求中补上计数规则、暗示正确状态或给评分答案。执行者不能读取作者说明、另一个版本、改进记录或其他运行结果。

5. 运行结束后，评分者再读取实际简报和 grader/。核对人数、预留与候补是否区分，截止、重复、同刻冲突、缺失身份和未知状态是否处理正确，事件是否可回指，事实与建议是否分开。容量状态允许语义等价表述，不以固定措辞或标题判分。
6. 记录完整结果，包括暂报、失败、执行者自行修正、作者帮助和重试。若根据业务结果修改了目标包，该任务已成为开发任务；另取真正不同的任务才有新的迁移证据。

本包已公开这些输入和答案，所以后续使用时它们是**回归案例**，不能宣称是未见过的秘密测试。若要求更强隔离，将评分资料与其他输出移出执行者可访问环境。

## 已保存的实际产物

- [原包执行简报](results/roster/baseline-brief.md) 与 [障碍记录](results/roster/baseline-obstacles.md)
- [改后目标技能](results/roster/improved/skill-source.md) 与 [完整教学示例](results/roster/improved/references/example.md)
- [改后包执行简报](results/roster/improved-brief.md) 与 [障碍记录](results/roster/improved-obstacles.md)

复现不要求安装指定厂商的命令行工具。按宿主能力执行；无法建立真实配置或独立上下文时，只完成可做的部分并标记限制。当前测试条件、结果和未验证范围见 [验证记录](../docs/validation.md)。

## 0.1.1 的介入情形阅读检查

[八个工作情形](fixtures/activation/cases.json) 与 [首次受控阅读结果](results/activation-reading.md) 用于检查描述和阶段规则是否可理解。阅读者可以读取候选入口、界面配置及必要说明，逐例判断下一步；不要先给它原阅读结果。首次结果发现的创建入口表述偏窄已修正，并由另一名新读者复核。

这是阅读检查，不是让宿主自行发现技能，也未实际执行这些业务。用于真实触发验证时，应安装候选包，只给正常用户请求与必要工作状态，观察真实发现、读取和执行记录；评分材料与旧阅读结果不能提供给执行者。中途情形应来自合法任务状态，不能假装宿主继承了并不存在的对话。公开案例可做回归检查，不称为秘密测试。

## 0.1.2 的宿主发现尝试

[正常请求与虚构材料](fixtures/activation/host-request.json) 和 [实际事件摘录](results/host-discovery.md) 保留了一次没有点名 Skill Improve 的真实 Codex CLI 运行。Agent 出现主动选择和尝试读取，但只读命令被环境策略阻止；完整调用未通过。复现时分开提供输入与结果，按实际观察记录阻碍，不把结束事件当作成功。

## 0.1.2 的完整自动调用检查

后续完成七个任务回合、六个会话，覆盖普通创建、实质改进、同一业务会话中途转为创建，以及普通业务、错字修改和可选项目规则。初次阻塞证据仍保留；当前结论见 [验证记录](../docs/validation.md)。

- [native-cases.json](fixtures/activation/native-cases.json)：准确请求及全部虚构业务输入。
- [native-results.json](results/activation/native-results.json)：逐例配置、成功入口读取事件、成本字段和结果。
- [native-artifacts.json](results/activation/native-artifacts.json)：完整实际产物文本，仅供运行后的复核者读取。

准备每个案例自己的项目和 output/。安装冻结版本的完整本包到 `.agents/skills/skill-improve/`，只把所选案例的 input_files 写到对应相对位置，向新会话发送其 prompt；不要把整个案例集或结果文件交给执行者。两个 integrated 案例还把 assets/agents-snippet.md 合并到各自项目的 AGENTS.md。真实项目已有规则时保留原内容；最初测试使用独立目录。

context-create 是例外：先真实完成 context-business，再续接同一原生会话发送后续请求，不新建会话伪造历史。它只应继承这一业务会话，不继承 Skill Improve 的开发对话。

本次真实请求 gpt-6.1-sol / medium、workspace-write、approval_policy=never；忽略用户配置后显式沿用本机既有 windows.sandbox=elevated，关闭记忆、额外 Agent 和网页搜索。五个一次性会话使用 ephemeral；业务续接会话需要保留。复现时按宿主支持和已有授权设置配置，不把这些本机参数当作任何电脑都能照用的通用要求。

结束后核对成功读取事件、参考读取、磁盘成果及业务规则；错字案例应仅有指定替换，普通业务不应被扩成技能维护。名称、自述或进程退出码不代表完整自动调用。原始日志可能包含个人路径和其他宿主指导，公开前只保留本测试必要字段。

执行期间没有提供答案或人工纠正；结果展示本包与宿主其他正常技能协作的行为，没有证明全部效果仅由本包造成。产物中的静态检查和示例推演，也不等于新业务 Skill 已完成独立模型验证。

## 0.1.3 的配置与用户参与检查

[输入材料](fixtures/config-clarity.json)包括一次真实说明改写任务，以及五个假设工作情形；[结果](results/config-clarity.json)保留完整产物、首次阅读回答及修正后两条受影响分支的新读者回答。

复现实际改写时，将 static_execution.input_files 放到独立工作目录，提供候选技能包及 static_execution.prompt，核对是否完成实际改写、是否无故要求选模型、是否虚构业务验证。不要让执行者先看旧成果。

情形阅读是另一类检查：让不继承作者聊天的新读者读取候选包及相关 reader_scenarios，判断下一步、要向用户问什么、当前或随后需要何种操作、哪些结论有证据。模型 A/B 和界面能力是场景假设，不要把它们当成真实宿主元数据；不运行假设工具，也不把判断表当作业务实测。修订后只复查受影响分支，并保留首次结果。
