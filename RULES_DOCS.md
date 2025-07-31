# Clash 规则列表说明文档

## 📋 概述

本文档详细说明 `list/` 目录下各种规则列表文件的用途、内容和维护方式。这些规则文件决定了不同网站和服务的流量路由方式。

## 🎯 规则语法说明

### 基本语法类型

```ini
# 域名完全匹配
DOMAIN,example.com

# 域名后缀匹配  
DOMAIN-SUFFIX,example.com

# 域名关键字匹配
DOMAIN-KEYWORD,example

# IP地址段匹配
IP-CIDR,192.168.1.0/24,no-resolve

# IP地址段匹配（IPv6）
IP-CIDR6,2001:db8::/32,no-resolve
```

### 匹配优先级

1. **DOMAIN** (最高优先级) - 精确域名匹配
2. **DOMAIN-SUFFIX** - 域名后缀匹配
3. **DOMAIN-KEYWORD** - 域名关键字匹配
4. **IP-CIDR** - IP段匹配
5. **GEOIP** (最低优先级) - 地理位置匹配

## 🤖 AI 服务规则

### 📝 AI.list - 主要AI服务

**覆盖服务**：
- OpenAI (ChatGPT)
- Anthropic (Claude) 
- Microsoft Copilot
- Bing AI

**规则示例**：
```ini
# OpenAI 相关域名
DOMAIN-SUFFIX,chatgpt.com
DOMAIN-SUFFIX,openai.com
DOMAIN-SUFFIX,oaistatic.com
DOMAIN-SUFFIX,oaiusercontent.com

# Anthropic Claude
DOMAIN-SUFFIX,anthropic.com
DOMAIN-SUFFIX,claude.ai

# Microsoft AI服务
DOMAIN,copilot.microsoft.com
DOMAIN-SUFFIX,bing.com
```

**更新频率**: 每周更新，跟随AI服务变化

### 🚀 AI2.list - 扩展AI服务

**覆盖服务**：
- Google Gemini
- Perplexity
- Meta AI
- 其他新兴AI服务

**特点**：
- 覆盖新兴AI平台
- 实验性服务规则
- 快速响应新服务

### 💬 ChatGPT.list - ChatGPT专用

**规则数量**: 16条  
**覆盖范围**：
```ini
# 核心服务
DOMAIN-KEYWORD,openai
DOMAIN-SUFFIX,openai.com
DOMAIN-SUFFIX,chatgpt.com

# 支持服务
DOMAIN-SUFFIX,auth0.com              # 身份验证
DOMAIN-SUFFIX,challenges.cloudflare.com  # Cloudflare验证
DOMAIN-SUFFIX,intercom.io            # 客服系统
DOMAIN-SUFFIX,statsigapi.net         # 数据统计
```

### 🤖 Claude.list - Claude专用

**特点**：
- Anthropic官方服务
- Claude Web界面
- API服务支持

### 💻 Copilot.list - GitHub Copilot

**覆盖范围**：
- GitHub Copilot服务
- VS Code集成
- 开发者工具支持

### 🔮 Gemini.list - Google Gemini

**覆盖服务**：
- Gemini Web界面
- Google AI服务
- Bard相关服务

### 🧠 MetaAi.list - Meta AI

**覆盖范围**：
- Meta AI助手
- Facebook AI集成
- Instagram AI功能

### 🔍 Perplexity.list - Perplexity搜索

**特点**：
- AI搜索引擎
- 实时信息查询
- 学术研究优化

## 🌐 网络分流规则

### 📡 Direct.list - 直连规则

**用途**: 确保国内服务直连访问

**主要内容**：
```ini
# 国内DNS服务
DOMAIN-SUFFIX,dns.alidns.com
DOMAIN-SUFFIX,doh.pub

# 国内常用服务
DOMAIN-KEYWORD,baidu
DOMAIN-SUFFIX,hao123.com
DOMAIN-SUFFIX,lanzov.com

# 系统服务
DOMAIN-SUFFIX,time.windows.com

# 特定IP段
IP-CIDR,219.146.1.66/32,no-resolve
IP-CIDR,219.147.1.66/32,no-resolve
```

**适用场景**：
- 防止国内服务误走代理
- 提高访问速度
- 减少代理负载

### 🚀 Proxy.list - 代理规则

**用途**: 需要代理访问的国外服务

**主要类别**：
- 被封锁的国外网站
- 受地理限制的服务
- 需要加速的国外服务

### 🔍 Check.list - 连接测试规则

**主要用途**: 网络连接状态检测

**包含服务**：
```ini
# 网速测试
DOMAIN-SUFFIX,speedtest.net
DOMAIN-SUFFIX,speedtest.cn
DOMAIN-SUFFIX,fast.com

# IP检测
DOMAIN-SUFFIX,test-ipv6.com
DOMAIN-SUFFIX,ipw.cn
DOMAIN-SUFFIX,whoer.net

# DNS检测
DOMAIN-SUFFIX,dnscheck.tools

# 隐私检测
DOMAIN-SUFFIX,browserleaks.com
DOMAIN-SUFFIX,browserleaks.org
```

**使用建议**: 定期测试确保代理配置正确

### 📥 Download.list - 下载优化规则

**用途**: 优化下载服务的路由

**覆盖服务**：
- 软件下载站点
- 系统更新服务
- 大文件传输服务

### 🔄 302.list - 重定向规则

**用途**: 处理重定向和跳转服务

**特点**：
- 防止重定向导致的规则失效
- 优化跳转链接处理
- 提高访问稳定性

## 🎬 媒体服务规则

### 🎞️ YouTube.list - YouTube专用

**覆盖范围**：
- YouTube主站服务
- YouTube Music
- YouTube TV
- 相关CDN服务

**优化特点**：
- 支持4K视频播放
- 优化缓冲体验
- 区域解锁支持

## 🛠️ 自定义规则

### 📋 自定义规则分类

| 文件名 | 用途 | 维护方式 |
|--------|------|----------|
| **gn01.list** | 个人自定义规则组1 | 用户维护 |
| **ww01.list** | 工作相关规则组1 | 用户维护 |
| **ww02.list** | 工作相关规则组2 | 用户维护 |
| **ww03.list** | 工作相关规则组3 | 用户维护 |
| **xnb.list** | 特殊需求规则组 | 用户维护 |

### 🔧 自定义规则编写指南

#### 1. 规则格式规范

```ini
# 注释说明规则用途
# 域名规则示例
DOMAIN-SUFFIX,example.com

# IP规则示例  
IP-CIDR,192.168.1.0/24,no-resolve

# 关键字规则示例
DOMAIN-KEYWORD,example
```

#### 2. 规则优化建议

- **精确匹配优先**: 优先使用 `DOMAIN` 而非 `DOMAIN-KEYWORD`
- **避免过度匹配**: 关键字规则要谨慎，避免误匹配
- **IP规则慎用**: 尽量使用域名规则，IP规则容易失效
- **添加注释**: 每个规则组都应有清晰的注释说明

#### 3. 测试验证

```bash
# 测试规则匹配
curl -x proxy_server:port target_url

# 检查DNS解析
nslookup target_domain

# 验证IP归属
whois target_ip
```

## 📊 规则维护策略

### 🔄 更新频率

| 规则类型 | 更新频率 | 触发条件 |
|----------|----------|----------|
| **AI服务** | 每周 | 新服务上线、域名变更 |
| **流媒体** | 每月 | CDN变更、地区调整 |
| **基础网络** | 每季度 | 网络环境变化 |
| **自定义** | 按需 | 用户需求变化 |

### 🧪 测试流程

1. **语法验证**: 检查规则语法正确性
2. **功能测试**: 验证规则匹配效果
3. **冲突检测**: 确保规则间无冲突
4. **性能测试**: 评估规则对性能的影响

### 📈 监控指标

- **匹配率**: 规则被正确匹配的比例
- **响应时间**: 规则处理耗时
- **错误率**: 规则匹配错误的比例
- **更新频率**: 规则更新的频次

## 🚨 故障排除

### 常见问题

#### 1. 规则不生效

**可能原因**：
- 规则语法错误
- 规则优先级冲突
- 缓存未清理

**解决方案**：
```bash
# 检查规则语法
grep -n "语法错误" rule.list

# 清理DNS缓存
ipconfig /flushdns

# 重启代理服务
systemctl restart clash
```

#### 2. 误匹配问题

**可能原因**：
- 关键字规则过于宽泛
- 域名规则覆盖范围过大

**解决方案**：
- 使用更精确的匹配规则
- 添加排除规则
- 调整规则顺序

#### 3. 性能问题

**可能原因**：
- 规则数量过多
- 复杂正则表达式
- 频繁的DNS查询

**优化方案**：
- 合并相似规则
- 优化规则顺序
- 使用域名规则替代IP规则

## 📚 规则库推荐

### 官方规则库

- **blackmatrix7**: 最全面的规则集合
- **Loyalsoldier**: 精简优化的规则
- **ACL4SSR**: 适合中国用户的规则

### 规则获取地址

```ini
# blackmatrix7 规则库
https://git.yylx.win/raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Clash/

# Loyalsoldier 规则库  
https://git.yylx.win/raw.githubusercontent.com/Loyalsoldier/clash-rules/release/

# 本项目规则库
https://git.yylx.win/raw.githubusercontent.com/liandu2024/clash/main/list/
```

## 🔒 安全注意事项

### 规则安全

- **验证规则来源**: 只使用可信的规则源
- **定期安全审查**: 检查规则中是否有恶意内容
- **备份重要规则**: 定期备份自定义规则

### 隐私保护

- **避免明文敏感信息**: 规则中不要包含敏感域名
- **使用安全的DNS**: 配置可信的DNS服务器
- **监控异常访问**: 留意异常的网络访问模式

---

📅 **最后更新**: 2025-01-30  
🔧 **规则版本**: v1.8  
📖 **贡献指南**: 参考项目 CONTRIBUTING.md