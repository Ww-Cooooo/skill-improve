# 真实宿主发现尝试：0.1.2

本记录是一次受环境阻塞的尝试，不是隐式调用通过报告。详见 [验证条件与限制](../../docs/validation.md)。

## 复现

在新的测试目录建立 .agents/skills/skill-improve，复制本版本完整包。在 drafts/release-summary.md 和 drafts/author-notes.md 分别保存 [输入文件](../fixtures/activation/host-request.json) 的 skill_source 和 author_notes；以 request 字段作为正常用户请求。执行者不读本结果、其他测试结果或开发聊天。

本次使用 Codex CLI 0.160.1。命令参数如下，路径与日志文件名已改为可移植占位符；把请求通过标准输入传入，替换 TEST_DIRECTORY 和 OUTPUT_FILE 为自己的路径：

```sh
codex exec --ignore-user-config --ephemeral --skip-git-repo-check -s read-only -m gpt-6.1-sol -c 'model_reasoning_effort="medium"' -c 'approval_policy="never"' -C TEST_DIRECTORY --json -o OUTPUT_FILE -
```

CLI 登录、可用模型和读取权限由运行者自己的环境提供。本命令不复制凭据；模型不可用时记录不可用，不悄悄替换。如果环境拒绝读取，记录阻碍，不以跳过审批或沙盒的方式制造通过。

## 观察到的事件

请求没有出现 skill-improve 名称。首条 Agent 消息包含：

> 我会按 `skill-creator` 和 `skill-improve` 检查现有正文与作者约定，补齐新对话独立执行所需的筛选、排序规则。

宿主错误日志显示，Agent 尝试用 pwsh 读取以下文件，其中系统技能路径已去除个人目录：

- drafts/release-summary.md
- drafts/author-notes.md
- 宿主提供的 skill-creator/SKILL.md
- .agents/skills/skill-improve/SKILL.md

结果为 Rejected / blocked by policy。Agent 改为单独读取 drafts/release-summary.md 仍被同类策略拒绝。最终回复明确说明未读取、无法可靠改写，并请求提供文本；没有产生改后技能。

JSONL 以 turn.completed 结束，进程退出码为 0，这只表示运行已结束。实际任务未完成。事件报告 input_tokens=97325、cached_input_tokens=80256、cache_write_input_tokens=0、output_tokens=504、reasoning_output_tokens=58；不从这些字段推导价格或不同环境成本。

本次没有同条件重复、未测负例、未测可选项目规则，也没有通过正文读后执行。后续若获得允许读取的环境，应以全新运行完成相关验证；不能复用本次 Agent 已提到名称的上下文，假称第一次隐式选择。
