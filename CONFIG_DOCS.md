# Clash 配置文件详细说明

## 📋 概述

本文档详细说明各个配置文件的结构、功能和使用场景，帮助用户选择合适的配置并进行个性化定制。

## 🔧 配置文件架构

所有配置文件都采用 Clash 的 `.ini` 格式，主要包含两个核心部分：

1. **规则集定义** (`ruleset`): 定义流量分流规则
2. **策略组配置** (`custom_proxy_group`): 定义代理策略组

## 📁 配置文件对比

| 配置文件 | 规则数量 | 复杂度 | 内存占用 | 适用场景 |
|----------|----------|--------|----------|----------|
| **Clash-Full.ini** | 完整 | 高 | 较高 | 日常使用，功能全面 |
| **Clash-LIAN.ini** | 精简 | 中 | 中等 | 性能优化，稳定使用 |
| **Clash-mini.ini** | 最少 | 低 | 最低 | 临时使用，资源受限 |
| **Cash-All.ini** | 完整+ | 高 | 高 | 高级用户，全功能 |
| **Clash-S01.ini** | 特定 | 中 | 中等 | 特殊需求场景 |

## 📄 详细配置说明

### 🎯 Clash-Full.ini (推荐配置)

**特点**: 最完整的功能配置，适合大多数用户

#### 规则集结构

```ini
;1、域名组
ruleset=✨ AI1,https://git.yylx.win/raw.githubusercontent.com/liandu2024/clash/refs/heads/main/list/AI.list
ruleset=✨ AI2,https://git.yylx.win/raw.githubusercontent.com/liandu2024/clash/refs/heads/main/list/AI2.list
ruleset=📘 GitHub,https://git.yylx.win/raw.githubusercontent.com/blackmatrix7/ios_rule_script/refs/heads/master/rule/Clash/GitHub/GitHub.list
```

#### 分类覆盖范围

**🤖 AI服务分类**
- `✨ AI1` - 主要AI服务（OpenAI、Claude等）
- `✨ AI2` - 扩展AI服务（Gemini、Perplexity等）

**💻 开发工具分类**
- `📘 GitHub` - GitHub代码托管服务
- `Ⓜ️ Microsoft` - 微软系列服务
- `🍎 Apple` - 苹果生态服务

**🎮 游戏娱乐分类**
- `🎮 Steam` - Steam游戏平台
- `🕹️ Game` - 综合游戏平台（Epic、EA、Blizzard等）
- `🎞️ YouTube` - YouTube视频服务

**📺 流媒体分类**
- `🎥 Netflix` - Netflix流媒体
- `📺 Disney` - Disney+服务
- `🎬 HBO MAX` - HBO Max服务
- `🎵 Spotify` - Spotify音乐服务

**🌐 网络分流**
- `🌍 国外` - 国外网站代理规则
- `➡️ 国内` - 国内网站直连规则

#### 策略组配置

```ini
;2、策略组（域名组-节点组）
custom_proxy_group=✨ AI1`select`[]DIRECT`[]所有-手动`[]所有-自动`[]港台日新韩-自动`[]台日新韩-自动`[]香港-自动`[]台湾-自动`[]日本-自动`[]新加坡-自动`[]韩国-自动`[]美国-自动`[]其他-自动`[]REJECT
```

**策略组类型说明**：
- `select` - 手动选择策略
- `[]DIRECT` - 直连选项
- `[]所有-手动` - 手动选择所有节点
- `[]所有-自动` - 自动选择最优节点
- `[]地区-自动` - 按地区自动选择
- `[]REJECT` - 拒绝连接

### 🔧 Clash-LIAN.ini (精简配置)

**特点**: 性能优化版本，减少不必要的规则

**优化内容**：
- 合并相似规则组
- 精简策略组选项
- 优化规则匹配顺序
- 减少内存占用

**适用场景**：
- 路由器配置受限
- 追求稳定性能
- 不需要复杂分流规则

### 📱 Clash-mini.ini (迷你配置)

**特点**: 最小化配置，核心功能保留

**精简策略**：
- 仅保留基础分流规则
- 简化策略组结构
- 最低资源占用
- 快速启动加载

**适用场景**：
- 临时使用需求
- 低配置设备
- 测试环境部署

### 🏢 Cash-All.ini (企业配置)

**特点**: 企业级全功能配置

**增强功能**：
- 更详细的规则分类
- 更多的策略组选项
- 企业服务优化规则
- 高级安全设置

### 🎯 Clash-S01.ini (特殊配置)

**特点**: 针对特殊需求定制

**应用场景**：
- 特定地区优化
- 特殊网络环境
- 自定义规则需求

## ⚙️ 策略组详解

### 节点选择策略

```ini
# 手动选择组
custom_proxy_group=服务名`select`[选项列表]

# 自动选择组  
custom_proxy_group=服务名`url-test`[节点列表]`[测试URL]`[间隔时间]

# 负载均衡组
custom_proxy_group=服务名`load-balance`[节点列表]`[测试URL]`[间隔时间]
```

### 地区节点分组

**🇭🇰 香港节点** (`[]香港-自动`)
- 适合：流媒体服务、游戏加速
- 特点：延迟低、稳定性好

**🇯🇵 日本节点** (`[]日本-自动`)  
- 适合：Netflix日区、游戏服务
- 特点：内容丰富、速度快

**🇺🇸 美国节点** (`[]美国-自动`)
- 适合：ChatGPT、YouTube Premium
- 特点：解锁能力强、选择多

**🇸🇬 新加坡节点** (`[]新加坡-自动`)
- 适合：东南亚服务、稳定连接
- 特点：地理位置优势

## 🔗 外部规则源

### 官方规则源

```ini
# blackmatrix7 规则集（推荐）
https://git.yylx.win/raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Clash/[服务名]/[服务名].list

# 本项目规则集
https://git.yylx.win/raw.githubusercontent.com/liandu2024/clash/refs/heads/main/list/[规则名].list
```

### 规则更新策略

- **自动更新**: 配置文件支持自动更新规则
- **手动更新**: 可手动触发规则更新
- **缓存机制**: 本地缓存减少网络请求

## 🎛️ 高级配置选项

### DNS 配置

```ini
# DNS 服务器配置
dns:
  enable: true
  listen: 0.0.0.0:53
  enhanced-mode: fake-ip
  nameserver:
    - 223.5.5.5
    - 119.29.29.29
  fallback:
    - 8.8.8.8
    - 1.1.1.1
```

### 端口配置

```ini
# 代理端口设置
port: 7890          # HTTP 代理端口
socks-port: 7891    # SOCKS5 代理端口
mixed-port: 7893    # 混合代理端口
```

### 模式配置

```ini
# 运行模式
mode: rule          # 规则模式
allow-lan: true     # 允许局域网连接
log-level: info     # 日志级别
```

## 🔍 故障排除

### 常见问题

1. **规则不生效**
   - 检查规则源是否可访问
   - 验证规则语法正确性
   - 确认策略组配置匹配

2. **节点连接失败**
   - 检查节点有效性
   - 验证端口配置
   - 确认防火墙设置

3. **速度较慢**
   - 优化节点选择策略
   - 调整超时参数
   - 考虑使用精简配置

### 调试技巧

```bash
# 查看实时日志
tail -f /var/log/clash.log

# 测试规则匹配
curl -x proxy_address:port target_url

# 验证配置文件
clash -t -f config.yaml
```

## 📊 性能优化建议

### 内存优化
- 选择合适的配置文件规模
- 定期清理无用规则
- 合理配置缓存大小

### 网络优化
- 选择地理位置近的节点
- 配置合适的超时时间
- 使用负载均衡策略

### 稳定性优化
- 配置多个备用节点
- 设置健康检查
- 启用自动故障转移

---

📅 **最后更新**: 2025-01-30  
🔄 **配置版本**: v2.4  
📞 **技术支持**: 参考项目 Issues 页面