# Clash 项目文档索引

## 📋 项目概览

这是一个 OpenClash 网络代理配置集合项目，包含多种预配置的规则集和模板文件，主要用于路由器和设备的网络代理设置。

**项目特点**：
- 🎯 完整的代理规则分类（AI服务、流媒体、游戏、社交等）
- ⚙️ 多种配置模板适应不同使用场景
- 🌐 支持主副路由器部署
- 📱 优化的移动端和桌面端体验

## 📁 项目结构

```
clash/
├── 📄 配置文件 (.ini)
│   ├── Cash-All.ini          # 完整功能配置
│   ├── Clash-Dev.txt         # 开发版配置
│   ├── Clash-Full.ini        # 全功能版配置（推荐）
│   ├── Clash-LIAN.ini        # 精简版配置
│   ├── Clash-S01.ini         # 特殊版配置
│   └── Clash-mini.ini        # 迷你版配置
│
├── 📁 规则列表 (list/)
│   ├── AI相关
│   │   ├── AI.list           # 主要AI服务规则
│   │   ├── AI2.list          # 扩展AI服务规则
│   │   ├── ChatGPT.list      # ChatGPT专用规则
│   │   ├── Claude.list       # Claude专用规则
│   │   ├── Copilot.list      # GitHub Copilot规则
│   │   ├── Gemini.list       # Google Gemini规则
│   │   ├── MetaAi.list       # Meta AI规则
│   │   └── Perplexity.list   # Perplexity规则
│   │
│   ├── 流媒体服务
│   │   └── YouTube.list      # YouTube专用规则
│   │
│   ├── 网络分类
│   │   ├── Check.list        # 连接测试规则
│   │   ├── Direct.list       # 直连规则
│   │   ├── Download.list     # 下载专用规则
│   │   ├── Proxy.list        # 代理规则
│   │   └── 302.list         # 重定向规则
│   │
│   └── 自定义规则
│       ├── gn01.list        # 自定义规则组1
│       ├── ww01.list        # 自定义规则组2
│       ├── ww02.list        # 自定义规则组3
│       ├── ww03.list        # 自定义规则组4
│       └── xnb.list         # 自定义规则组5
│
├── 📁 路由器配置
│   ├── main_router/         # 主路由器配置
│   │   └── openclash        # OpenClash主路由配置
│   └── second_router/       # 副路由器配置
│       └── openclash        # OpenClash副路由配置
│
├── 📁 代理配置 (proxy/)
│   ├── clash-all.ini        # 代理版完整配置
│   ├── clash-full.ini       # 代理版全功能配置
│   ├── clash-lian.ini       # 代理版精简配置
│   ├── clash-mini.ini       # 代理版迷你配置
│   └── clash-test.ini       # 代理版测试配置
│
└── 📄 README.md             # 项目说明文档
```

## 🎯 主要功能分类

### 🤖 AI 服务支持
- **完整AI生态**：覆盖OpenAI、Claude、Gemini、Copilot等主流AI服务
- **专用优化**：每个AI服务都有专门的规则优化
- **智能分流**：AI1和AI2两套独立的AI服务规则组

### 🎮 娱乐媒体
- **流媒体**：YouTube、Netflix、Disney+、HBO Max、Spotify等
- **游戏平台**：Steam、Epic、EA、Blizzard、UBI、Sony、Nintendo
- **社交平台**：TikTok、Telegram、Twitter、Facebook

### 🌐 网络服务
- **云服务**：Amazon、Apple、Microsoft、GitHub
- **直连/代理**：智能分流国内外流量
- **下载优化**：专门的下载规则优化

## ⚙️ 配置文件说明

| 文件名 | 特点 | 适用场景 |
|--------|------|----------|
| **Clash-Full.ini** | 功能最全面，规则最完整 | 日常使用推荐 |
| **Clash-LIAN.ini** | 精简版，性能优化 | 低配置设备 |
| **Clash-mini.ini** | 最小化配置 | 临时使用 |
| **Cash-All.ini** | 完整功能版 | 高级用户 |
| **Clash-S01.ini** | 特殊场景版 | 特定需求 |

## 🔧 路由器部署

### 主路由器 (main_router/)
- 完整的订阅管理配置
- 多个代理服务商支持
- 详细的DNS配置
- 端口和模式设置

### 副路由器 (second_router/)
- 简化的配置文件
- 与主路由器协同工作
- 负载均衡支持

## 📋 规则列表分类

### 🤖 AI服务类
```
AI.list          # 主要AI服务（OpenAI、Anthropic等）
AI2.list         # 扩展AI服务
ChatGPT.list     # ChatGPT专用
Claude.list      # Claude专用
Copilot.list     # GitHub Copilot
Gemini.list      # Google Gemini
MetaAi.list      # Meta AI
Perplexity.list  # Perplexity搜索
```

### 🌐 网络分流类
```
Direct.list      # 国内直连规则
Proxy.list       # 国外代理规则
Check.list       # 连接测试规则
Download.list    # 下载优化规则
302.list         # 重定向处理规则
```

### 🎬 媒体服务类
```
YouTube.list     # YouTube视频服务
```

### 🎯 自定义类
```
gn01.list - xnb.list    # 用户自定义规则组
ww01.list - ww03.list   # 扩展自定义规则
```

## 🚀 快速开始

1. **选择配置文件**：推荐使用 `Clash-Full.ini` 作为基础配置
2. **路由器部署**：根据设备选择 `main_router` 或 `second_router` 配置
3. **自定义规则**：根据需要修改 `list/` 目录下的规则文件
4. **订阅设置**：在路由器配置文件中替换订阅地址

## 📖 相关文档

- [配置文件详细说明](CONFIG_DOCS.md)
- [规则列表说明](RULES_DOCS.md)
- [OpenClash配置教程](https://www.youtube.com/watch?v=S2l_0g4EOHk&t=2s)

## ⚠️ 注意事项

- 请确保订阅源稳定可靠
- 定期更新规则列表保持最佳效果
- 根据实际网络环境调整配置参数
- 遵守当地法律法规使用网络代理

---

📅 **最后更新**: 2025-01-30  
🔗 **项目地址**: https://github.com/liandu2024/clash