# B2B Skills

> 17 个 B2B Skills 的完整使用文档 —— 从获客到履约的全流程编排

## 快速开始

| 文档 | 用途 | 适合谁 |
|------|------|--------|
| [README.md](README.md) | 全景图 + 业务流程 + Skill 详细说明 | 所有人 |
| [QUICKREF.md](QUICKREF.md) | 场景速查卡，一句话找到对应 Skill | 日常使用 |
| [USAGE-ORDER.md](USAGE-ORDER.md) | 按阶段排列的 Skill 调用顺序 | 新手部署 |
| [REFERENCE.md](REFERENCE.md) | 每个 Skill 的完整技术规范 | 深度使用 |
| [FLOWCHARTS.md](FLOWCHARTS.md) | Mermaid 流程图（可渲染查看） | 可视化理解 |

## Skills 总览

### 获客阶段
- **b2b-lead-generation** — 三通道并行搜索潜客 + 写开发信
- **b2b-osint** — 客户背景调查/尽职调查/风险评估
- **b2b-email-intel** — 邮箱背景调查（120+ 平台注册检测）
- **b2b-customs-data** — 海关进出口数据分析找采购商

### 触达阶段
- **b2b-cold-outreach** — 产品推广信/开发信/跟进信
- **b2b-linkedin-marketing** — LinkedIn Profile 优化 + 内容营销
- **b2b-social-media** — Facebook/Instagram/TikTok/YouTube 社媒策略
- **b2b-platform** — B2B 平台（Alibaba/独立站）店铺诊断优化

### 管理阶段
- **b2b-customer-mgmt** — 客户档案管理/分级/报价/订单跟踪
- **b2b-data-directory** — 公司文档库/客户池/数据目录管理
- **b2b-document** — 文档分析（报价单/规格书/合同数据提取）
- **b2b-doc-generation** — 文档生成（DOCX/PPTX/XLSX）

### 运营阶段
- **b2b-trade-ops** — 催款/索赔/展会/验厂/节日/样品/物流/售后
- **b2b-trade-compliance** — 文化禁忌/缩写解释/Incoterms/翻译二审/投标
- **b2b-daily-automation** — 早安简报/定时发布/日报/周报自动化

### 扩展阶段
- **b2b-onboarding** — 新公司/新用户从零部署全套营销方案
- **b2b-skill-generator** — 根据需求描述自动生成新 Skill

## 典型工作流

```
新公司启动 → b2b-onboarding → 建立档案
     ↓
找客户 → b2b-lead-generation → b2b-osint 背调
     ↓
写信 → b2b-cold-outreach → b2b-trade-compliance 合规检查
     ↓
管理 → b2b-customer-mgmt → b2b-doc-generation 报价单
     ↓
运营 → b2b-trade-ops 履约 → b2b-daily-automation 自动化
```

详见 [README.md](README.md) 中的完整业务流程编排。

## 项目结构

```
b2b-skills-docs/
├── README.md          # 主文档
├── QUICKREF.md        # 场景速查卡
├── REFERENCE.md       # 完整参考
├── USAGE-ORDER.md     # 使用顺序
├── FLOWCHARTS.md      # 流程图
├── CONTRIBUTING.md    # 贡献指南
└── LICENSE
```

## License

Internal documentation — all rights reserved.
