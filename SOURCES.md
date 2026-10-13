# 来源与证据边界

以下官方资料在 2026-10-13 的开发过程中实际阅读，用于指导结构、测试与证据边界。本包正文和虚构案例为针对本项目编写，没有打包第三方 Skill、模型或运行时。

- [OpenAI：Build skills](https://developers.openai.com/plugins/build/skills)：输入、步骤、输出、依赖与支持资源；入口与详细参考按需组织。
- [OpenAI：Skills activation](https://developers.openai.com/plugins/concepts/skills)：模型先看到名称与描述，再按适用条件读取正文；不能仅靠正文要求一个尚不可见的 Skill 自动触发。主动介入各工作阶段是本包的设计，不是对所有宿主的触发保证。
- [OpenAI：Codex local skills](https://learn.chatgpt.com/docs/build-skills)：项目与用户技能目录、隐式选择和目录拥挤时的描述缩短或省略。安装方式与可见性需要分别核对。
- [OpenAI：AGENTS.md](https://learn.chatgpt.com/docs/agent-configuration/agents-md)：项目规则的加载范围、覆盖和新会话核对；用于本包可选工作流接入。
- [OpenAI：Testing Agent Skills Systematically with Evals](https://developers.openai.com/blog/eval-skills)：先确定成功标准，记录真实运行和产物，分开检查触发与实际行为。
- [OpenAI：Evaluation best practices](https://developers.openai.com/api/docs/guides/evaluation-best-practices)：任务相关评估、新任务验证、模型评审偏差与人工校准。
- [OpenAI：Harness-aware evaluation of plugins](https://developers.openai.com/cookbook/examples/partners/harness_aware_plugin_evals/harness_aware_plugin_evals)：工具、提示和执行环境影响测试结论的可迁移范围。

开发时使用了宿主提供的 skill-creator 初始化与格式检查能力。本项目不携带该工具，不把它的安装位置作为使用条件。运行本包时若有可用的创建工具，可按任务配合。

这些来源支持设计选择，不能替代本包在具体模型与环境中的实际验证。当前验证范围单列在 [验证记录](docs/validation.md) 中。
