# Claude 微信远程连接

> Windows x64 研发预览。首次手机公网扫码和不同网络环境仍在验收中，请勿视为正式稳定版。

本仓库提供 Claude 原生插件目录和版本下载；不是 Anthropic 官方产品。完整插件及依赖许可随 Releases 中的版本包提供。

```text
Claude 微信远程连接 · Windows x64 预览

将 Claude Desktop 的 Code 会话或 Claude Code CLI 接入微信小程序。
同一套插件，两种独立节点：身份、二维码、配对资料和连接开关互不混用。
这是预览版，不是 DSH 插件升级包。已装旧研发包的电脑请先核对安装来源，勿重复安装。
当前验证环境：Windows x64、Claude Code 2.1.304、第三方 API 模式 Desktop 3.1623.1。
macOS、Linux 和其他版本尚未完成验收；本包不能用于这些平台。

一、CLI 用户
1. 在终端执行一条原生命令：
   claude plugin install harness-wechat --marketplace martinbear1/claude-wechat-remote --scope user
2. 在自己的工作目录正常运行 claude。工作区信任提示由你自行确认。
3. 点“微信 CLI 节点 · 打开连接管理 / 手机配对”，或输入 /wechat-connect。
4. 在本机网页点“开启远程连接”→“显示配对二维码”，用小程序添加节点扫码。
5. 保持至少一个已加载插件的 Claude 终端运行，在手机选择该 CLI 节点。
无需另跑连接服务脚本；关闭全部 Claude 终端后 CLI 节点离线。
原有 CLI 会话先在终端恢复一次即可接入；不会把 Desktop 历史自动归入 CLI。
手机新建：选工作区→空白页→首次真正发送才创建会话，不发占位消息。

二、Desktop 用户
1. 在 Claude 的 Code 插件入口打开插件浏览器（Customize / Plugins，
   或输入框旁“+”→Plugins / Add plugins），添加 marketplace：
   martinbear1/claude-wechat-remote
2. 找到“微信远程连接（Windows 预览）”（harness-wechat），安装到用户范围。
3. 首次打开一个自己的 Code 会话，点击“微信连接 · Desktop”，也可输入 /wechat-connect。
4. 在 Claude 内的连接侧栏开启远程连接、显示二维码，用小程序添加节点扫码。
5. 如希望只停留首页也能连接，在侧栏选择“设置随 Desktop 启动”→“确认设置”。
   在 10 分钟内从 Claude 菜单正常退出，稍候再打开；以后无需重复设置。
只关闭窗口可能还在托盘运行，首次设置请使用菜单的退出。
安装收尾只保存本插件的启动项一次后结束，不添加系统开机启动或常驻服务。
如果提示设置未完成，先刷新核对；不要反复点击或手工覆盖配置。
配对入口位于原生连接侧栏，不是插件管理详情页。
Desktop 目前可从手机继续原有会话；手机创建普通新聊天仍未接通，请先在电脑新建。

三、首次手机公网检查
配对时请确认是自己的手机，勿转发管理链接、二维码或配对资料。
配对后可暂时关闭手机 Wi-Fi，使用移动网络打开该节点，检查会话列表和测试消息。
Desktop 首页连接需保持 Desktop 应用运行；CLI 需保持至少一个 Claude 终端运行。
网络、防火墙或公网访问权益仍需满足小程序原有要求，配对成功不代表可绕过这些条件。

四、更新、停用和卸载
在 Claude 原生插件管理中更新；CLI 也可依次执行：
   claude plugin marketplace update claude-wechat-remote
   claude plugin update harness-wechat@claude-wechat-remote --scope user
先结束任务，再按 Claude 提示重新加载；Desktop 首页连接的更新在正常重开后生效。
更新不删除配对，不自动开启已关闭的连接；同一用户配置下两端共用插件版本。
只停用一个节点：在它自己的连接页关闭连接，配对资料保留。
卸载整套插件会影响两端；需要解除手机配对时，请先在小程序管理对应节点。
Desktop 可在连接侧栏关闭“随 Desktop 启动”；停用插件后首页连接会停止，
可能需等待一次状态检查。正常重开后不再启动；配对资料仍保留。
旧研发包的 install.cmd 等入口仅供旧安装维护，不与新装流程混用。

五、连接和权限
配对、端到端加密、中继、安全局域网沿用 DSH 1.7.14 的通信实现。
默认不启用远程连接；配对后的手机可以读取和操作本节点接入的会话与文件。
新装接入当前用户的原生工作区；旧安装明确指定的目录限制不会随更新放宽。
Claude 的工作区信任、工具授权和并发限制仍有效，不会自动批准。
第三方 API 沿用 Claude 自己的配置，插件不设置、复制或展示模型密钥。
```
