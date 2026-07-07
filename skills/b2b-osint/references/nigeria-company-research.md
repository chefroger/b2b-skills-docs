# Nigeria Company OSINT — Reference Notes

## CAC (Corporate Affairs Commission) — Official Registry

- **官网**: https://cac.gov.ng/services/company-search
- **公墓搜索**: https://icrp.cac.gov.ng/public-search
- CAC 是尼日利亚公司注册的唯一官方机构，所有合法公司都必须在 CAC 登记。
- 尼日利亚公司注册号格式：**RC 123456**（RC = Registration Certificate）
- RC 编号规律：编号越小（以"30万"开头），注册时间越早（1990年代）
- CAC 记录可查：注册号、公司名、注册地址、董事信息、成立日期、当前状态

## 关键第三方查询平台（绕过 Cloudflare 拦截）

| 平台 | 用途 | 地址 |
|------|------|------|
| **ng-check.com** | CAC 记录摘要，含注册号/日期/地址/状态 | https://ng-check.com/[company-slug] |
| **nigeria24.me** | 公司信息、董事、联系人（含 Cloudflare 防护） | https://nigeria24.me/[company-slug] |
| **addresshistoryafrica.com** | 尼日利亚地址历史（含曾用名/曾注册公司） | https://www.addresshistoryafrica.com/NG/ |
| **icpcredit.com** | 信用报告（付费，最后更新日期可判断活跃度） | 直接搜索公司名 |
| **B2BHint** | 尼日利亚公司数据库 | https://b2bhint.com/ng/ |

## 地址核验技巧

- 搜索地址时加 "site:addresshistoryafrica.com" 查历史
- 45 Tejuosho Road, Yaba, Lagos 是宗教/商业混合区，曾有多个不同公司注册于此
- 如果注册地址与用户提供地址不一致 → 红旗（可能是空壳公司或地址出租）

## 搜索 Query 模板（Yahoo/Bing，非 Google）

```
# 公司基础信息（去掉 PTY/LTD/PLC 等后缀）
"{Company Name}" Nigeria limited RC number registration
"{Company Name}" Nigeria limited RC number registration {year}

# 地址核实
"{Company Name}" {具体地址片段}
"{Address}" Nigeria {company_type}

# 制裁检查
"{Company Name}" Nigeria sanctions OFAC terrorist

# EFCC 诈骗名单
site:businesselitesafrica.com EFCC companies scams Nigeria 2025
```

## 制裁名单检查顺序

1. **OFAC** (美国): https://sanctionssearch.ofac.treas.gov
2. **UN** (联合国): OpenSanctions 搜索
3. **EU** (欧盟): OpenSanctions 搜索
4. **Nigeria Nigsac**: https://nigsac.gov.ng
5. **EFCC 诈骗名单** (2025年3月): 58家未授权投资平台，名单发布于 businesselitesafrica.com

## 红旗判定标准（Nigerian Companies）

| 红旗 | 阈值 |
|------|------|
| 地址不一致 | 注册地址与运营地址不匹配 |
| 极弱数字足迹 | 注册10年以上但无官网/无社媒/无新闻 |
| 状态"unknown" | CAC 记录显示状态未知，可能已注销 |
| 个人邮箱 | 使用 Gmail/Yahoo/Hotmail 而非企业邮箱 |
| 无 CAC 记录 | RC 编号无法在 CAC 系统核实 |
| 地址为住宅/宗教 | 商业公司地址在非商业区 |

## 注册年限判断

- RC 编号 30万~40万区间 → 1990年代中期注册
- RC 编号 50万~80万区间 → 2000年代
- RC 编号 100万+ → 2010年代后

## 重要教训（本次背调 [Prospect Company] 得出）

1. **Google 被 Cloudflare 拦截** → 改用 Yahoo/Bing/DuckDuckGo
2. **ng-check.com 可能被拦截** → 多次尝试或换用 Yahoo search snippet 数据
3. **地址是两个红旗的交汇点**: (a) CAC 注册地址可能已过时；(b) 用户提供的地址如果是"PLOT 46"格式，要注意尼日利亚地址格式规范（Plot No. 后是门牌号，不是门牌号是 Plot）
4. **29年老公司 + 零数字足迹 = 异常组合** → 可能已停业，或仅做线下贸易
