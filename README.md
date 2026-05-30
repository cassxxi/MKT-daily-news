# 🌍 MKT Daily News | 全球品牌营销日报

自动化的全球品牌与广告营销行业新闻摘要服务。每天早上9点，从全球顶级营销媒体、中国本土优质内容平台及社交媒体实时监测，收集最新的品牌营销新闻、社交媒体趋势、品牌营销方案和创意案例，支持中英双语，整理成个性化摘要发送到多个用户邮箱。

**Automated global brand and advertising marketing news digest service. Every morning at 9 AM, collect from top global marketing media, Chinese content platforms, and social media real-time monitoring. Supports Chinese-English bilingual, personalized summaries sent to multiple users.**

---

## 🚀 完整系统已部署

所有核心文件已在 `setup/automated-daily-digest` 分支中准备完毕：

✅ **配置文件**
- `config/news-sources.json` - 25+ 信息源配置（全球 + 中国）
- `config/users.yml` - 多用户订阅管理

✅ **脚本文件**
- `scripts/collect_news.py` - 智能新闻采集（去重 + 排序）
- `scripts/send_emails.py` - 多用户邮件发送

✅ **工作流**
- `.github/workflows/daily-news-digest.yml` - GitHub Actions 自动化

✅ **文档**
- `README.md` - 完整使用文档
- `requirements.txt` - Python 依赖

---

## ⚙️ 必需配置步骤

完成以下步骤来激活自动化日报系统：

### 1️⃣ 添加 GitHub Secrets

访问仓库设置：`Settings` → `Secrets and variables` → `Actions`

添加这 4 个 Secrets：

```
SMTP_SERVER = smtp.gmail.com
SMTP_PORT = 465
SENDER_EMAIL = your-email@gmail.com
SENDER_PASSWORD = [Gmail 应用专用密码]
```

**Gmail 用户获取应用密码步骤：**
1. 访问 https://myaccount.google.com/security
2. 启用 2-Step Verification（两步验证）
3. 生成 App Password（选择 Mail）
4. 复制 16 位密码

### 2️⃣ 合并 PR 将文件合并到主分支

从 `setup/automated-daily-digest` 分支创建 Pull Request，审查后合并。

### 3️⃣ 可选：自定义配置

- 编辑 `config/users.yml` 添加其他用户邮箱
- 编辑 `config/news-sources.json` 调整信息源

---

## 📰 信息源覆盖

### 全球顶级媒体（10+ 个）
AdWeek · Digiday · Marketing Dive · Social Media Today · The Drum · Campaign Live · eMarketer · Ad Age · Brandweek · Marketing Week

### 中国优质平台（7+ 个）
数英 · 品牌星球 · 鸟哥笔记 · 36氪 · 微博热搜 · 抖音创作者 · 小红书

### 社交媒体官方（6+ 个）
LinkedIn · Facebook · Twitter/X · TikTok · Instagram · Google Marketing

---

## 📊 核心功能

✅ **自动化** - 每天早上9点准时发送  
✅ **中英双语** - 完整支持中英文内容  
✅ **多用户** - 支持无限用户，个性化推送  
✅ **智能排序** - 综合考虑时间、分类、优先级  
✅ **去重** - MD5精确匹配 + 相似度比对  
✅ **分类** - 10个营销行业维度  
✅ **美观** - HTML格式，移动端友好  

---

## 🔗 快速链接

- 📝 **完整文档** - 见下方详细内容
- 🐛 **问题报告** - GitHub Issues
- 💬 **讨论交流** - GitHub Discussions

---

## 📋 完整文档

### 📑 新闻分类

| 类别 | 图标 | 说明 |
|------|------|------|
| 广告 | 📢 | 广告创意、广告投放、广告趋势 |
| 营销策划 | 📊 | 营销活动、营销策略、营销研究 |
| 数字营销 | 💻 | 数字营销、SEO、SEM 等 |
| 营销创意 | 🎨 | 创意广告、营销创新 |
| 社交媒体 | 📱 | 社交媒体趋势、平台新闻 |
| 品牌 | 🏆 | 品牌案例、品牌策略 |
| 移动营销 | 📲 | 移动端营销、APP 营销 |
| 品牌活动 | 🎯 | 品牌活动、营销方案 |
| 流行趋势 | 📈 | 行业趋势、热点话题 |
| 创意灵感 | 💡 | 创意案例、设计灵感 |

### 📧 邮件格式

每封邮件包含：
- 个性化问候 (Hi {姓名})
- 统计数据（精选资讯数、语言版本数）
- 最多 10 条精选新闻
- 每条新闻包括：序号、分类、语言标签、标题、摘要、来源、阅读链接
- 响应式设计，完美适配移动端

### 🛠️ 配置说明

#### `config/news-sources.json`

```json
{
  "sources": [
    {
      "name": "来源名称",
      "url": "网站地址",
      "feed_url": "RSS Feed地址",
      "category": "分类",
      "language": "en/zh",
      "priority": 1,
      "region": "global/china"
    }
  ],
  "settings": {
    "max_news_per_day": 10,
    "similar_content_threshold": 0.75
  }
}
```

#### `config/users.yml`

```yaml
users:
  - id: 1
    name: "Clarisse"
    email: "isclarisse.to@gmail.com"
    language_preference: "both"  # en/zh/both
    categories:
      - advertising
      - marketing
      - brand
      - social-media
    regions:
      - china
      - global
    enabled: true
```

### 📊 排序算法

```
总分 = (时间权重 × 0.4) + (分类权重 × 0.4) + (优先级 × 0.2)
```

- **时间权重**：72小时衰减，最近最高
- **分类权重**：0.8~1.0，根据重要性
- **优先级**：1级源 1.0 分，2级源 0.8 分

### 🔄 去重机制

1. **精确匹配**：MD5 哈希比对
2. **相似度**：SequenceMatcher > 75% 判定为重复

### 📝 本地测试

```bash
# 环境设置
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt

# 测试采集
python scripts/collect_news.py

# 测试发送（需设置环境变量）
export SMTP_SERVER=smtp.gmail.com
export SMTP_PORT=465
export SENDER_EMAIL=your-email@gmail.com
export SENDER_PASSWORD=your-password
python scripts/send_emails.py
```

### 🐛 故障排除

| 问题 | 解决方案 |
|------|--------|
| 邮件未送达 | 检查 Secrets 配置；Gmail 用户需用应用密码 |
| 工作流失败 | 查看 Actions 日志；验证 JSON/YAML 格式 |
| 新闻为空 | 检查新闻源 URL 可访问性 |
| 时间不对 | cron `0 1 * * *` = 北京时间早上9点 |

### 👥 多用户管理

**添加用户**：编辑 `config/users.yml`，添加新用户配置

**暂停用户**：设置 `enabled: false`

**修改偏好**：直接编辑用户配置

---

## 📚 依赖

- feedparser - RSS/Atom 解析
- requests - HTTP 请求
- python-dateutil - 日期处理
- pytz - 时区支持
- pyyaml - YAML 配置

---

## 📄 许可证

MIT License

---

## 💡 建议与反馈

- 📝 GitHub Issues - 问题报告和功能建议
- 💬 GitHub Discussions - 讨论交流
- 📧 isclarisse.to@gmail.com

---

**版本**: 1.0.0  
**最后更新**: 2024-05-30  
**维护者**: [@cassxxi](https://github.com/cassxxi)

Made with ❤️ for global marketing professionals
