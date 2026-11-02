# Codex Sidebar Chat 0.3.0

在 Obsidian 桌面端使用本机 Codex 登录账号进行侧边栏对话。请先安装 Codex CLI，并在同一 Windows 用户下运行 `codex login`。插件不保存账号密码或自行读取登录令牌。

## 安装与更新

将 `manifest.json`、`main.js`、`styles.css` 复制到目标仓库的 `.obsidian/plugins/obsidian-codex-chat/`，在 Obsidian 的第三方插件设置中启用。更新后请重启 Obsidian 或先停用再启用插件。如果找不到 Codex，在插件设置中填写 `codex.exe` 完整路径；本机路径是 `C:\Users\Administrator\AppData\Local\Microsoft\WinGet\Links\codex.exe`。更改路径后请重新打开聊天面板。

## 使用

- 点击左侧聊天图标或执行“打开 Codex 对话”。Enter 发送，Shift + Enter 换行。
- 界面采用暖色、衬线正文的对话风格，自动跟随 Obsidian 的明暗主题。空白页的快捷建议会填入提示词（笔记类建议会同时开启“当前笔记”），可编辑后发送。回复下方可一键复制。
- 顶部历史按钮显示当前仓库对应的本机 Codex CLI、编辑器会话；点击可查看并继续。每条右侧可删除，删除会同时清掉本机会话记录。列表支持加载更多，不含已归档会话。读取会话时仅展示文字消息。插件本身不缓存对话，记录由 Codex 保存在用户目录的 `.codex\sessions`。
- 输入框右下角显示当前窗口的剩余额度百分比。点击它或右上角头像，可查看本机 Codex 当前登录账号、订阅类型，以及服务返回的使用百分比、重置时间和可用积分。无数据时显示不可用，实际额度以 Codex 服务为准。
- 输入框底栏从左到右：模型、推理强度（Effort，选项由所选模型提供）、上下文占用环（本会话最近一轮占模型上下文窗口的比例，读自本机会话记录）、额外文件夹（通过 `--add-dir` 传给 Codex，并在提问里告诉它这些路径）、附带当前笔记，以及右侧的 YOLO 开关。设置会保存，切换对下一次发送生效。
- YOLO 关闭时使用只读沙箱；开启时改用 `--dangerously-bypass-approvals-and-sandbox`，Codex 可以直接修改文件和执行命令，开启前会弹窗确认。
- 点亮输入框左下角的“当前笔记”按钮（开启后显示笔记名）会将当前 Markdown 笔记全文附加至本次提问。Codex 也可能根据问题读取工作区文件，不勾选不代表禁止读取。
- 插件传入只读沙箱参数，但具体隔离能力与操作系统和 Codex 配置相关，外部 MCP 服务不一定受此限制。Codex 自身可能保存会话记录；对话完成后会刷新额度。
- 当前回复在完整消息生成后显示，尚不支持逐字流式输出。需要 Obsidian 桌面端，移动端不支持。
