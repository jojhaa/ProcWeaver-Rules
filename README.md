# ProcWeaver-Rules

[ProcWeaver](https://github.com/jojhaa/ProcWeaver) 官方业务规则包仓库与客户端发行中心。

---

## 仓库概述

本仓库专用于托管面向 [ProcWeaver](https://github.com/jojhaa/ProcWeaver) 客户端的**业务规则包（Business Rulesets）**预设模板与最新发行版本。

ProcWeaver 创新性地采用“以业务为中心”的精细化分流模式。通过规则包，用户可以将特定应用的主进程、深层伴生子进程树以及业务域名整体打包，为其指派专属的出站节点与独立 DNS。本仓库提供的规则包由官方维护，开箱即用，帮助用户快速构建隔离、纯净的业务网络环境。

---

## 官方预设业务规则包

当前仓库提供并维护两套核心生产力业务规则包：

| 规则包名称 | 适用业务场景 | 纳管的核心进程 | 纳管的核心域名 | 规则包下载 |
| --- | --- | --- | --- | --- |
| **OpenAI / ChatGPT 生产力套件** | ChatGPT 桌面客户端、Web 访问、Codex 及相关 API 研发调试 | `ChatGPT.exe`<br>`codex.exe`<br>`node.exe` | `openai.com`<br>`chatgpt.com`<br>`oaistatic.com`<br>`oaiusercontent.com`<br>`auth0.openai.com` | [下载规则包 (JSON)](https://raw.githubusercontent.com/jojhaa/ProcWeaver-Rules/main/Business-Rules/openai-chatgpt.pwpack.json) |
| **Google Antigravity 2.0 研发套件** | Antigravity IDE、语言推理模型工作进程及 CLI 工具链 | `Antigravity.exe`<br>`language_server.exe`<br>`agy.exe`<br>`antigravity-service.exe` | `antigravity.google`<br>`gemini.google.com`<br>`generativeai.google`<br>`aistudio.google.com` | [下载规则包 (JSON)](https://raw.githubusercontent.com/jojhaa/ProcWeaver-Rules/main/Business-Rules/google-antigravity.pwpack.json) |

> 📁 规则包源文件存放于 [`Business-Rules/`](Business-Rules/) 目录。下载时如遇浏览器直接展示 JSON 文本，可直接右键“另存为”保存为 `.pwpack.json` 文件。

---

## 规则包核心机制与安全设计

为了保证规则在跨设备、跨用户之间分发的安全性与灵活性，ProcWeaver 业务规则包遵循以下设计准则：

### 1. 规则定义与出口插槽解耦（Slot Architecture）

规则包仅描述**“匹配哪些应用进程”**、**“匹配哪些业务域名”**以及**“需要哪些出口用途”**，不包含任何具体用户的节点配置：

- **主业务出口（Main Slot）**：业务主进程与核心后台伴生进程访问外网所使用的代理节点。
- **DNS 解析出口（DNS Slot）**：该业务关联域名的专属解析出口，默认智能跟随主业务出口，亦可单独指定，彻底防止 DNS 投毒与污染。

### 2. 零隐私与安全便携性

- **无敏感凭据**：导出的规则包文件不包含任何本机的订阅链接、节点 IP、端口、密码或私有密钥。
- **独立绑定生效**：**每次导入新规则包后，用户都需要在 ProcWeaver 中为插槽重新选定本机当前订阅的节点**。未完成出口绑定的规则包不会静默启用，杜绝因未配置而引发流量泄漏或非预期回退。

### 3. 动态子进程树穿透保障

针对现代开发套件动态拉起后台 Worker（如 LSP 语言服务、CLI 编译进程）的特征，规则包配合 ProcWeaver 客户端的“包含未来子进程”机制，可自动追踪并纳管衍生后代，无需繁琐手动逐一添加。

---

## 快速使用指南

1. **获取客户端**：安装并启动 [ProcWeaver 客户端](https://github.com/jojhaa/ProcWeaver)。
2. **下载规则包**：从本仓库 [`Business-Rules/`](Business-Rules/) 目录下载所需的 `.pwpack.json` 规则包文件。
3. **导入与配置**：
  - 打开 ProcWeaver 的“业务规则包”管理界面，点击“导入规则包”并选择下载的文件；
  - 在规则包配置面板中，为“主业务出口”和“DNS 解析出口”分别绑定你当前订阅中的可用节点；
  - 确认进程匹配范围（注：若存在同名程序如 `node.exe`，请核对实际路径是否符合业务预期）；
  - 点击“启用规则包”即可立即生效。

---

## 客户端下载与发布中心

ProcWeaver 客户端的正式安装包、免安装便携版压缩包及分发材料均发布于本仓库的 Releases 页面：

👉 **[前往 ProcWeaver 官方发布页面 (Releases)](https://github.com/jojhaa/ProcWeaver-Rules/releases)**

- **安装版**：`ProcWeaver_vX.X.X_x64_Setup.exe`
- **便携版**：`ProcWeaver_vX.X.X_x64_Portable.zip`
- **源码与架构仓库**：[jojhaa/ProcWeaver](https://github.com/jojhaa/ProcWeaver)

---

## 声明与开源许可

### 仅供学习声明

本仓库托管的所有规则包及分发内容**仅供计算机网络协议、分流路由机制及应用进程调度的个人学习、技术研究与学术交流**使用。

1. 本仓库仅提供分流匹配逻辑模板与客户端分发，**不提供任何网络代理节点、服务器资源或规避网络监管的服务**。
2. 规则包内所有条目均为开源的文本匹配规则，不包含任何商业机密、私有凭据或侵权内容。
3. 使用者应当严格遵守所在地区的法律法规。任何因将本仓库规则包用于技术研究之外的用途所引发的责任与后果，均由使用者自行承担，项目维护者不承担任何法律责任。

### 开源许可证

本仓库原创规则包遵循 **[GNU Affero General Public License v3.0 (AGPL-3.0-only)](LICENSE)** 协议开源。

### 商标与第三方说明

文中所涉及的 OpenAI、ChatGPT、Codex、Antigravity、Google 等公司、产品及服务名称，仅用于客观标明规则包适配的软件与域名范围。本仓库由 ProcWeaver 开源社区独立维护，不代表相关厂商参与、赞助或认可本项目。
