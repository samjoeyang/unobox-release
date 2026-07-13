<div align="center">
 <br/>
 <img src="https://unobox.zhenzhidaole.com/assets/logo.png" alt="unobox" width="120"/>
 <br/>
 <h1>💬 unobox</h1>
 <p><strong>Your Data, Your Control. AI-Powered Private Messenger.</strong></p>

 <p>
 <a href="https://unobox.zhenzhidaole.com">
 <img src="https://img.shields.io/badge/官网-unobox.zhenzhidaole.com-3390ec?style=flat-square" alt="Website"/>
 </a>
 <a href="https://github.com/samjoeyang/unobox-release/releases/latest">
 <img src="https://img.shields.io/github/v/release/samjoeyang/unobox-release?style=flat-square&color=3390ec" alt="Release"/>
 </a>
 <a href="https://github.com/samjoeyang/unobox-release/releases/latest">
 <img src="https://img.shields.io/github/downloads/samjoeyang/unobox-release/total?style=flat-square&color=00d060" alt="Downloads"/>
 </a>
 <a href="https://unobox.zhenzhidaole.com/changelog.html">
 <img src="https://img.shields.io/badge/changelog-📋-3390ec?style=flat-square" alt="Changelog"/>
 </a>
 </p>

 <p>
 <a href="#-features">Features</a> •
 <a href="#-quick-start">Quick Start</a> •
 <a href="#-why-unobox">Why unobox</a> •
 <a href="#-architecture">Architecture</a> •
 <a href="#-roadmap">Roadmap</a>
 </p>

 <br/>
</div>

---

**unobox** is a Telegram-style private instant messaging app for **Windows, macOS, and Linux**. It gives you full control over your data — store everything locally or on your own server — while integrating 8 major AI models, a full-format file previewer, and a built-in browser with smart video sniffing.

> 🧪 Built by one person with AI assistance in ~20 days. A living proof of what's possible in the AI-augmented development era.

---

## ✨ Features

### 🛡️ Data Sovereignty

- **Local-first storage** using SQLite — data stays on your machine, fully offline
- **Self-hosted WebSocket server** for LAN/team communication — zero third-party access
- **Matrix federation** support — connect to any Matrix/Synapse server
- **Choice of 3 modes**: Local-only / WebSocket LAN / Matrix global

### 🎨 Telegram-Style UI

- High-fidelity 3-column layout with beautiful message bubbles
- Dark & light themes with adjustable font sizes
- **Groups** with member management, admin roles, announcements, slow mode
- **Channels** with subscriber management, post scheduling, stats dashboard
- **Topics** (Supergroup-style sub-rooms)
- **Polls** (single/multi choice, timers, real-time results)
- **Bot framework** with inline keyboards, webhooks, and built-in commands

### 🤖 8 AI Models Built-In

| Provider                            | Support                          |
| ----------------------------------- | -------------------------------- |
| OpenAI (GPT-4o, GPT-4, o3, etc.)    | ✅ Streaming                     |
| Anthropic Claude (Sonnet, Opus)     | ✅ Streaming + Extended Thinking |
| Google Gemini (Pro, Flash, 2.5 Pro) | ✅ Streaming                     |
| DeepSeek (V3, R1)                   | ✅ Reasoning content display     |
| OpenRouter (100+ models)            | ✅ All providers                 |
| Alibaba Qwen (QwQ-32B, Qwen-Plus)   | ✅                               |
| MiniMax                             | ✅                               |
| Custom OpenAI-compatible            | ✅                               |

- Real-time **streaming output** (token-by-token)
- **Thinking process visualization** for reasoning models
- **Persistent AI sessions** — survive app restarts
- Per-session model binding with full conversation history

### 📄 Full-Format File Preview

- **EPUB E-Books** — full reader: font size / line spacing / theme / CFI position memory / FTS5 full-text search / dark mode
- **Audiobook (EPUB → Speech)** — TTS sentence-by-sentence reading + active sentence highlight + auto page-turn, cross-chapter continuous playback
- **Audiobook Export** — batch synthesize all sentences in current chapter → FFmpeg concatenation → export as WAV / MP3 audio file
- **Word (.docx)** — rendered as HTML with theme-aware styling
- **Excel (.xlsx / .csv)** — multi-sheet table viewer
- **PDF** — page-by-page browsing
- **Markdown** — rendered inline
- **Office preview mode** — built-in or open in system app

### 🌐 Built-in Browser + Smart Video Sniffing

- Chat links open in an **independent browser window** with toolbar (back/forward/refresh/address bar)
- **3-layer video sniffing**:
- Layer 1: URL regex (`.mp4`, `.m3u8`, `.mpd`, `.flv`, `.webm`, etc.)
- Layer 2: Content-Type header inspection
- Layer 3: JS injection — hijacks `fetch`/`XHR` + scans `<video>` tags
- **M3U8 validation** — async checks stream validity
- **HLS playback** via hls.js with graceful fallback
- **Sniffed video playback** — one-click to open detected videos in standalone player window
- **Anti-detection** — UA spoofing, `navigator.webdriver` masking, Referer auto-fill

### 🎬 FFmpeg Media Suite

- Video codec detection (HEVC/Dolby Vision → H.264 transcode)
- Auto thumbnail extraction from first frame
- **Circular video notes** (Telegram-style, muted/autoPlay/loop)
- **Subtitle system** — extract embedded subtitles (WebVTT) + upload external `.srt`/`.vtt`/`.ass`
- Custom video player with draggable progress bar, speed control (0.25x-16x), fullscreen controls, **volume/subtitle/progress/speed full persistence**
- System FFmpeg auto-detection (no bundled binaries, guided install, zero LGPL compliance risk)

### 💬 Rich Messaging

- Text with Markdown (bold, italic, code, block quotes)
- Images, videos, voice messages, GIFs, files (any format)
- **Quote reply**, **forward** (cross-room), **edit**, **delete** (self/both), **pin**
- **Message reactions**, **read status** (✓/✓✓), **scheduled send**
- **Search** (per-chat or global), **message jumping** with highlight animation
- Multi-image & multi-file batch send, **drag-and-drop** to send
- Full-screen image viewer with zoom (25%–500%), pan, rotate, download

---

## 🚀 Quick Start

### Download

| Platform                     | Download                                                                                                                                                                                                                                 |
| ---------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 🪟 **Windows x64**           | [📥 unobox-Setup-x.x.x.exe](https://github.com/samjoeyang/unobox-release/releases/latest/download/unobox-Setup-0.1.0.exe)                                                                                                                |
| 🍎 **macOS (Apple Silicon)** | [📥 unobox-x.x.x-arm64.dmg](https://github.com/samjoeyang/unobox-release/releases/latest/download/unobox-0.1.0-arm64.dmg) or [📦 .zip](https://github.com/samjoeyang/unobox-release/releases/latest/download/unobox-0.1.0-arm64-mac.zip) |
| 🐧 **Linux x64**             | [📥 unobox-x.x.x.AppImage](https://github.com/samjoeyang/unobox-release/releases/latest/download/unobox-0.1.0.AppImage) or [📦 .deb](https://github.com/samjoeyang/unobox-release/releases/latest/download/unobox_0.1.0_amd64.deb)       |

> Full installation guide at [unobox.zhenzhidaole.com/usage.html](https://unobox.zhenzhidaole.com/usage.html)

### Quick Setup (3 Modes)

**Mode 1: 🔌 WebSocket LAN** (recommended for teams)

1. On one machine: select "Server Mode" → set port & password → Start
2. Others: "Client Mode" → enter `ws://[HOST_IP]:8080` + password → Connect

**Mode 2: 🌐 Matrix Federation**

1. Enter your Homeserver URL (e.g., `https://matrix.org`)
2. Log in with username + password or Access Token
3. Start chatting across the Matrix universe

**Mode 3: 💾 Local Storage**

- No network, no server needed. Just click "Connect" and go.
- All data stays in your local SQLite. Perfect for notes, drafts, or testing.

---

## 🎯 Why unobox?

### vs. Other Messengers

| Feature                            | **unobox**             | Telegram         | Signal        | Matrix/Element | Rocket.Chat  |
| ---------------------------------- | ---------------------- | ---------------- | ------------- | -------------- | ------------ |
| Self-host/Offline                  | ✅ Local + WS + Matrix | ❌ Cloud only    | ❌ Cloud only | ✅ Self-host   | ✅ Self-host |
| No server needed                   | ✅ Local mode          | ❌               | ❌            | ❌             | ❌           |
| AI models built-in                 | ✅ **8 models**        | ❌ Via bots only | ❌            | ❌             | ❌ Plugin    |
| File preview (Word/Excel/EPUB/PDF) | ✅ Built-in            | ✅ Basic         | ❌            | ❌ Basic       | ❌ Plugin    |
| Built-in browser + video sniff     | ✅                     | ❌               | ❌            | ❌             | ❌           |
| Bot framework                      | ✅                     | ✅ Full          | ❌            | ✅ Full        | ✅ Full      |
| Voice/video calls                  | ⏳ Planned             | ✅               | ✅            | ✅             | ✅           |
| E2E Encryption                     | ⏳ Planned             | ❌ Custom        | ✅ Default    | ✅ Optional    | ⏳ Plugin    |
| Mobile app                         | ⏳ WIP                 | ✅               | ✅            | ✅             | ✅           |

### Why Choose unobox?

1. **Privacy without compromise** — local-only mode needs zero cloud trust
2. **AI in your chat** — not a bot you have to configure, but a native AI interface with 8 providers
3. **All-in-one toolbox** — chat, browser, file previewer, video player, and AI assistant in one app
4. **Telegram familiarity** — if you love Telegram's UX but want your data back, this is for you
5. **Single dev, big ambition** — built with modern AI tools, iterating fast based on community feedback

---

## 🏗️ Architecture

```
unobox/
├── apps/
│ ├── desktop/ # Electron 32 + React 18 + TypeScript (main client)
│ │ ├── src/main/ # Electron main process
│ │ ├── src/preload/ # Context bridge
│ │ └── src/renderer/ # React UI (Zustand state)
│ └── mobile/ # Expo 52 + React Native (scaffolding)
├── packages/
│ ├── core/ # Shared TypeScript (types, interfaces, utils)
│ ├── ui-web/ # Web UI component library
│ └── ui-mobile/ # Mobile UI component library
├── backend/
│ └── ws-server/ # Built-in WebSocket server (Node.js)
└── web/ # Official website (static)
```

### Provider System (`IServerProvider`)

```
 ┌─────────────────┐
 │ ProviderManager │
 └────────┬────────┘
 │
 ┌──────────────────┼──────────────────┐
 │ │ │
 ┌──────▼──────┐ ┌──────▼──────┐ ┌──────▼──────┐
 │ LocalProv. │ │ WSProv. │ │MatrixProv. │
 │ (SQLite) │ │ (WebSocket) │ │ (Synapse) │
 └─────────────┘ └─────────────┘ └─────────────┘
 │ │ │
 ┌─────┴──────┐ ┌─────┴──────┐ ┌─────┴──────┐
 │ Offline │ │ LAN/Team │ │ Federation │
 │ Personal │ │ Private │ │ Global │
 └────────────┘ └────────────┘ └────────────┘
```

---

## 🗺️ Roadmap

### Short-term (v0.2.x)

- [ ] **Mobile MVP** (iOS + Android, WebSocket mode + AI)
- [ ] **E2E encryption** for local storage mode
- [ ] **Code signing** for macOS (remove Gatekeeper warning)
- [ ] **Contacts** & user profile system
- [ ] **Open-source core packages** (packages/core, LocalProvider)

### Medium-term (v0.3.x)

- [ ] **WebRTC voice/video calls** (P2P, integrated in chat UI)
- [ ] **Stickers** with pack manager
- [ ] **Image editor** (crop, draw, text overlay)
- [ ] **Contact list** with search and profile pages
- [ ] **Docker one-liner** for WebSocket server deployment
- [ ] Matrix E2EE support

### Long-term

- [ ] **PWA web client** (lightweight browser-based version)
- [ ] Multi-user server admin panel
- [ ] Plugin marketplace
- [ ] Federation between unobox instances

---

## 📝 Changelog

See [changelog](https://unobox.zhenzhidaole.com/changelog.html) for full release history.

**v0.2.0** (2026-06-07) — TTS Speech Synthesis + Audiobooks + Player UI Redesign

- **TTS Synthesizer**: 13 engines (4 local + 9 cloud), Sherpa-ONNX/Kokoro as primary engine
- **Audiobooks**: EPUB → TTS sentence reading + highlight + auto page-turn + cross-chapter + resume playback
- **Audiobook Export**: batch synthesize → FFmpeg concatenation → export WAV/MP3
- **Player UI Redesign**: bottom drawer + floating button + subtitle scroll + speed/skip/sleep timer

**v0.1.0** (2026-05-07) — First public release

- Core messaging, groups, channels, bots, AI integration
- File preview, EPUB reader, video player, built-in browser
- 3 provider types (Local, WebSocket, Matrix)
- Windows / macOS / Linux support

---

## 💡 The Story Behind unobox

> unobox was built by **one person** in **~20 days**, with heavy assistance from multiple AI agents (Claude, Gemini, DeepSeek, Qwen, and more).
>
> This project started as an experiment: _"Can AI help a solo developer build a production-quality messaging app?"_
>
> The answer turned out to be **yes** — and the result is unobox. Every line of code has been reviewed, tested, and polished. The AI wrote the scaffolding; the human wrote the architecture and made the calls. The speed of iteration that this combo enables is what makes unobox possible as a solo project.

---

## ☕ Support Development

unobox is completely free and ad-free, built by an independent developer. If it helps you, consider supporting continued maintenance and iteration.

All contributions are entirely voluntary and come with no commercial promises or special privileges.

<p align="center">
  <img src="web/assets/wepay.JPG" alt="WeChat Pay" width="200">
  &nbsp;&nbsp;&nbsp;&nbsp;
  <img src="web/assets/alipay.JPG" alt="Alipay" width="200">
</p>
<p align="center"><sub>WeChat Pay &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Alipay</sub></p>

---

## 🤝 Community

We're just getting started! Join us:

- 🐛 **Issues & Feature Requests** — [GitHub Issues](https://github.com/samjoeyang/unobox-release/issues)
- 💬 **Discord** — _coming soon_
- 📬 **Feedback** — Private, constructive, and brutally honest feedback is all welcome

---

## ⚠️ Known Limitations

| Issue                         | Status                                                                                      |
| ----------------------------- | ------------------------------------------------------------------------------------------- |
| No mobile app (yet)           | 🚧 Scaffolding stage                                                                        |
| No end-to-end encryption      | 📋 Planned                                                                                  |
| macOS app is not signed       | 📋 Will fix — see [Gatekeeper workaround](https://unobox.zhenzhidaole.com/usage.html#macos) |
| No voice/video calls          | 📋 Planned                                                                                  |
| Source code partially private | 📋 Core packages to be open-sourced                                                         |
| No contact management UI      | 📋 Planned                                                                                  |

---

<div align="center">
 <br/>
 <p>
 <sub>Made with ❤️ by one human and a few AIs.</sub>
 </p>
 <p>
 <a href="https://unobox.zhenzhidaole.com">🌐 Official Website</a> •
 <a href="https://github.com/samjoeyang/unobox-release/releases">📦 Releases</a>
 </p>
 <br/>
</div>
