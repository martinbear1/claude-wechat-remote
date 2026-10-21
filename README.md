# Claude 微信远程连接

> Windows x64 预览版，尚非正式稳定版。当前验证环境：Claude Code 2.1.304、第三方 API 模式 Claude Desktop 3.1623.1。

本仓库提供 Claude 原生插件目录和版本下载；不是 Anthropic 官方产品。完整插件及依赖许可随 Releases 中的版本包提供。

将 Claude Desktop 的 Code 会话或 Claude Code CLI 接入微信小程序。同一套插件，Desktop 和 CLI 分别扫码，拥有独立节点、配对资料和连接开关。

## Desktop：在 Claude 内安装和扫码

1. 打开 **Customize → Plugins → Discover → Add marketplace → Add from a repository**，填入 `martinbear1/claude-wechat-remote`。
2. 安装“微信远程连接（Windows 预览）”，安装范围选择 **User**。
3. 首次打开一个 Code 会话，打开“微信连接 · Desktop”（也可输入 `/wechat-connect`）。
4. 在 Claude 内的连接侧栏点击“开启远程连接”，显示二维码，用小程序“添加节点”扫码。
5. 若希望只打开 Desktop 首页就能连接，再点“设置随 Desktop 启动”并确认。在 10 分钟内从 Claude 菜单正常退出，稍候重开；这一步只需设置一次。

无需外部安装脚本。首次设置请用菜单退出，仅关闭窗口可能仍在托盘运行。设置未完成时，先刷新核对，不要反复点击或手工覆盖配置。

配对页面位于原生连接侧栏，不是插件管理详情页。Desktop 目前可从手机继续原有会话；手机创建普通新聊天尚未接通，请先在电脑新建。

## CLI：一条命令安装，点链接扫码

先确认 Claude Code 本身已能正常使用，再执行：

```sh
claude plugin install harness-wechat --marketplace martinbear1/claude-wechat-remote --scope user
```

1. 在自己的工作目录正常运行 `claude`，按原生提示确认工作区。
2. 点“微信 CLI 节点 · 打开连接管理 / 手机配对”；也可输入 `/wechat-connect`。
3. 在打开的本机网页点击“开启远程连接”，显示二维码，用小程序“添加节点”扫码。
4. 保持至少一个已加载插件的 Claude 终端运行，即可在手机选择 CLI 节点使用。

无需另跑连接服务脚本，关闭全部 Claude 终端后 CLI 节点离线。原有 CLI 会话先在终端恢复一次即可接入，不会把 Desktop 历史自动归入 CLI。

手机新建会话：选择工作区 → 进入空白页 → 首次真正发送时创建会话，不发占位消息。

## 更新、停用和卸载

在 Claude 原生插件管理中更新；CLI 也可依次执行：

```sh
claude plugin marketplace update claude-wechat-remote
claude plugin update harness-wechat@claude-wechat-remote --scope user
```

先结束任务，再按 Claude 提示重新加载。Desktop 首页连接的更新需正常退出并重开后生效。更新保留配对，不自动开启已关闭的连接；同一用户配置下两端共用插件版本。

只停用一个节点，在该节点的连接页关闭连接即可，配对保留。卸载整套插件会影响两端；解除手机配对请在小程序管理对应节点。Desktop 连接侧栏也可关闭“随 Desktop 启动”；停用插件后首页连接会停止，可能需等待一次状态检查，正常重开后不再启动。

## 适用范围与注意事项

- 本包仅供 Windows x64 使用，macOS、Linux 及其他版本尚未完成验收。
- 这是 Claude 预览插件，不是 DSH 升级包。已装旧研发包的电脑请先核对安装来源，不要重复安装同名插件。
- Desktop 需保持应用运行，CLI 需保持至少一个 Claude 终端运行。首次配对后可用手机移动网络检查连接；公网访问仍需满足小程序原有的网络与权益要求。
- 默认不启用远程连接。配对后的手机可以读取和操作该节点接入的会话与文件，请勿转发管理链接、二维码或配对资料。
- 配对、端到端加密、中继和安全局域网沿用 DSH 1.7.14 的通信实现。不添加系统开机启动或独立常驻服务。
- 新装不限定测试工作区，旧安装明确设置的目录限制不会随更新放宽。Claude 原生工作区信任、工具授权和并发限制仍有效，不会自动批准。
- 模型服务沿用 Claude 自己的配置，插件不设置、复制或展示模型密钥。
