# WindTermPro

面向开发者与运维人员的跨平台终端项目，支持 SSH、SFTP、SCP、Telnet、TCP、串口和本地 Shell，并提供 tmux 集成、会话管理、文件传输与多窗口分屏等功能。

本仓库派生自 [kingToolbox/WindTerm](https://github.com/kingToolbox/WindTerm)。下文介绍的是上游 WindTerm 已公开说明的功能，具体可用功能以所使用的发行版本为准。

## 目录

- [项目简介](#项目简介)
- [下载与入门](#下载与入门)
- [界面预览](#界面预览)
- [主要功能](#主要功能)
- [源码说明](#源码说明)
- [性能与基准测试](#性能与基准测试)
- [文档与快捷键](#文档与快捷键)
- [问题反馈与交流](#问题反馈与交流)
- [开发计划](#开发计划)
- [许可证](#许可证)
- [致谢](#致谢)

## 项目简介

WindTerm 将远程连接、本地终端、文件管理和会话组织整合在同一界面中，适用于日常开发、服务器管理、远程文件传输和串口调试。

- **跨平台**：支持 Windows、macOS 和 Linux。
- **多种连接方式**：支持 SSH v2、Telnet、原始 TCP、串口及本地 Shell。
- **终端与文件传输一体化**：内置 SFTP、SCP 客户端和本地文件管理器。
- **高效操作**：提供自动补全、同步输入、命令面板、快捷栏和分屏视图。
- **会话管理**：支持会话树、代理、跳板机、日志记录及布局恢复。
- **多语言界面**：支持包括简体中文在内的多种界面语言。

## 下载与入门

### 下载

Windows、macOS 和 Linux 的 WindTerm 二进制程序请从[上游发行页面](https://github.com/kingToolbox/WindTerm/releases)获取，选择与操作系统和处理器架构匹配的安装包或压缩包，并参考对应版本的发行说明。

**该链接提供的是上游 WindTerm 发行包。** 本仓库中的部分源码不能直接视为完整的 WindTermPro 安装包。

### 基本使用流程

1. 下载适合当前系统的发行包，按发行说明安装或解压后启动。
2. 新建会话，按用途选择 SSH、Telnet、串口或本地 Shell 等类型。
3. 配置连接地址、端口和认证方式；串口会话则配置对应的串口参数。
4. 连接成功后，在终端中执行命令；需要传输文件时，可使用内置的文件管理功能。
5. 根据需要设置会话分组、分屏布局、主题、快捷键和日志记录。

详细操作可参考[新建会话教程](https://kingtoolbox.github.io/2020/01/22/new-session/)和[会话管理教程](https://kingtoolbox.github.io/2020/01/22/manage-sessions/)。

## 界面预览

### 主界面（zsh）

![WindTerm 主界面](images/screenshots/WindTerm.png)

### 分屏视图

![WindTerm 分屏视图](images/screenshots/SplitView.png)

### DigeWhite 浅色主题

![WindTerm DigeWhite 浅色主题](images/screenshots/WindTerm_DigeWhite_Theme.png)

## 主要功能

### 连接与认证

- 支持 SSH v2、Telnet、原始 TCP、串口和本地 Shell。
- 支持 SSH 认证成功后自动执行命令，以及 SSH ControlMaster。
- 支持 [ProxyCommand 和 ProxyJump](https://kingtoolbox.github.io/2021/03/11/proxycommand/)。
- 支持 [SSH Agent](https://kingtoolbox.github.io/2020/08/22/ssh_agent/) 及 Agent 转发。
- 支持密码、公钥、键盘交互等 SSH 自动登录方式，详见[自动登录教程](https://kingtoolbox.github.io/2020/01/23/auto-login/)。
- 支持 [X11 转发](https://kingtoolbox.github.io/2020/07/21/x11_forwarding/)。
- 支持[本地、远程和动态端口转发](https://kingtoolbox.github.io/2020/07/21/port_forwarding/)。
- 支持 [HTTP、SOCKS5 代理](https://kingtoolbox.github.io/2021/03/11/proxy-http-socks5/)和[跳板机代理](https://kingtoolbox.github.io/2021/03/11/proxy-jump-server/)。
- 支持 [tmux 集成](https://kingtoolbox.github.io/2025/01/05/tmux-integration/)。

### 文件传输与管理

- 内置 SFTP、SCP 客户端，支持上传、下载、删除、重命名及新建文件或目录等操作。
- 内置本地文件管理器，支持复制、移动、删除、重命名及新建文件或目录等操作。
- 支持 [XModem、YModem 和 ZModem](https://kingtoolbox.github.io/tags/modem/) 文件传输。
- 通过[文件传输教程](https://kingtoolbox.github.io/tags/transfer/)了解具体操作。

### 本地 Shell

- Windows：支持 Cmd、PowerShell，以及以管理员身份运行的 Cmd 和 PowerShell。
- Linux：支持 Bash、Zsh、PowerShell Core 等。
- macOS：支持 Bash、Zsh、PowerShell Core 等。
- 支持 Powerline 风格显示，可配合 Oh My Zsh、Oh My Posh 等使用。

### 界面与操作效率

- 支持多语言界面、主题切换、配色方案、标签页颜色和窗口透明度设置。
- 支持会话对话框、会话树、资源管理器面板和 Shell 面板。
- 支持[自动补全](https://kingtoolbox.github.io/tags/auto-completion/)、[自由输入模式](https://kingtoolbox.github.io/2022/04/12/free_type_mode/)和[专注模式](https://kingtoolbox.github.io/2021/06/28/ui_focus_mode/)。
- 支持[同步输入](https://kingtoolbox.github.io/2021/05/27/sync-input/)，方便同时向多个会话发送命令。
- 支持[命令面板](https://kingtoolbox.github.io/tags/command-palette/)、[命令发送器](https://kingtoolbox.github.io/tags/sender/)和[快捷栏](https://kingtoolbox.github.io/2020/08/22/quickbar/)。
- 支持[粘贴对话框](https://kingtoolbox.github.io/2020/08/22/paste_dialog/)、选中即复制、右键或中键粘贴。
- 支持带有 Vim 键位的本地与远程模式，可使用 `Shift+Enter` 切换，详见[键盘模式说明](https://kingtoolbox.github.io/2020/06/21/keyboard-modes/)。
- 支持时间戳、文本折叠、大纲和分屏视图。
- 支持[文本搜索与预览](https://kingtoolbox.github.io/2020/01/22/search-and-mark/)，以及括号和自定义分隔符的配对高亮。
- 支持搜索已打开的标签页，以及关闭右侧标签页。
- 支持通过 Google、Bing、GitHub、Stack Overflow、Wikipedia 和 DuckDuckGo 在线搜索选中文本。
- 支持输入时隐藏鼠标指针，以及[锁屏](https://kingtoolbox.github.io/2021/04/23/lock-screen/)功能。
- 提供[会话用户名与密码保护](https://kingtoolbox.github.io/2021/03/11/protection-username-password/)功能。

### 终端与会话

- 支持 VT100、VT220、VT340、VT420、VT520、xterm 和 xterm-256color 等终端类型。
- 支持 Unicode、Emoji、真彩色、鼠标协议及自动换行。
- 支持自定义协议与终端配置。
- 支持手动和自动[会话日志记录](https://kingtoolbox.github.io/tags/logging/)。
- 支持重命名、复制会话，以及重启后[恢复会话与布局](https://kingtoolbox.github.io/2020/01/22/restore-sessions/)。
- 支持启动时打开指定会话或一组会话。

## 源码说明

**WindTerm 是部分开源项目。** 根据上游说明，源码将逐步开放；本仓库目前包含部分协议实现、工具类、界面组件及第三方库，未提供完整应用的源码和根目录构建入口。

### 仓库结构

```text
WindTermPro/
├── benchmark/       # 基准测试脚本
├── images/          # 项目图标、截图等资源
├── src/
│   ├── libssh/      # SSH 库及其改进代码
│   ├── Onigmo/      # 正则表达式库及其改进代码
│   ├── Pty/         # 伪终端相关实现
│   ├── Protocols/   # 协议接口与 Telnet 实现
│   ├── Utility/     # 缓冲区、加密、线程等工具类
│   ├── Widgets/     # 弹出窗口、滚动条、分隔器等组件
│   ├── LICENSE      # Apache-2.0 许可证文本
│   └── README.md    # 已公开组件说明（英文）
└── README.md        # 中文项目说明
```

### 已公开组件

- **libssh**：增加 Pageant、外部 Socket 及部分 HMAC 算法支持。
- **Onigmo**：增加迭代器支持，可对间隙缓冲区或不连续内存块进行匹配。
- **Pty**：基于 [ptyqt](https://github.com/kafeg/ptyqt) 改进的伪终端实现。
- **Protocols**：协议接口及 Telnet 协议实现。
- **Utility**：循环缓冲区、加密工具、智能指针、作用域清理、自旋锁和线程局部存储等。
- **Widgets**：弹出窗口、支持 64 位范围的滚动条及分隔器组件。

更多细节见 [src/README.md](src/README.md)。使用单独组件时，请结合对应源码、依赖及许可证说明进行集成。

## 性能与基准测试

WindTerm 以高吞吐、低延迟和较低内存占用为设计目标，并提供动态内存压缩机制。

原始 README 中的 SFTP、终端输出、Linux 终端和输入延迟测试主要使用 2020 年前后的软件版本。相关结果受硬件、操作系统、网络、终端配置和回滚行数影响，应作为历史参考，不能直接代表当前版本的表现。

- [本仓库基准测试脚本](benchmark/urandom_test.sh)
- [上游 README 中的性能资料](https://github.com/kingToolbox/WindTerm#sftp-performance)
- [上游性能演示](https://kingtoolbox.github.io/2020/01/23/windterm-putty-performance/)

## 文档与快捷键

- [上游介绍与教程](https://kingtoolbox.github.io)
- [快捷键说明](https://kingtoolbox.github.io/tags/keyboard/)
- [会话管理](https://kingtoolbox.github.io/2020/01/22/manage-sessions/)
- [自动补全](https://kingtoolbox.github.io/tags/auto-completion/)
- [文件传输](https://kingtoolbox.github.io/tags/transfer/)
- [tmux 集成](https://kingtoolbox.github.io/2025/01/05/tmux-integration/)

## 问题反馈与交流

欢迎反馈问题、提出功能建议或改进文档。

- 本仓库的修改与文档建议：通过 [Pull Request](https://github.com/aa24615/WindTermPro/pulls) 提交。
- 上游 WindTerm 的使用问题与功能请求：访问 [Issues](https://github.com/kingToolbox/WindTerm/issues)。
- SSH、SFTP、Shell、Telnet、串口和 WindTerm 相关讨论：访问 [Discussions](https://github.com/kingToolbox/WindTerm/discussions)。

反馈问题时，建议附上操作系统、WindTerm 版本、连接类型、复现步骤，以及脱敏后的日志或截图，便于定位。

## 开发计划

原始 README 包含 v2.7 及后续版本的历史规划，涉及命令片段、会话搜索、外部工具、更多协议、脚本、宏和插件等方向。**历史规划不代表当前已实现功能或本仓库的交付承诺。**

当前发布内容与开发进展请参考[上游发行说明](https://github.com/kingToolbox/WindTerm/releases)及[上游项目](https://github.com/kingToolbox/WindTerm)。

## 许可证

根据上游项目说明，WindTerm 可免费用于商业和非商业用途；已发布源码（第三方目录除外）采用 Apache-2.0 许可证。

许可证全文见 [src/LICENSE](src/LICENSE)。第三方组件请遵循各自随附的许可证。

## 致谢

感谢 [kingToolbox](https://github.com/kingToolbox) 及所有为 WindTerm 开发、翻译和改进作出贡献的参与者。

原始 README 致谢的翻译贡献者包括：

- [EvoWebFrance](https://github.com/EvoWebFrance)：法语翻译。
- [kvnklk](https://github.com/kvnklk)：德语翻译。
- [Lemonawa](https://github.com/Lemonawa)：简体中文翻译。
- [LuxNegra](https://github.com/LuxNegra)：法语翻译。
- [MosamXu](https://github.com/MosamXu)：简体中文翻译。

如果你也需要高性能文本编辑器，可以了解同一作者的 [WindEdit](https://github.com/kingToolbox/WindEdit)。
