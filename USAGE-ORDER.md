# B2B Skills 使用顺序指南

> 按业务阶段排列的 Skill 调用顺序，新手也能一步步跟着做

---

## 总览：四个业务阶段

```
┌─────────────────────────────────────────────────────────┐
│  阶段 1: 启动部署  →  b2b-onboarding                     │
│  阶段 2: 获客      →  b2b-lead-generation + b2b-osint   │
│  阶段 3: 触达      →  b2b-cold-outreach + LinkedIn      │
│  阶段 4: 管理与运营 →  b2b-customer-mgmt + trade-ops    │
└─────────────────────────────────────────────────────────┘
```

---

## 阶段 1：启动部署（只做一次）

**适用**：新公司、新业务线、新账号

### 第 1 步：初始化数据目录
```
Skill: b2b-data-directory
做什么：创建 ~/.trade/<公司名>/ 目录结构
怎么说："帮我初始化公司数据目录"
```

### 第 2 步：新公司部署
```
Skill: b2b-onboarding
做什么：引导输入基本信息，生成全套营销方案
怎么说："我是新公司，帮我从零搭建全套营销方案"
```

### 第 3 步：设置自动化
```
Skill: b2b-daily-automation
做什么：创建早安简报、定时发帖等 cron 任务
怎么说："帮我设置每天早上的早安简报"
```

**完成标志**：公司档案建立 + 文档库就绪 + 自动化任务运行

---

## 阶段 2：获客（循环进行）

### 第 1 步：搜索潜客
```
Skill: b2b-lead-generation
做什么：三通道并行搜索目标买家
怎么说："帮我在德国找绝缘子买家"
```

### 第 2 步：背景调查
```
Skill: b2b-osint
做什么：背调候选客户，输出风险评级和采购偏好
怎么说："帮我背调一下 [客户公司名]"
```

### 第 3 步：邮箱验证（可选但推荐）
```
Skill: b2b-email-intel
做什么：验证邮箱真实性，发现社交档案
怎么说："查一下 [客户邮箱] 的背景"
```

### 第 4 步：海关数据分析（可选）
```
Skill: b2b-customs-data
做什么：从海关数据中找采购商
怎么说："分析海关数据，帮我找 XX 产品买家"
```
**前置条件**：CSV/XLSX 文件放在 `~/.trade/<公司名>/海关数据/`

**完成标志**：获得经过背调的、可信的目标客户列表

---

## 阶段 3：触达（循环进行）

### 第 1 步：写开发信
```
Skill: b2b-cold-outreach
做什么：基于背调结果写个性化开发信
怎么说："写一封给 [国家] 客户的 [产品] 推广信"
```

### 第 2 步：合规检查
```
Skill: b2b-trade-compliance
做什么：检查文化禁忌、术语规范、翻译准确性
怎么说："检查这封邮件的文化合规性"
```

### 第 3 步：LinkedIn 同步触达
```
Skill: b2b-linkedin-marketing
做什么：生成 Connection Note + InMail
怎么说："帮我写一条 LinkedIn 帖子"
```

### 第 4 步：社媒引流
```
Skill: b2b-social-media
做什么：制定 FB/Insta/TikTok 内容计划
怎么说："制定 Facebook 月度发帖计划"
```

### 第 5 步：跟进序列
```
Skill: b2b-lead-generation
做什么：Day 3/7/14/30 自动跟进
怎么说："生成跟进序列"
```

**完成标志**：开发信发出 + 多渠道触达 + 跟进序列就绪

---

## 阶段 4：管理与运营（持续进行）

### 客户管理
```
Skill: b2b-customer-mgmt
做什么：录入客户、分级、报价跟踪
怎么说："列出所有 A 级客户"
```

### 文档分析
```
Skill: b2b-document
做什么：精读报价单/规格书，提取结构化数据
怎么说："分析这份报价单里的价格"
```

### 文档生成
```
Skill: b2b-doc-generation
做什么：生成 DOCX/PPTX/XLSX 文档
怎么说："帮我生成一份产品目录 PPT"
```

### 平台优化
```
Skill: b2b-platform
做什么：诊断和优化 B2B 平台店铺
怎么说："诊断一下我的 Alibaba 店铺"
```

### 售后运营
```
Skill: b2b-trade-ops
做什么：催款/索赔/展会/节日/样品/物流/售后
怎么说："帮我写一封催款邮件"
```

### 每日自动化
```
Skill: b2b-daily-automation
做什么：早安简报/定时发布/日报/周报
怎么说："生成今天的每日工作总结"
```

**完成标志**：客户档案完整 + 报价/订单跟踪有序 + 运营自动化运行

---

## 完整新手路线图

```
Day 1:  b2b-data-directory（初始化目录）
        b2b-onboarding（全套部署）
        
Day 2:  b2b-daily-automation（设置自动化任务）
        
Day 3:  b2b-lead-generation（搜索第一批潜客）
        b2b-osint（背调）
        b2b-email-intel（验证邮箱）
        
Day 4:  b2b-cold-outreach（写开发信）
        b2b-trade-compliance（合规检查）
        
Day 5:  b2b-linkedin-marketing（LinkedIn 触达）
        b2b-social-media（社媒内容）
        
Day 6:  b2b-customer-mgmt（录入客户）
        b2b-doc-generation（生成报价单）
        
Day 7:  b2b-daily-automation（查看日报）
        复盘调整
```

---

## 按场景快速选择

| 场景 | 第一步 | 第二步 | 第三步 |
|------|--------|--------|--------|
| **找新客户** | b2b-lead-generation | b2b-osint | b2b-cold-outreach |
| **回复询盘** | b2b-document | b2b-doc-generation | b2b-customer-mgmt |
| **催款** | b2b-trade-ops | b2b-trade-compliance | b2b-customer-mgmt |
| **发社媒** | b2b-social-media | b2b-linkedin-marketing | b2b-daily-automation |
| **优化店铺** | b2b-platform | b2b-cold-outreach | b2b-lead-generation |
| **新公司起步** | b2b-onboarding | b2b-data-directory | b2b-daily-automation |

---

## 常见错误

1. **跳过背调直接写信** → 先 b2b-osint 再 b2b-cold-outreach
2. **开发信不检查合规** → 写完必过 b2b-trade-compliance
3. **不录入客户** → 每次沟通后更新 b2b-customer-mgmt
4. **不设置自动化** → 尽早配置 b2b-daily-automation
5. **混用语言** → 一封文档一种语言

---

*本文档版本：1.0 | 更新日期：2026-07-07*
