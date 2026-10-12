# 统一标准引用：跨仓库接入记录

日期：2026-10-12。用户已授权将统一标准引用加入其其他仓库，并明确保留各仓库原规则。此次授权覆盖本记录描述的接入，不是日后批量修改的常设授权。

## 审查、方案与任务卡

账号共18个仓库：中央仓库已接入，本次对象为其他17个；均未归档且具备写权限。2个对象已有根AGENTS.md，4个已有CLAUDE.md；均保留原文，引用追加在托管段之外。包含3个fork，只修改用户自己的副本，不向上游发送变更。

| 卡 | 目标与范围 | 输入、前提与动作 | 停止条件 | 验收 |
|---|---|---|---|---|
| R1 | 检查17个默认分支、规则及工作流 | GitHub账号清单→默认分支SHA→根Git树和原始规则blob；读取现存AGENTS/CLAUDE及工作流触发条件 | API失败、树截断、异常文件类型、缺写权限时停止该对象 | 确认各文件原字节和基准SHA；不把读取失败当作不存在 |
| R2 | 接入AI入口 | 无AGENTS则创建，有则仅追加中央模板；已有CLAUDE仅追加本地AGENTS引用；有GSD约束的项目用quick记录计划/证据 | 重复标记、原文变化、不可判定状态或规则冲突时停止；不覆盖原内容 | 新文件可读；旧内容逐字节保留；仅本次入口和必要任务记录被修改 |
| R3 | 测试、验收、提交 | 隔离快照验证引用/原文/变更范围；按仓库提交，使用expectedHeadOid拒绝并发覆盖；回读文件及提交差异；检查本次SHA的CI | 提交失败/并发变化/远端校验失败，停止该对象后续步骤并记录，不重试或强推 | 各仓库远端字节与候选相同，旧规则无删除；CI通过、未触发、未配置、失败分别报告 |

只接入引用，不运行项目业务，不改变规则优先级、分支保护、工作流、依赖或默认配置。若旧规则与中央要求冲突，入口要求明确报告，不静默废除旧规则。私有仓库名称、原文及详细操作材料不汇总到本公开记录。

## 验收

| 里程碑/整体 | 实际证据 | 结论 |
|---|---|---|
| R1 审查 | 17个对象的默认分支、原始规则blob和工作流触发条件已读取 | 通过，无归档或无写权限对象 |
| R2 接入 | 15个新AGENTS；2个已有AGENTS及4个CLAUDE原字节全部保留，引用仅追加 | 通过，共21个AI入口文件 |
| R2 GSD记录 | 3个项目完成quick初始化、计划、summary和状态记录；1个旧任务表依GSD规范化并检查旧数据单元格及其他文字保留 | 通过，原AI规则没有被改写 |
| R3 发布 | 每次提交带expectedHeadOid；原文前缀、提交文件范围、无规则删除、远端内容与最终默认分支SHA均核验 | 17/17通过 |
| R3 CI | 3个触发的工作流完成且成功；2个已配置未触发；12个未配置 | 逐次SHA核验完成，不把未触发称为通过 |
| 整体 | 所有目标均接入；本次代码/依赖/工作流未修改；私有仓库详情只写本地报告 | 本次引用接入范围完成 |

跨AI自动读取与行为验证未执行；添加入口不意味着所有AI工具必定加载。本次没有修改现用代理或应用。现有meishu-ui的push工作流自动完成Pages部署，未修改其触发设置。

## 公开仓库提交证据

私有仓库的名称及逐项提交详情不发布到此公开记录。


| 仓库 | 提交 | CI |
|---|---|---|
| [Scrapling](https://github.com/qixian771-spec/Scrapling) | [09509209](https://github.com/qixian771-spec/Scrapling/commit/095092099598edc212a80a982535b6093ef65749) | 已配置，本次未触发 |
| [agents-bianxiezhuanjia](https://github.com/qixian771-spec/agents-bianxiezhuanjia) | [3f11234e](https://github.com/qixian771-spec/agents-bianxiezhuanjia/commit/3f11234e92d47c8631a5acf8d7b04fc850fad260) | 未配置 |
| [claude-client-full-reset](https://github.com/qixian771-spec/claude-client-full-reset) | [c03755c8](https://github.com/qixian771-spec/claude-client-full-reset/commit/c03755c8bb6824f24dc2f8a72387261bf403ccf8) | [Validate skill package：通过](https://github.com/qixian771-spec/claude-client-full-reset/actions/runs/38316724749) |
| [codeviz](https://github.com/qixian771-spec/codeviz) | [e33a0582](https://github.com/qixian771-spec/codeviz/commit/e33a05821947b4e9450ceb7b5766a0af228eb97a) | 未配置 |
| [codeviz-visualizer](https://github.com/qixian771-spec/codeviz-visualizer) | [97211e18](https://github.com/qixian771-spec/codeviz-visualizer/commit/97211e187306ab5b3b11997e6309cdcacd27b97f) | 未配置 |
| [expert-teams](https://github.com/qixian771-spec/expert-teams) | [cd5429ba](https://github.com/qixian771-spec/expert-teams/commit/cd5429bada0004c3777d8ab1b22268dfb5ee0ef4) | 未配置 |
| [meishu-ui](https://github.com/qixian771-spec/meishu-ui) | [73861fe4](https://github.com/qixian771-spec/meishu-ui/commit/73861fe42900568513d21895edd4b7293ce7da76) | [Deploy demo to GitHub Pages：通过](https://github.com/qixian771-spec/meishu-ui/actions/runs/38316773369) |
| [red-gsd](https://github.com/qixian771-spec/red-gsd) | [8f430150](https://github.com/qixian771-spec/red-gsd/commit/8f430150a634fc99e49f2f7591a96bbd59bb648c) | 未配置 |
| [social-auto-upload](https://github.com/qixian771-spec/social-auto-upload) | [b9f083a7](https://github.com/qixian771-spec/social-auto-upload/commit/b9f083a7fe4f2e01077ab58973d2a1e34c76d7b8) | 未配置 |
| [system_prompts_leaks](https://github.com/qixian771-spec/system_prompts_leaks) | [0249a33e](https://github.com/qixian771-spec/system_prompts_leaks/commit/0249a33ef655d134120ce3c4cba9a23dbd89514e) | 未配置 |
| [vps-node-rebuild-3xui](https://github.com/qixian771-spec/vps-node-rebuild-3xui) | [873ee5c8](https://github.com/qixian771-spec/vps-node-rebuild-3xui/commit/873ee5c898ae9a09985faec71477ca8dea2f66da) | [Skill delivery validation：通过](https://github.com/qixian771-spec/vps-node-rebuild-3xui/actions/runs/38316806162) |
