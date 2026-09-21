# ProcWeaver-Rules

[ProcWeaver](https://github.com/jojhaa/ProcWeaver) 的业务规则包仓库，目前只提供 **OpenAI** 和**反重力（Antigravity）**两个包。

规则包用于组织应用进程与域名分流，可下载到 ProcWeaver 中导入，并按自己的业务需要编辑。

## 下载规则包

| 规则包 | 适用进程 | 下载 |
| --- | --- | --- |
| OpenAI / ChatGPT | `ChatGPT.exe`、`codex.exe`、`node.exe` | [OpenAI 规则包](https://raw.githubusercontent.com/jojhaa/ProcWeaver-Rules/main/Business-Rules/openai-chatgpt.pwpack.json) |
| 反重力 / Antigravity | `Antigravity.exe`、`language_server.exe`、`agy.exe`、`antigravity-service.exe` | [反重力规则包](https://raw.githubusercontent.com/jojhaa/ProcWeaver-Rules/main/Business-Rules/google-antigravity.pwpack.json) |

浏览器直接显示 JSON 时，将其另存为原文件名即可。也可以在 ProcWeaver 的规则仓库入口获取。

## 出口由你选择

**每次导入后都需要重新绑定自己的出口。**

包内只有进程、域名及出口插槽定义，不携带原作者的订阅、节点凭据或本机绑定。为主业务出口选择自己的节点或策略组，DNS 出口可跟随主出口或另行选择。

导入后请核对进程范围；`node.exe`、`language_server.exe` 等同名进程也可能属于其他应用。规则需要结合实际代理模式使用，导入包本身不代表目标应用已经接管成功。

客户端介绍见 [ProcWeaver 主仓库](https://github.com/jojhaa/ProcWeaver)，安装包及分发附件见 [Releases](https://github.com/jojhaa/ProcWeaver-Rules/releases)。

## 许可证

Copyright (C) 2026 jojhaa.

本仓库原创规则包以 **GNU Affero General Public License v3.0（AGPL-3.0-only）** 提供，完整条款见 [LICENSE](LICENSE)。项目不提供任何担保。

OpenAI、ChatGPT、Codex、Antigravity 等名称仅标明适用程序。本仓库由 ProcWeaver 项目独立维护，不表示相关厂商参与或认可。
