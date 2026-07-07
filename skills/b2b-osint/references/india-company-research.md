# 印度公司 OSINT 调研参考

## 关键发现（2026-05-22 [Prospect Company] Group 案例）

### 大型集团/上市公司研究框架

印度大型企业集团（如 TATA、[Prospect Company]、Reliance、Adani、Bharti）与小型私营公司有本质区别：
- **上市公司** → NSE/BSE 上市，合规透明，制裁风险极低
- **上市公司子公司** → 可能独立上市（如 [Prospect Company] Steel、[Prospect Company] Energy）
- 研究这类公司时，评估维度需调整（偏重市场地位、财务实力、国际布局）

### 印度公司必查信息来源

| 平台 | 用途 | 地址 |
|------|------|------|
| **NSE India** | 上市公司股票信息、营收、公司治理 | https://www.nseindia.com/ |
| **BSE India** | 孟买证券交易所，上市公司数据 | https://www.bseindia.com/ |
| ** Zaubacorp** | 印度公司董事/注册信息免费汇总 | https://www.zaubacorp.com/ |
| **Tofler** | 印度公司账务/董事/注册详细信息 | https://www.tofler.in/ |
| **Insightbk** | 印度公司数据 | https://www.insightbk.com/ |
| **Wikipedia** | 大型集团有独立词条，含历史/子公司/关键人 | https://en.wikipedia.org/wiki/{CompanyName} |

### WHOIS 查询要点（.in 域名）

- `.in` 域名 WHOIS 数据通过 IANA 注册商提供
- 典型注册商：GoDaddy (Wild West Domains)、NameCheap、BigRock
- 注册人通常为集团核心子公司（如 `[Prospect Company] Steel Ltd. - Corporate Office`）
- 域名注册年限 ≥ 15 年 = 信用良好标志
- 注册人国家为 `IN` = 印度本土注册

### Google 被拦截时的降级方案

当 Google 显示 "请求被阻止" 页面时：
1. 改用 **DuckDuckGo**：`https://duckduckgo.com/?q={query}`
2. 改用 **Bing**：`https://www.bing.com/search?q={query}`
3. 直接访问目标网站首页（通常不过滤）

### 制裁检查降级方案

OFAC Sanctions Search 网站（https://sanctionssearch.ofac.treas.gov/）可能临时不可用：
- **降级方案 1**：`web_search("site:ofac.treas.gov {公司名}")`
- **降级方案 2**：`web_search("{公司名} sanctions OFAC SDN 2024 2025")`
- **降级方案 3**：OpenSanctions 聚合搜索 `https://www.opensanctions.org/search/?q={公司名}`

### 大型印度集团红旗判定

| 红旗类型 | 阈值 | 备注 |
|----------|------|------|
| 上市公司 | — | 公开上市 = 合规透明度高 = 低风险 |
| 子公司 NSE/BSE 上市 | — | 多了一层监管，风险更低 |
| 营收规模 | >$1B | 通常无制裁风险 |
| 员工规模 | >10,000 | 抗风险能力强 |
| 域名年龄 | ≥15年 | 长期运营信用标志 |
| 关键人为政界人士兄弟 | ⚠️ 注意 | 需评估政治关联风险（如 BJP 议员 Naveen Jindal 为 [Prospect Company] 创始人兄弟） |

### 印度集团搜索 Query 模板

```bash
# 公司基础信息
"{Company Name}" India conglomerate founder CEO Sajjan Jindal
"{Company Name}" India Wikipedia company profile subsidiaries
"{Company Name}" India NSE BSE stock revenue

# 域名注册
"{Company Name}.in" WHOIS registered since
site:whois.com "{Company Name}.in"

# 制裁检查
"{Company Name}" India sanctions OFAC SDN
"{Company Name}" India blacklisted banned

# 关键人核查
"{Chairman Name}" India billionaire Net Worth
"{Chairman Name}" India political affiliation BJP Congress
```

### 关键人背景调查

印度大型集团关键人（Sajjan Jindal 案例）：
- 父亲是已故政治家/商人 Om Prakash Jindal
- 兄弟 Naveen Jindal 是 BJP 人民党议员（与执政党关系良好）
- 曾任世界钢铁协会（World Steel Association）主席
- 妻子 Sangita Jindal 运营家族慈善基金会

### 上市公司财务数据快速获取

通过 NSE/BSE 上市公司页面可直接获取：
- 股价（实时）
- 营收（年度/季度）
- 产能数据
- 员工规模

这些数据来自官网首页 Banner，无需注册即可查看。

### 本次 [Prospect Company] 背调关键结论

1. **低风险客户**：$23B 营收 + 37,000 员工 + 上市公司背景 + 无制裁记录
2. **域名21年**：[prospect company].in 2005年注册，信用充分
3. **注册人为集团核心子公司**（[Prospect Company] Steel Ltd. Corporate Office）
4. **制裁筛查**：无 OFAC/UN/EU/UK 命中记录
5. **行动建议**：可推进业务合作
