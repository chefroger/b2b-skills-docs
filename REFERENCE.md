# B2B Skills 完整参考文档

> 每个 Skill 的详细技术规范、参数说明、模板、检查清单

---

## 目录

- [1. b2b-onboarding — 新公司部署](#1-b2bonboarding--新公司部署)
- [2. b2b-lead-generation — 客户开发与开发信](#2-b2blead-generation--客户开发与开发信)
- [3. b2b-osint — 客户背景调查](#3-b2bosint--客户背景调查)
- [4. b2b-email-intel — 邮箱情报](#4-b2bemail-intel--邮箱情报)
- [5. b2b-customs-data — 海关数据分析](#5-b2bcustoms-data--海关数据分析)
- [6. b2b-cold-outreach — 冷 outreach 邮件](#6-b2bcold-outreach--冷-outreach-邮件)
- [7. b2b-linkedin-marketing — LinkedIn 营销](#7-b2blinkedin-marketing--linkedin-营销)
- [8. b2b-social-media — 多平台社媒营销](#8-b2bsocial-media--多平台社媒营销)
- [9. b2b-platform — B2B 平台诊断](#9-b2bplatform--b2b-平台诊断)
- [10. b2b-customer-mgmt — 客户管理](#10-b2bcustomer-mgmt--客户管理)
- [11. b2b-data-directory — 数据目录管理](#11-b2bdata-directory--数据目录管理)
- [12. b2b-document — 文档分析](#12-b2bdocument--文档分析)
- [13. b2b-doc-generation — 文档生成](#13-b2bdoc-generation--文档生成)
- [14. b2b-trade-ops — 运营沟通](#14-b2btrade-ops--运营沟通)
- [15. b2b-trade-compliance — 外贸合规](#15-b2btrade-compliance--外贸合规)
- [16. b2b-daily-automation — 每日自动化](#16-b2bdaily-automation--每日自动化)
- [17. b2b-skill-generator — 自定义 Skill 生成](#17-b2bskill-generator--自定义-skill-生成)

---

## 1. b2b-onboarding — 新公司部署

### 概述
引导新用户/新公司从零搭建完整的外贸业务体系。

### 触发词
- 新手部署
- 新公司上线
- 全套营销方案
- 从零开始
- new company setup
- full marketing plan

### 输入要求
按顺序引导用户提供（一次 1-2 个）：
1. 公司名称和成立时间
2. 主要产品/服务（最好提供产品资料文件）
3. 目标市场（哪些国家/地区）
4. 核心竞争优势（价格/质量/交期/服务）
5. 现有营销渠道（平台/展会/Direct）

### 输出清单
| 交付物 | 格式 | 说明 |
|--------|------|------|
| 公司介绍文档 | .docx | 中英文各一份 |
| 产品介绍文档 | .docx | 按产品线分类 |
| 目标客户画像 | .md | 3 个典型客户类型 |
| 竞争对手分析 | .docx | 3-5 个主要竞争者 |
| 差异化策略 | .docx | 关键差异点 + 话术 |
| LinkedIn 设置指南 | .docx | Profile + 公司页 + 内容日历 |
| 社媒月历 | .xlsx | 月度内容计划 |
| B2B 平台优化方案 | .docx | 产品 listing 优化 |
| 邮件模板 | .docx | 开发信 + 跟进序列 |

### 7 天行动计划
| 天 | 任务 |
|----|------|
| Day 1 | 完成公司介绍 + 产品目录 |
| Day 2 | 优化 LinkedIn Profile |
| Day 3 | 发布第一条 LinkedIn 帖子 |
| Day 4 | 制定社媒月历 |
| Day 5 | 开始客户搜索 |
| Day 6 | 发送第一批开发信 |
| Day 7 | 复盘 + 调整策略 |

### 30 天里程碑
- 第 1 周：基础搭建完成
- 第 2 周：首批客户搜索 + 背调
- 第 3 周：首批发信 + LinkedIn 内容积累
- 第 4 周：询盘跟进 + 报价生成

### 注意事项
- 不提供具体数据时用定性表述（"超过 X 年"）
- 所有文档单一语言，不混用
- 内容必须可执行，不留占位符

---

## 2. b2b-lead-generation — 客户开发与开发信

### 概述
外贸 B2B 客户开发的核心 Skill，覆盖从找客户到成交的全流程。

### 触发词
- 找客户 / 找潜客 / 找买家
- 写开发信 / 产品推广信
- 客户分析 / 报价 / 谈判
- find prospects / development letter
- inquiry handling / price negotiation

### 核心能力矩阵

| 能力 | 说明 | 关联 Skill |
|------|------|-----------|
| 三通道搜索 | Google Maps + Google Search + FB/LinkedIn | b2b-osint |
| 客户分级 | A（高价值）/ B（中等）/ C（潜力） | b2b-customer-mgmt |
| 开发信撰写 | 痛点先行型 + 价值先行型 A/B 变体 | b2b-cold-outreach |
| 多语言邮件 | 阿拉伯语/西班牙语/德语/日语等 | b2b-trade-compliance |
| 跟进序列 | Day 1/3/7/14/30 | — |
| 报价生成 | PI 模板 + 价格谈判 3 步法 | b2b-doc-generation |
| 询盘处理 | 30 分钟回复规则 | b2b-customer-mgmt |
| 样品管理 | 全流程模板（请求→寄送→跟进→转化） | b2b-trade-ops |

### 三通道搜索详解

**通道 A — Google Maps**（本地分销商/批发商）
- Query：`{product} distributor in {country/city}`
- 适合：有实体店/仓库的本地买家
- 决策快、订单稳定

**通道 B — Google Search**（B2B 买家站点）
- Query：`{product} buyer OR importer OR purchasing {country}`
- 适合：品牌方/工厂/连锁超市采购负责人

**通道 C — Facebook/LinkedIn**（活跃在线买家）
- Query：`site:linkedin.com/company {product} {country}`
- 适合：中小买家（FB）+ 中大型企业（LinkedIn）

**去重规则**：
- 域名级去重（同一域名只保留信息最全的一条）
- 优先级：命中 3 通道 > 命中 2 通道 > 命中 1 通道但信息完整

**黑名单**：
- 平台目录页（alibaba.com/made-in-china.com）
- 聚合页（yellowpages.com/yelp.com）
- 竞争对手
- 政府机构（.gov/.edu）
- 死链（404/503）
- 占位页（Wix/Squarespace 模板页）

### 开发信写作规则

**内容比例**：
- 60% 客户痛点 + 解决方案
- 25% 工厂/产品硬实力
- 15% CTA

**主题行策略**：
- A — 个性化引用：`[Company] | [Pain Point Solution]`
- B — 提问引发好奇：`Quick question about [their specific challenge]`
- C — 关联触发事件：`Following up on [trigger event]`
- D — 价值先行：`[Benefit] for [Company]`

**反营销腔自检**（每封邮件必须通过）：
1. 第一句讲客户还是讲自己？→ 必须是客户
2. 60% 篇幅讲痛点还是讲产品？→ 必须痛点为主
3. 有没有具体到这个客户独有的细节？→ 必须有
4. 删掉公司名是否适用任何同行？→ 不适用才合格
5. 客户 5 秒内能否感受"这封信和我有关"？→ 能

**SPAM 触发词**（禁止使用）：
FREE / Guaranteed / No obligation / 100% / Winner / Limited time / Act now / Urgent / Best price / Lowest price / Million / Cash bonus / Extra income

### 跟进序列

| 天数 | 动作 | 渠道 | 内容 |
|------|------|------|------|
| Day 1 | 首次 outreach | Email | 开发信 |
| Day 3 | 轻提醒 | Email | "making sure it didn't get buried" |
| Day 7 | 换角度 | LinkedIn | Connection Note / InMail |
| Day 14 | 新信息 | Email | "Quick question: ..." |
| Day 30 | 分手信 | Email | "Last note from me 👋" |

### 客户类型与策略

| 类型 | 决策速度 | 订单规模 | 策略 |
|------|---------|---------|------|
| 零售商/小批发商 | 快（天-周） | 小 | 快速响应、灵活 MOQ |
| 贸易公司/中间商 | 中（周-月） | 中 | 找决策人、留佣金空间 |
| OEM/品牌买家 | 慢（月-年） | 大 | 展示研发/认证能力 |
| 连锁超市/大卖场 | 很慢（6-18月） | 很大 | 持久战、准备审计 |

### 质量检查清单（发送前 60 秒）

**开发信**：
- [ ] 提到客户网站/动态的具体细节？
- [ ] 标题不超过 8 个词？
- [ ] 60/25/15 比例？
- [ ] 3-5 个主题行变体？

**报价函**：
- [ ] 有效期？
- [ ] 贸易术语（FOB/CIF/EXW）+ 地点？
- [ ] 包装方式？
- [ ] MOQ？
- [ ] 付款条件？
- [ ] 报价单号唯一可追溯？

---

## 3. b2b-osint — 客户背景调查

### 概述
三阶段客户尽职调查，输出结构化背调报告。

### 触发词
- 背调 / 尽职调查 / 背景调查
- 查公司 / 查域名 / 风险评估
- due diligence / background check
- company research

### 三阶段流程

**Phase 1: 信息发现**（最多 6 轮搜索）
1. 搜索 `"{Company Name} official website"`
2. 根据结果状态决策：
   - 找到官网+LinkedIn → 直接进入 Phase 2
   - 找到官网无 LinkedIn → 搜索关键人
   - 只有零散信息 → 换角度搜地址/电话/邮箱
   - 无结果 → 输出"零数字足迹"，评分 0-30

**Phase 2: 信息提取**
- 访问官网关键页面（首页/Contact/About/Team）
- 访问 LinkedIn 公司页
- 提取：公司名、官网、邮箱、关键人、国家/城市
- **关键联系人富化**（必做）：
  - 目标角色优先级：CEO/Founder → Purchasing Manager → Import Manager → Supply Chain Manager
  - 结构化字段：name/title/email/LinkedIn/WhatsApp/phone/decision_maker
  - 邮箱推测：Hunter.io + 模式匹配 + 验证
  - **双跑验证**：WebFetch + WebSearch 交叉确认

**Phase 3: 深度验证**
- 邮箱背景调查（120+ 平台）
- 企业邮箱 vs 个人邮箱判断
- WHOIS 域名查询
- 技术栈检测
- 制裁筛查
- LinkedIn 验证
- 综合风险评分

### 输出格式

```
## 公司概况
| 项目 | 内容 | 来源 |
|------|------|------|

## 关键联系人详表
### 联系人 1: [姓名] — [职位]
| 字段 | 值 | 验证状态 |

## 采购偏好
| 字段 | 推断值 | 依据 |

## 邮箱背景调查
| 平台 | 注册 | 用户名 | 档案URL |

## 综合风险评级
评级 [低/中/高] | 分数 X/100 | 红旗列表

## 行动建议
1. [具体可执行的下一步]
```

### 溯源铁律
- 每条结论必须标注来源 URL
- 区分「读到的」和「推断的」
- 搜索不到就说搜索不到
- Web Search snippet 不是可靠来源，关键信息必须访问原始页面确认

---

## 4. b2b-email-intel — 邮箱情报

### 概述
静默邮箱背景调查，检测 120+ 平台注册情况。

### 触发词
- 查邮箱 / email intel / 邮箱调查
- email background check / verify email

### 输入
单个邮箱地址（格式：xxx@domain.com）

### 输出
```
### ✅ 已找到的注册账号
| 平台 | 账号 | 公开档案 |
|------|------|---------|

### ⚠️ 受限平台
| 平台 | 状态 |

### ❌ 未注册的知名平台
| 平台 |

### 📋 汇总分析
- 真实性评估：高/中/低
- 客户画像：技术型/商务型/混合型
- 风险提示
```

### 适用场景
| 场景 | 价值 |
|------|------|
| 收到陌生客户询盘 | 验证真实性 |
| 开发信发送前 | 预判客户画像 |
| 怀疑虚假询盘 | 发现低可信信号 |
| 初次接触前 | 发现社交档案，准备针对性开场 |

### 技术实现
- 使用 holehe 开源工具
- 注册接口探测 + 密码找回泄露 + Gravatar 头像
- **不发送任何邮件**，完全静默

---

## 5. b2b-customs-data — 海关数据分析

### 概述
分析海关进出口数据，识别目标采购商和竞品。

### 触发词
- 海关数据 / 进出口数据 / 找采购商
- customs data / import export data
- HS code analysis

### 前置条件
数据文件放置在 `~/.trade/<公司名>/海关数据/` 目录下，格式为 CSV 或 XLSX。

### 分析维度
| 维度 | 说明 |
|------|------|
| 采购商分析 | TOP10 买家，购买频率，价格敏感度 |
| 供应商分析 | 主要竞争者市场份额 |
| 市场趋势 | 近 N 个月进口量变化 |
| 价格区间 | CIF/FOB 价格分布 |
| 目标客户优先级 | A 级（高频率大批量）/ B 级 / C 级 |

### 过滤规则
1. 排除超出业务范围的产品
2. 按目标地理区域筛选
3. 排除一次性买家（无 repeat 潜力）
4. 排除低于 MOQ 的订单
5. 优先制造商/品牌方/大型分销商

### 优先级评分矩阵
| 标准 | 权重 | 评分 |
|------|------|------|
| 行业匹配度 | 25% | 1-5 |
| 体积潜力 | 25% | 1-5 |
| 地理契合度 | 20% | 1-5 |
| 可触达性 | 15% | 1-5 |
| 增长趋势 | 15% | 1-5 |

### 输出
- P1（Hot）：24h 内联系
- P2（Warm）：1 周内联系
- P3（Medium）：培育序列
- P4（Low）：定期检查

---

## 6. b2b-cold-outreach — 冷 outreach 邮件

### 概述
基于公司产品数据和历史报价，生成个性化的 B2B 冷 outreach 邮件。

### 触发词
- 开发信 / 产品推广信 / 跟进信
- cold email / promotion letter
- development letter / follow-up

### 语言策略
| 目标市场 | 语言 |
|---------|------|
| 欧美/澳洲/东南亚 | 英语 |
| 中东 | 英语（商务标准） |
| 拉美 | 西班牙语/葡萄牙语 |
| 越南/泰国 | 英语（B2B 首选） |

### 邮件类型

**开发信（首次接触）**：
```
Subject: [Product Category] from [Company] — [Key Differentiator]
Dear [Title/Name],
[Intro: 你是谁 + 怎么找到他 + 相关性]
[Product: 核心产品 + 具体型号]
[Why Us: 3-5 个具体优势]
[Social Proof: 区域经验 + 认证]
[CTA: 下一步]
```

**产品推广信**：
```
Subject: [Specific Product] — [Benefit/Price Point] from [Company]
[Context: 引用具体项目/标准/需求]
[Product: 具体型号 + 规格]
[Value: 解决什么问题]
[Offer: 样品/试单/折扣]
```

**跟进信**：
```
Subject: Re: [Original Subject] / Following up on [Product]
[Reference previous contact]
[New information: 价格更新/新产品/认证/产能]
[Soft CTA]
```

### 常见产品类别速查
| 类别 | 示例 | 关键参数 |
|------|------|---------|
| 预绞丝耐张线夹 | NL series, GG series | 导线尺寸/材质/抗拉强度 |
| 悬垂线夹 | CLCS series, XG series | 电压等级/导线类型 |
| 防震锤 | FD, FFH series | 档距/导线直径 |
| 间隔棒 | FJZ series | 分裂配置/间距 |
| 接地线夹 | ALM, STG series | 导线截面 |
| 并沟线夹 | APG, CAPG series | 电缆尺寸范围 |
| 光缆金具 | OPGW clamp | 电缆直径/张力等级 |

---

## 7. b2b-linkedin-marketing — LinkedIn 营销

### 概述
LinkedIn 个人品牌 + 公司主页 + 内容营销全流程。

### 触发词
- LinkedIn / 领英 / LinkedIn 营销
- Profile optimization / LinkedIn content
- InMail / connection request

### Profile 优化

**Headline 公式**：
`[Job Title] | [Core Value Proposition] | [Industry/Product]`

**About 结构**：
```
[HOOK — 1-2 句解决客户痛点]
[BACKGROUND — 资历背书]
[WHAT YOU OFFER — 3 个核心服务 + 利益]
[CTA — 联系方式]
```

### 内容日历（每周）
| 内容类型 | 比例 | 说明 |
|---------|------|------|
| 客户痛点洞察 | 25% | 行业难题 + 你的解决方案 |
| 成功案例故事 | 20% | 帮客户解决了什么 + 创造价值 |
| 差异化服务展示 | 20% | 独到服务 + 工厂硬实力 |
| 产品应用场景 | 15% | 真实使用场景，不讲参数 |
| 互动讨论 | 15% | 引导评论 |
| 客户背书 | 5% | 推荐信/好评 |

### 开发信模板

**Connection Request（≤300 字符）**：
```
Hi [Name], saw your post about [pain point].
I help [industry] buyers solve [specific problem].
Open to connecting?
```

**Follow-Up（Day 3-5）**：
- 提及连接后的具体价值
- 用数据说话（不编造）
- 15 分钟通话 CTA

**InMail**：
- 主题行：`[Their company] + supply chain idea`
- 参考客户具体行业挑战
- 分享经验，不推销

---

## 8. b2b-social-media — 多平台社媒营销

### 概述
Facebook/Instagram/TikTok/YouTube 四平台差异化内容策略。

### 触发词
- Facebook / Instagram / TikTok / YouTube
- 社媒 / 社交媒体 / 发帖计划
- social media strategy / content calendar

### 内容配比
| 内容方向 | 比例 | 说明 |
|---------|------|------|
| 帮客户避坑 + 解决方案 | 30% | 采购陷阱/验货盲区/认证雷区 |
| 差异化服务展示 | 20% | 48h 打样/非标定制/实验室检测 |
| 工厂硬实力 + 产品力 | 20% | 产线实拍/检测流程/工艺细节 |
| 客户成功故事 | 15% | 帮客户解决棘手问题 |
| 互动 + 行业话题 | 15% | 投票/提问/讨论 |

### 平台差异化

**Facebook**：
- B2B 长文/案例分析/行业洞察
- Group 运营
- 最佳时间：8-10 AM, 2-4 PM

**Instagram**：
- 工厂纪实/品质瞬间/客户故事
- Reels 产品展示
- Stories 日常幕后
- 最佳时间：11 AM-1 PM, 7-9 PM

**TikTok**：
- 采购冷知识/行业避坑/工厂日常
- 视频结构：0-2s Hook → 2-5s Intro → 5-30s 主体 → 30-45s 价值 → 45-60s CTA
- 频率：1-3 条/天

**YouTube**：
- 客户案例纪录片/品质管控全流程
- 行业趋势/采购指南
- 固定上传时间

### 竞品分析模板
```
Competitor: [账号名]
Followers: [数量]
Posting Frequency: [条/周]
Content Types: [视频/图片/文章比例]
What They Do Well: [具体帖子]
What They Don't Do: [你的机会]
```

---

## 9. b2b-platform — B2B 平台诊断

### 概述
诊断和优化 B2B 平台店铺（Alibaba/独立站/Amazon 等）。

### 触发词
- 平台诊断 / 店铺诊断 / 网站优化
- platform audit / store diagnosis
- Alibaba optimization / independent site

### 五维度分析

| 维度 | 检查项 |
|------|--------|
| 产品标题 | 关键词覆盖/移动端友好度/专业性 |
| 产品图片 | 数量(3-6+)/质量/工厂/证书展示 |
| 产品描述 | 结构化程度/关键词密度/卖点清晰度 |
| 关键词 | 排名词覆盖/长尾词布局 |
| 询盘转化 | 主图/视频/交易保障因素 |

### 标题优化规则
1. 前 30 字符最重要 — 放核心关键词
2. 包含产品类型
3. 加关键规格（材料/尺寸/型号）
4. 包含买家意图词（manufacturer/wholesale）
5. 不超过 3-5 个关键词
6. 不要堆砌

### 竞品对标
```
Competitor: [公司名]
URL: [链接]
Titles: [他们的标题]
Images: [数量 + 质量 1-5]
Descriptions: [长度 + 结构]
Pricing: [可见范围]
Certifications: [展示的证书]
Strengths to Borrow: [可借鉴的战术]
```

### 优先级行动
- P1 Critical（本周）：修复致命问题
- P2 Important（本月）：优化排名因素
- P3 Nice to Have（本季）：提升体验

---

## 10. b2b-customer-mgmt — 客户管理

### 概述
客户档案全生命周期管理。

### 触发词
- 客户列表 / 客户详情 / 客户分级
- 订单跟踪 / 导入客户 / 报价管理
- customer list / customer details / import customers

### 客户分级

| 级别 | 标准 | 服务级别 | 联系频率 |
|------|------|---------|---------|
| A - 重点 | 收入前 20%/战略重要性 | 最高 | 每周至少 1 次 |
| B - 常规 | 稳定订单/关系良好 | 标准 | 每两周 1 次 |
| C - 培育 | 成长潜力/偶尔下单 | 培育 | 每月 1 次 |
| D - 风险 | 订单下降/有问题 | 紧急关注 | 随时 |

### 批量导入流程（强制）
1. 读取文件，列出列名和前 3 行示例
2. 展示列映射表（文件列名 → 系统字段），等待确认
3. 自动跳过非数据行（合计行/空行/标题行）
4. 用户确认后逐条创建

### 报价生命周期
```
Draft → Sent → Under Review → Revised → Accepted → Rejected → Expired
```

### 订单跟踪时间线
```
Inquiry → Quote → Sample → PI → Order Confirmation → Production → QC → Shipping → Delivery → Invoice → Payment → After-Sales
```

---

## 11. b2b-data-directory — 数据目录管理

### 概述
管理 `~/.trade/` 下的公司数据目录结构。

### 触发词
- 文档库 / 数据目录 / 公司文件管理
- document library / data directory

### 目录结构
```
~/.trade/
└── <公司名>/
    ├── MEMORY.md          # 长期记忆
    ├── 产品资料/           # 产品规格/目录
    ├── 客户池/             # 客户名单/分析
    ├── quotation/          # 历史报价（按国家分文件夹）
    ├── 海关数据/           # CSV/XLSX 海关数据
    └── output/            # 生成文件输出
```

### 核心操作
- 初始化公司数据目录
- 管理文档库索引
- 创建/更新 8 个固定公司文件
- 导航数据层级

---

## 12. b2b-document — 文档分析

### 概述
精读 B2B 文档（报价单/规格书/合同），提取结构化数据。

### 触发词
- 分析报价单 / 提取数据 / 读文档 / 看规格书
- analyze document / extract data / read quote

### 六条铁律
1. **R0 完整读取**：每个文件必须读到末尾，不截断
2. **R0.5 结构保真**：保留原始列顺序，不删不减不重排
3. **R1 没读不准说**：没 read_file 过的文件禁止断言
4. **R2 数字溯源**：每个数字标注来源单元格/行号/段落
5. **R3 数值原样**：不改精度、不四舍五入、不换算单位
6. **R4 缺单位标注**：源文档没标单位的加 "[单位未标注]"

### 四阶段流程
1. **Survey**：列出目录文件 → 确认类型/行数 → 排序优先级
2. **Deep Read**：逐文件完整精读 → 提取结构化数据
3. **Cross-Reference**：跨文件价格一致性 → 产品代码匹配 → 金额计算验证
4. **Verification Re-Read**：抽检 2-3 个关键数字确认

### 置信度标签
| 标签 | 含义 | 示例 |
|------|------|------|
| [确切] | 直接从文档读取 | "$3.50/pc [确切]" |
| [计算] | 基于文档数值计算 | "$3,500.00 [计算：$3.50 × 1000]" |
| [推断] | 合理推断 | "约30天 [推断：基于历史交期]" |
| [不确定] | 文档模糊 | "TBD [不确定：单据此处空白]" |

---

## 13. b2b-doc-generation — 文档生成

### 概述
生成专业 B2B 文档（DOCX/PPTX/XLSX）。

### 触发词
- 生成文档 / 做 PPT / 导出 Excel / 生成报价单
- generate document / create PPT / export Excel

### 文档类型

**DOCX**：
- 报价单 / 规格书 / 合同 / PI / 工作总结 / 背调报告

**PPTX**：
- 产品目录 / 公司介绍 / 培训材料

**XLSX**：
- 客户清单 / 数据报表 / 价格表 / 社媒月历

### PPTX 质量标准
1. 先规划结构再写代码（10-12 页产品目录，6-8 页公司介绍）
2. 配色 2-3 色，不通用蓝色
3. 每页必须有视觉元素（色条/卡片/表格/图标）
4. 字体层级：标题 36-44pt 粗体，小标题 18-24pt，正文 12-16pt
5. 表格：粗体标题+深色背景，交替行填充
6. 版式变化，不重复

### 通用规则
- **无占位符**：不输出 "XXX" / "[insert]" / "Lorem ipsum"
- **语言一致**：一份文档一种语言
- **生成后验证**：读回文件检查完整性

---

## 14. b2b-trade-ops — 运营沟通

### 概述
成交后全生命周期运营沟通，覆盖 11 个场景。

### 触发词
- 催款 / 索赔 / 展会 / 验厂 / 节日问候
- 样品 / 物流异常 / 售后 / 满意度 / 年度总结
- payment reminder / claim / exhibition / factory audit
- holiday greeting / sample / logistics / after-sales

### 11 个 Phase 速查

| Phase | 场景 | 核心规则 |
|-------|------|---------|
| 1 | 催款（首次） | 先问是否遇到问题，再提付款 |
| 2 | 索赔 | 先道歉安抚，再给方案 |
| 3 | 展会邀请 | 展位号+时间+能带走什么 |
| 4 | 验厂邀请 | 地址+接待人+议程 |
| 5 | 节日问候 | 先确认客户是否过该节日 |
| 6 | 样品寄送 | 追踪号+ETA+使用说明 |
| 7 | 二次催付 | 给台阶下 + 折中方案 |
| 8 | 物流异常 | 主动提供查询链接 + 代理电话 |
| 9 | 售后维护 | 收货第 7 天纯关心不推销 |
| 10 | 满意度调查 | 5 题以内选择题 |
| 11 | 年度总结 | 用数据代替空话 |

### 催款节奏
| 逾期天数 | 方式 | 语气 |
|---------|------|------|
| < 7 天 | 温和提醒 | "checking in" |
| 7-14 天 | 友好提醒 | "gentle nudge" |
| 14+ 天 | 二次催付 | 给折中方案 |

### 节日对照表
| 区域 | 适用节日 | 禁忌 |
|------|---------|------|
| 欧美/拉美 | Christmas, New Year | 非基督徒用 "Season's Greetings" |
| 中东/穆斯林 | Eid al-Fitr, Eid al-Adha | 不饮酒/不猪肉/不红酒 |
| 印度 | Diwali, Holi | 不对穆斯林发 Diwali |
| 中国/东南亚华人 | Lunar New Year, Mid-Autumn | 不给非华人发 |

---

## 15. b2b-trade-compliance — 外贸合规

### 概述
检查外贸沟通中的文化合规性、术语规范、翻译准确性。

### 触发词
- 文化禁忌 / 缩写解释 / Incoterms
- 翻译二审 / 投标 / 上架
- cultural compliance / abbreviation / translation review
- tender / listing check

### 六大 Phase

| Phase | 检查项 | 核心规则 |
|-------|--------|---------|
| 1 | 文化禁忌 | 颜色/数字/动物/手势/送礼 |
| 2 | 缩写解释 | 首次出现必须给全称 |
| 3 | Incoterms | 必须带 Incoterms 2020 + 具体地点 |
| 4 | 翻译二审 | 非英语内容自动附加母语者审阅建议 |
| 5 | 投标招标 | 逐条响应，不多不少 |
| 6 | 电商上架 | 违禁词 + 认证要求 |

### 文化禁忌速查
| 禁忌 | 地区 | 说明 |
|------|------|------|
| 白色 | 中日印 | 丧事/死亡 |
| 数字 4 | 中日韩越 | 谐音"死" |
| 数字 13 | 欧美 | 不吉利 |
| 猪 | 穆斯林国家 | 伊斯兰教禁 |
| 牛 | 印度 | 神圣 |
| 👍 竖大拇指 | 中东/西非 | 侮辱 |
| 左手递物 | 中东/印度/非洲 | 不洁之手 |

### 贸易术语校验
| 错误 | 正确 |
|------|------|
| "Price: FOB" | "Price: FOB Shanghai (Incoterms 2020)" |
| "Terms: CIF" | "Terms: CIF Dubai Port (Incoterms 2020)" |
| "EXW factory" | "EXW Dongguan Factory (Incoterms 2020)" |

### 缩写速查（首次出现必须展开）
ETA (Estimated Time of Arrival), ETD (Estimated Time of Departure), LC (Letter of Credit), BL (Bill of Lading), PI (Proforma Invoice), CI (Commercial Invoice), PL (Packing List), MOQ (Minimum Order Quantity), FOB, CIF, EXW, DDP, T/T, FCL, LCL, HS Code, CE, FDA, RoHS, REACH...

---

## 16. b2b-daily-automation — 每日自动化

### 概述
设置定时任务，自动化每日外贸运营流程。

### 触发词
- 早安简报 / 定时任务 / 自动化 / cron / 日报 / 周报
- morning brief / scheduled task / daily automation

### 定时任务列表

| 时间 | 任务 | 输出 |
|------|------|------|
| 08:00 | 早安简报 | 汇率+大宗+新闻+客户提醒 |
| 09:30 | LinkedIn 内容 | 1 条帖子 |
| 10:00 | 欧洲开发信 | 2-3 封邮件 |
| 11:00 | 平台巡检 | 检查清单 |
| 14:00 | 社媒发布 | FB/Insta/TikTok 帖子 |
| 16:00 | 美洲开发信 | 2-3 封邮件 |
| 17:30 | 每日总结 | 操作回顾+客户变动+待跟进 |
| 周五 17:30 | 周报 | KPI+管道+下周计划 |

### 早安简报规范
**最重要规则**：所有数据必须通过 web_search 实时获取，不得编造、不得留空。

必须搜索：
- 当日 USD/EUR/GBP → CNY 汇率
- 当日金价/铜价/铝价/原油价
- 目标市场 top business news
- 产品行业今日新闻

### Cron 调度语法
| 表达式 | 含义 |
|--------|------|
| `0 8 * * 1-5` | 周一到周五 08:00 |
| `30 9 * * 1-5` | 周一到周五 09:30 |
| `0 10 * * 1-5` | 周一到周五 10:00 |
| `0 14 * * 1-5` | 周一到周五 14:00 |
| `0 16 * * 1-5` | 周一到周五 16:00 |
| `30 17 * * 1-5` | 周一到周五 17:30 |
| `0 18 * * 5` | 每周五 18:00（周报） |

### 交付方式
所有任务使用 `deliver="local"`，结果写入 `~/.hermes/cron/output/`

---

## 17. b2b-skill-generator — 自定义 Skill 生成

### 概述
根据自然语言需求自动生成新 Skill 并注册到系统。

### 触发词
- 生成 skill / 创建 skill / 做个 skill / 写个 skill
- generate skill / create skill / new skill

### 六阶段流程

**Phase 1: 分析需求**
- 数据类型：网页抓取 / API调用 / 文件分析 / 数据库查询 / AI生成
- 输出形式：分析报告 / 数据表格 / 邮件 / 文档 / 图表
- 自动化程度：手动触发 / 定时任务 / 事件驱动

**Phase 2: 生成 SKILL.md**
- 按模板生成，分 Phase 编写
- 用具体工具名：web_search / browser_navigate / database / execute_code
- 如果涉及数据库，写明 SQL 示例

**Phase 3: 写入文件**
- 保存到 `~/.hermes/skills/{skill_name}/SKILL.md`

**Phase 4: 注册到系统**
- 编辑 `skill_registry.py`，在 `_SKILLS` 列表追加

**Phase 5: 重启服务**
- 执行 `_restart_trade_service()`

**Phase 6: 确认**
- 告知用户新 Skill 名称、触发词、保存路径

### 命名规范
- 格式：`b2b-{domain}`
- 英文小写，连字符分隔
- 避免与已有 Skill 重复

---

*本文档版本：1.0 | 更新日期：2026-07-07*
