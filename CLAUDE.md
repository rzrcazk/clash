# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## 项目概述

这是一个 OpenClash 网络代理配置集合项目，专为路由器和设备的网络代理设置而设计。项目提供从简单到企业级的完整配置模板，包含精细化域名分流规则和多种预配置策略组。

## 核心架构模式

### 分层配置架构
- **基础模板层**: 根目录的 .ini 配置文件（Clash-Mini.ini → Clash-Enterprise.ini）
- **规则文件层**: list/ 目录下按服务类型分类的域名规则
- **策略组层**: 表情符号 + 服务名的可视化策略组命名
- **设备适配层**: main_router/ 和 second_router/ 的多设备配置

### 智能分流策略
项目采用服务类型优先的分流逻辑：
- AI 服务 (ChatGPT, Claude, Gemini) → 美国节点优化
- 流媒体服务 → 地区特定节点
- 游戏服务 → 低延迟节点选择
- 国内服务 → 直连或香港节点

## 关键目录结构

```
/
├── Clash-*.ini          # 不同复杂度的配置模板
├── config.yaml          # 完整 Clash 核心配置
├── list/                # 分类域名规则集合
│   ├── AI.list          # AI 服务专用规则
│   ├── Media.list       # 流媒体服务规则
│   └── ...
├── main_router/         # 主路由器 OpenClash 配置
├── second_router/       # 副路由器配置
└── proxy/              # 代理服务商适配模板
```

## 规则编写规范

### 优先级顺序
1. DOMAIN（精确域名匹配）- 最高优先级
2. DOMAIN-SUFFIX（域名后缀匹配）
3. DOMAIN-KEYWORD（域名关键字匹配）
4. IP-CIDR（IP 段匹配）
5. GEOIP（地理位置匹配）- 最低优先级

### 最佳实践
- 优先使用精确的 DOMAIN 和 DOMAIN-SUFFIX 规则
- 避免过度宽泛的 DOMAIN-KEYWORD 规则
- 新增规则时考虑性能影响和匹配准确性

## 配置模板说明

### 推荐配置选择
- **日常使用**: Clash-Full.ini
- **轻量设备**: Clash-Mini.ini
- **企业环境**: Clash-Enterprise.ini
- **性能优先**: Clash-General.ini

### 特殊优化配置
- **AI 服务优化**: 针对 ChatGPT、Claude、Gemini 等服务的专门路由优化
- **流媒体优化**: Netflix、Disney+、YouTube 等平台的地区节点智能选择
- **游戏优化**: 低延迟节点选择和连接稳定性优化

## 开发和维护指南

### 规则更新流程
1. 在对应的 list/*.list 文件中添加新规则
2. 验证规则语法和匹配准确性
3. 考虑对现有规则的影响和冲突
4. 更新相关配置模板中的策略组引用

### 性能考虑
- 根据设备性能选择合适的配置复杂度
- 避免规则冗余和重复匹配
- 定期清理无效或过时的规则

### 策略组命名规范
- 使用表情符号增强可视化识别
- 按服务类型分组（🤖 AI、📺 媒体、🎮 游戏等）
- 保持命名一致性和层次清晰

## 特殊注意事项

### AI 服务配置
项目对 AI 服务进行了特别优化，包括：
- ChatGPT、Claude、Gemini 等主流 AI 平台的完整域名覆盖
- 美国西海岸节点优先选择以获得最佳访问体验
- API 和 Web 界面的分别优化配置

### 地理位置策略
- 流媒体服务按内容版权地区智能分流
- 国内服务优先直连或使用香港节点
- 特定服务的地区节点固定策略

### 多设备部署
- main_router/ 适用于主路由器的完整功能配置
- second_router/ 适用于副路由器的简化配置
- proxy/ 目录提供不同代理服务商的适配模板

## 常用命令和操作

### 配置文件验证
```bash
# 验证 YAML 配置文件语法
python -c "import yaml; yaml.safe_load(open('config.yaml'))"

# 使用 clash 验证配置文件 (如果安装了 clash)
clash -t -f config.yaml

# 验证 .ini 配置文件的 URL 可达性
curl -I "https://git.yylx.win/raw.githubusercontent.com/liandu2024/clash/refs/heads/main/list/AI.list"
```

### 规则文件管理
```bash
# 查看所有规则文件
ls -la list/

# 统计规则数量
wc -l list/*.list

# 搜索特定域名规则
grep -r "openai.com" list/

# 验证规则语法格式
grep -E "^(DOMAIN|DOMAIN-SUFFIX|DOMAIN-KEYWORD|IP-CIDR)" list/AI.list
```

### 配置模板切换
```bash
# 比较不同配置文件的差异
diff Clash-Full.ini Clash-LIAN.ini

# 查看配置模板的策略组数量
grep -c "custom_proxy_group" Clash-*.ini
```

### OpenClash 路由器配置管理
```bash
# 检查路由器配置文件
cat main_router/openclash | grep -E "(name|address|template_url)"

# 替换订阅地址
sed -i 's/【订阅地址复制并覆盖这里】/YOUR_SUBSCRIPTION_URL/g' main_router/openclash
```

## 配置调试和故障排除

### 连接测试命令
```bash
# 测试代理连接 (需要 curl 支持 proxy)
curl -x 127.0.0.1:7890 -I https://www.google.com

# 测试特定服务可达性
curl -x 127.0.0.1:7890 https://api.openai.com/v1/models

# DNS 解析测试
nslookup chatgpt.com 223.5.5.5
```

### 规则匹配验证
```bash
# 验证域名匹配规则
echo "chatgpt.com" | grep -f list/AI.list

# 检查规则冲突 (查找重复规则)
sort list/*.list | uniq -d

# 统计各类规则数量
grep -c "^DOMAIN," list/AI.list
grep -c "^DOMAIN-SUFFIX," list/AI.list
```

### 性能监控
```bash
# 监控配置文件大小
du -sh Clash-*.ini

# 检查外部规则源状态
for url in $(grep "https://" Clash-Full.ini | cut -d',' -f2); do
  echo "Testing: $url"
  curl -I --connect-timeout 10 "$url"
done
```

## 文件结构深度解析

### 配置文件层次关系
```
配置复杂度: Clash-Enterprise.ini > Cash-All.ini > Clash-Full.ini > Clash-LIAN.ini > Clash-mini.ini
规则数量:   最多                > 完整       > 全功能        > 精简         > 最少
性能要求:   最高                > 高         > 中等          > 低           > 最低
```

### 核心文件功能映射
- **config.yaml**: 完整 Clash 核心配置 (proxy-providers + proxy-groups + rules)
- **claw.yaml**: 简化的直连代理配置 (用于基础连接测试)
- **list/*.list**: 分类域名规则集 (按服务类型精细分组)
- **proxy/*.ini**: 代理服务商专用配置模板

### IPv6 配置支持
- **Clash-Full-IPv6.ini**: 完整功能 + IPv6 双栈支持
- **clash-mini-IPv6.ini**: 轻量级 + IPv6 双栈支持
- **Clash-LIAN-IPv6.ini**: 精简版 + IPv6 双栈支持