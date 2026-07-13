# 💬 unobox

<p align="center">
  <img src="docs/assets/icon-256.png" alt="unobox logo" width="128" height="128">
</p>

<p align="center"><strong>你的数据，你掌控。支持端到端加密的 AI 驱动私有即时通讯。</strong></p>

[🌐 官网](https://unobox.zhenzhidaole.com) ·
[📦 最新版本](https://github.com/samjoeyang/unobox-release/releases/latest) ·
[📋 更新日志](https://unobox.zhenzhidaole.com/changelog.html) ·
[🇬🇧 English](README-EN.md)

---

**unobox** 是一款面向 **Windows、macOS、Linux、iOS 和 Android** 的 Telegram 风格私有即时通讯应用。它让你完全掌控自己的数据——所有内容可存于本地或你自己的服务器——同时集成了 8 大 AI 模型、全格式文件预览器，以及内置浏览器和智能视频嗅探功能。

> 🧪 由一人借助 AI 辅助在约 20 天内构建完成。这是 AI 增强开发时代可行性的一枚活生生的证明。
>
> 📱 移动端从 v0.3.0 开始计算版本：当前已完成本地聊天功能完整闭环（群组/频道/消息/投票/评论/定时消息/慢速模式/文件夹/Bot/频道统计/全局搜索/文件管理），UI 全面重构为 Paper 主题。

<p align="center">
  <img src="web/assets/unobox_ui.png" alt="unobox 主界面" width="800">
</p>

---

## ✨ 功能特性

### 🛡️ 数据主权

- **本地优先存储** —— 基于 SQLite，数据留存在你的设备上，完全离线可用
- **🔒 全协议端到端加密** —— 三种 Provider 模式均已实现 E2EE
  - LocalProvider：XSalsa20-Poly1305 消息级加密 + 附件加密
  - WebSocketProvider：X3DH + Double Ratchet 端到端加密（带内协商 + 服务端辅助）
  - MatrixProvider：Olm + Megolm（matrix-sdk-crypto-wasm，兼容 Element 等客户端）
  - UI 层完整：设置面板 / 多服务器开关 / 密钥备份恢复 / 聊天导出 / E2EE 状态图标
  - **部署级加密策略**：支持 `none`（明文版）/ `optional`（自由选择）/ `mandatory`（强制加密）三种分发模式
- **自建 WebSocket 服务器** —— 用于局域网/团队通信，零第三方访问
- **Matrix 联邦支持** —— 连接任意 Matrix/Synapse 服务器
- **三种模式自由选择**：纯本地 / WebSocket 局域网 / Matrix 全球互联

### 🎨 Telegram 风格 UI

- 高保真三栏布局，精美的消息气泡
- 深色/浅色主题，可调节字体大小
- **国际化（i18n）**：基于 i18next + react-i18next，支持中/英文切换、远程下载语言包、聊天文件安装，57/57 组件全面覆盖
- **群组**：成员管理、管理员角色、群公告、慢速模式
- **频道**：订阅者管理、定时发文（主进程调度器自动发布）、数据统计面板
- **话题**（超群式子房间）
- **投票**（单选/多选、倒计时、实时结果）
- **机器人框架**：内联键盘、Webhook、内置命令

### 🤖 内置 9 大 AI 模型

| 提供商                               | 支持情况               |
| ------------------------------------ | ---------------------- |
| OpenAI（GPT-4o、GPT-4、o3 等）       | ✅ 流式输出            |
| Anthropic Claude（Sonnet、Opus）     | ✅ 流式输出 + 扩展思考 |
| Google Gemini（Pro、Flash、2.5 Pro） | ✅ 流式输出            |
| DeepSeek（V3、R1）                   | ✅ 推理过程显示        |
| OpenRouter（100+ 模型）              | ✅ 所有供应商          |
| 阿里通义千问（QwQ-32B、Qwen-Plus）   | ✅                     |
| MiniMax                              | ✅                     |
| **火山引擎（Coding Plan）**          | ✅                     |
| 自定义兼容 OpenAI 接口               | ✅                     |

- 实时**流式输出**（逐 token 显示）
- 推理模型的**思考过程可视化**
- **持久化 AI 会话** —— 应用重启不丢失
- 每个会话可绑定不同模型，保留完整上下文
- AI 回复支持 **Markdown 图片渲染**和全屏预览
- **会话管理**：右键菜单重命名/删除

### 📄 全格式文件预览

- **电子书阅读器**（EPUB/MOBI/AZW/FB2/CBZ）—— 基于 foliate-js 统一渲染引擎：字号/行距/主题切换、点击翻页/键盘翻页、全文 FTS5 搜索、阅读位置记忆、有声书跟读高亮
- **有声书（EPUB → 语音）** —— TTS 逐句朗读 + 当前句高亮 + 自动翻页，跨章节连续播放
- **有声书导出** —— 将当前章节所有句子批量合成 → FFmpeg 拼接 → 导出 WAV/MP3 音频文件
- **Word（.docx）** —— 以 HTML 渲染，支持主题自适应样式
- **Excel（.xlsx / .csv）** —— 多工作表表格查看器
- **PDF** —— 逐页浏览
- **Markdown** —— 内联渲染
- **Office 预览模式** —— 内置或在系统应用中打开

### 🌐 内置浏览器 + 智能视频嗅探

- 聊天中的链接在**独立浏览器窗口**中打开，带工具栏（前进/后退/刷新/地址栏）
- **3 层视频嗅探**：
  - 第 1 层：URL 正则匹配（`.mp4`, `.m3u8`, `.mpd`, `.flv`, `.webm` 等）
  - 第 2 层：Content-Type 响应头检测
  - 第 3 层：JS 注入 —— 劫持 `fetch`/`XHR` + 扫描 `<video>` 标签
- **M3U8 验证** —— 异步检查流地址有效性
- **HLS 播放** —— 基于 hls.js，优雅降级
- **嗅探结果播放** —— 点击嗅探到的视频弹出独立播放器窗口
- **反检测** —— UA 伪装、`navigator.webdriver` 隐藏、Referer 自动填充

### 🎬 FFmpeg 媒体套件

- 视频编码检测（HEVC/杜比视界 → H.264 转码）
- 自动首帧缩略图提取
- **圆形视频消息**（Telegram 风格，静音/自动循环播放）
- **字幕系统** —— 提取内嵌字幕（WebVTT）+ 上传外部 `.srt`/`.vtt`/`.ass`
- 自定义视频播放器，支持进度条拖拽、倍速（0.25x-16x）、全屏控件、**音量/字幕/进度/速度全持久化**
- 系统 FFmpeg 自动检测（不捆绑二进制，引导用户安装，无 LGPL 合规风险）

### 💬 丰富的消息能力

- 支持 Markdown 的文本消息（加粗、斜体、代码、引用块）
- 图片、视频、语音消息、GIF、贴纸、任意格式文件
- **引用回复**、**转发**（跨房间）、**编辑**、**删除**（仅自己/双方）、**置顶**
- **消息表情反应**、**已读状态**（✓/✓✓）、**定时发送**
- **贴纸**（内置 2 套贴纸包、14 款手绘 SVG，点击选择器即时发送）
- **搜索**（单聊或全局）、**消息跳转**带高亮动画
- 多图/多文件批量发送、**拖拽发送**
- 全屏图片查看器，支持缩放（25%–500%）、平移、旋转、下载

---

## 🚀 快速开始

### 下载安装

| 平台                       | 安装包                                                                                                                                               | 说明                                                                 |
| -------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------- |
| **Windows x64**            | [📥 Setup.exe](https://github.com/samjoeyang/unobox-release/releases/latest)                                                                         | 双击安装，SmartScreen 提示时选择"更多信息 → 仍要运行"                |
| **macOS（Apple Silicon）** | [📥 DMG](https://github.com/samjoeyang/unobox-release/releases/latest)                                                                               | 首次打开若提示"无法验证"：前往**系统设置 → 隐私与安全性 → 仍要打开** |
| **Linux x64**              | [📥 AppImage](https://github.com/samjoeyang/unobox-release/releases/latest) / [📦 deb](https://github.com/samjoeyang/unobox-release/releases/latest) | AppImage 需 `chmod +x` 后运行；deb 用 `sudo dpkg -i` 安装            |

> 完整安装指南（含图文）请访问 [unobox.zhenzhidaole.com/usage.html](https://unobox.zhenzhidaole.com/usage.html)

### 🛠️ 自建 WebSocket 服务端（一行命令）

```bash
# 方式 1：docker compose（推荐）
docker compose up -d

# 方式 2：直接拉取镜像
docker run -d -p 8080:8080 ghcr.io/samjoeyang/unobox-ws-server:latest
```

服务端启动后，在 unobox 客户端中选择 **WebSocket 模式**，填入 `ws://<服务器IP>:8080` 即可连接。

> 需要先安装 [Docker](https://docs.docker.com/get-docker/)。服务端默认监听 8080 端口，可通过 `docker-compose.yml` 修改。

### 快速配置（3 种模式）

**模式 1：🔌 WebSocket 局域网（团队推荐）**

1. 在一台机器上选择「服务器模式」→ 设置端口和密码 → 启动
2. 其他人选择「客户端模式」→ 输入 `ws://[主机IP]:8080` + 密码 → 连接

**模式 2：🌐 Matrix 联邦**

1. 输入你的 Homeserver 地址（如 `https://matrix.example.com`、自建 Synapse 地址，或确认本机网络可解析的公共 Matrix 地址）
2. 使用用户名+密码或 Access Token 登录
3. 创建会话时选择「普通对话 / 普通房间 / 加密对话 / 加密房间」
4. 开始跨 Matrix 宇宙聊天

> Matrix 添加服务器会默认填入 `https://matrix.org` 便于快速体验；如果 DNS/网络不可达，请改成可访问的自建或公共 Homeserver。Matrix 加密会话采用房间级 `m.room.encryption`；加密房间创建后不可降级为普通房间。

**模式 3：💾 本地存储**

- 无需网络，无需服务器。点击「连接」即可开始。
- 所有数据保存在本地 SQLite 中。非常适合笔记、草稿或测试。

---

## 🎯 为什么选择 unobox？

### vs. 其他通讯软件

| 功能                | unobox                                                          | Telegram        | Signal    | Matrix/Element | Rocket.Chat |
| ------------------- | --------------------------------------------------------------- | --------------- | --------- | -------------- | ----------- |
| 自建/离线           | ✅ 本地+WS+Matrix                                               | ❌ 仅云端       | ❌ 仅云端 | ✅ 自建        | ✅ 自建     |
| 无需服务器          | ✅ 本地模式                                                     | ❌              | ❌        | ❌             | ❌          |
| 内置 AI 模型        | ✅ 8个模型                                                      | ❌ 仅通过机器人 | ❌        | ❌             | ❌ 插件     |
| TTS 语音合成        | ✅ 13 引擎                                                      | ❌              | ❌        | ❌             | ❌          |
| 电子书/有声书       | ✅ EPUB + 朗读                                                  | ❌              | ❌        | ❌             | ❌          |
| 文件预览            | ✅ 内置                                                         | ✅ 基础         | ❌        | ❌ 基础        | ❌ 插件     |
| 内置浏览器+视频嗅探 | ✅                                                              | ❌              | ❌        | ❌             | ❌          |
| 机器人框架          | ✅                                                              | ✅ 完整         | ❌        | ✅ 完整        | ✅ 完整     |
| 应用内反馈/Issue    | ✅ 一键提交                                                     | ❌              | ❌        | ❌             | ❌          |
| 语音/视频通话       | ⏳ 计划                                                         | ✅              | ✅        | ✅             | ✅          |
| 端到端加密          | ✅ 三种协议                                                     | ❌ 自定义       | ✅ 默认   | ✅ 可选        | ⏳ 插件     |
| 移动端 App          | ✅ 功能完整（Paper 主题 / 文件夹 / 投票/Bot/频道统计/全局搜索） | ✅              | ✅        | ✅             | ✅          |

---

## 🏗️ 架构设计

```
unobox/
├── apps/
│   ├── desktop/       # Electron 32 + React 18 + TypeScript（主客户端）
│   └── mobile/        # Expo 54 + React Native（本地功能完整：Paper 主题/文件夹/投票/Bot/频道统计/搜索）
├── packages/
│   ├── core/          # 共享 TypeScript（类型、接口、工具函数）
│   ├── ui-web/        # Web UI 组件库
│   └── ui-mobile/     # 移动端 UI 组件库
├── backend/
│   └── ws-server/     # 内置 WebSocket 服务器（Node.js）
└── web/               # 官方网站（静态）
```

### 服务商体系

```
        ┌─────────────────┐
        │ ProviderManager │
        └────────┬────────┘
                 │
     ┌───────────┼───────────┐
     │           │           │
 ┌───▼───┐  ┌───▼───┐  ┌───▼───┐
 │Local  │  │WS     │  │Matrix │
 │SQLite │  │WS Svr │  │Synapse│
 └───────┘  └───────┘  └───────┘
     │           │           │
 ┌───┴────┐ ┌───┴────┐ ┌───┴────┐
 │离线    │ │局域网  │ │联邦    │
 │个人使用│ │团队私有│ │全球互联│
 └────────┘ └────────┘ └────────┘
```

---

## 🗺️ 开发路线

### 短期（v0.3.x）

- [x] 移动端本地聊天功能完整闭环（投票/Bot/频道统计/定时消息/慢速模式/文件夹/Paper 主题）
- [x] 部署级 E2EE 加密策略开关（none/optional/mandatory）
- [ ] 移动端 WebSocket / Matrix 模式迁移
- [x] 本地存储模式的端到端加密
- [ ] 移动端原生 Dev Client + E2EE 支持
- [ ] macOS 代码签名（消除 Gatekeeper 警告）
- [ ] 通讯录与用户资料系统
- [ ] 开源核心包（packages/core, LocalProvider）

### 中期（v0.3.x）

- [ ] WebRTC 语音/视频通话（P2P，集成在聊天界面）
- [ ] 表情包及包管理器
- [ ] 图片编辑器（裁剪、涂鸦、文字叠加）
- [ ] 联系人列表，包含搜索和个人资料页
- [x] WebSocket 服务器一键 Docker 部署
- [x] Matrix 端到端加密支持

### 长期

- [ ] PWA 网页客户端（轻量浏览器版本）
- [ ] 多用户服务器管理后台
- [ ] 插件市场
- [ ] unobox 实例之间的联邦功能

---

## 📝 更新日志

查看 [完整更新日志](https://unobox.zhenzhidaole.com/changelog.html)。

**v0.3.5**（2026-07-13）—— 移动端功能完整闭环 + i18n 增强 + @提及/搜索/多选

- **移动端功能完整**：Phase 1-7 聊天功能全部完成，包括投票/评论/定时消息/慢速模式/已读状态/频道统计/文件管理/全局搜索/Bot 管理
- **移动端 UI 重构**：Paper 主题迁移 + UI 全面优化 + 文件夹管理 + 新建功能
- **国际化增强**：语言设置「系统跟随」选项，翻译键从 949 条扩至 1669 条，批量修复 536 条劣质翻译

**v0.2.1**（2026-06-13）—— 反馈问题 + 赞赏菜单 + TTS 增强

- **反馈问题**：应用内直接提交 Bug 报告/功能建议到 GitHub Issues，自动附带环境信息
- **赞赏支持**：从关于页面提升为设置主菜单独立项
- **Bug 修复**：TTS 文件句柄释放、字幕显示完整性、播放进度持久化

**v0.2.0**（2026-06-07）—— TTS 语音合成 + 有声书 + 播放器 UI 重设计

- **TTS 语音合成**：13 引擎（4 本地 + 9 云端），Sherpa-ONNX/Kokoro 主力引擎
- **有声书**：EPUB → TTS 逐句朗读 + 高亮 + 自动翻页 + 跨章节连续播放 + 断点续听
- **有声书导出**：批量合成 → FFmpeg 拼接 → 导出 WAV/MP3
- **播放器 UI 重设计**：底部抽屉 + 浮动按钮 + 字幕横滚 + 调速/快进/定时关闭

**v0.1.0**（2026-05-07）—— 首次公开发布

- 核心消息、群组、频道、机器人、AI 集成
- 文件预览、EPUB 阅读器、视频播放器、内置浏览器
- 3 种服务商类型（本地、WebSocket、Matrix）
- 支持 Windows / macOS / Linux

---

## 💡 背后的故事

> unobox 由**一个人**在约 **20 天**内构建完成，过程中大量借助了多个 AI 代理（Claude、Gemini、DeepSeek、Qwen 等）的帮助。
>
> 这个项目最初只是一个实验：_"AI 能帮助独立开发者构建一个生产级的即时通讯应用吗？"_
>
> 答案证明是**可以**——而 unobox 就是成果。每一行代码都经过了审查、测试和打磨。AI 负责脚手架，人类负责架构设计和关键决策。这种组合带来的迭代速度，让 unobox 作为一个单人项目成为可能。

---

## ☕ 赞赏支持

unobox 是一款完全免费、无广告的独立开发作品。如果你觉得它对你有帮助，欢迎赞赏支持开发者持续维护和迭代。

所有赞赏均为用户自愿行为，不附带任何商业承诺或特殊权益。

<p align="center">
  <img src="web/assets/wepay.JPG" alt="微信赞赏码" width="200">
  &nbsp;&nbsp;&nbsp;&nbsp;
  <img src="web/assets/alipay.JPG" alt="支付宝收款码" width="200">
</p>
<p align="center"><sub>微信支付 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 支付宝</sub></p>

---

## 🤝 社区

我们才刚刚开始！欢迎加入：

- 🐛 **问题反馈与功能建议** —— 应用内 **设置 → 反馈问题** 一键提交，或 [GitHub Issues](https://github.com/samjoeyang/unobox-release/issues)
- 💬 **Discord** —— _即将上线_
- ⭐ **Star 支持** —— 如果觉得有帮助，欢迎点亮右上角的 Star

---

## ⚠️ 已知限制

| 问题             | 状态                                                                                                                                    |
| ---------------- | --------------------------------------------------------------------------------------------------------------------------------------- |
| 移动端功能覆盖   | ✅ 本地聊天功能完整（群组/频道/消息/投票/Bot/频道统计/定时消息/慢速模式/文件夹/Paper 主题）；WebSocket / Matrix / E2EE / 推送仍在迁移中 |
| 移动端 E2EE      | 🚧 Expo Go + Hermes 暂不支持 libsodium WebAssembly，后续通过原生 Dev Client 启用                                                        |
| macOS 应用未签名 | 📋 即将修复 [[Gatekeeper 临时方案]](https://unobox.zhenzhidaole.com/usage.html#macos)                                                   |
| 无语音/视频通话  | 📋 计划中                                                                                                                               |
| 部分源码未公开   | 📋 核心包即将开源                                                                                                                       |
| 无联系人管理界面 | 📋 计划中                                                                                                                               |

---

---

<p align="center">
  <strong>如果 unobox 对你有帮助，请给一个 ⭐ Star</strong><br>
  <sub>这不仅是对独立开发者的鼓励，也能让更多人发现这个项目。</sub>
</p>

<p align="center">
  <a href="https://github.com/samjoeyang/unobox">⭐ 去 GitHub 给个 Star</a>
</p>

---

❤️ 由一个人和几个 AI 共同打造。

[🌐 官方网站](https://unobox.zhenzhidaole.com) ·
[📦 版本发布](https://github.com/samjoeyang/unobox-release/releases) ·
[🇬🇧 English](unobox-release-readme.md)
