# 早安简报数据源执行笔记
> 更新：2026-06-05 | 来源：早安简报生成实战

## 汇率数据

### ✅ 可用来源
| 源 | 端点 | 成功率 | 备注 |
|---|---|---|---|
| exchangerate-api.com | `https://api.exchangerate-api.com/v4/latest/USD` | **高** | 返回完整汇率表，含CNY |
| frankfurter.app | `https://api.frankfurter.app/latest?from=USD&to=CNY` | **高** | 轻量，免费 |

### ❌ 失败来源
- exchangerate-api.com 的 `/v4/latest/USD` — 无API Key时正常，有Key时返回空
- frankfurter.app — 正常可用（session记录中获取了USD/CNY 6.7739）

**实战结果（2026-06-05）**：
- exchangerate-api.com date=2026-06-05：USD 6.79，EUR 7.89，GBP 9.12
- frankfurter.app date=2026-06-04：USD/CNY 6.7739（仅USD一个货币对）

---

## 大宗商品数据

### ⚠️ 所有免费API均失败（2026-06-05实测）

| 源 | 端点 | 失败原因 |
|---|---|---|
| metals-api.com | demo key | 401 Invalid API key |
| commodities-api.com | demo key | 401 Invalid API key |
| metals.live | API | 返回空 |
| metalpriceapi.com | API | 返回空 |
| alphavantage.co | API | 返回空 |
| tiingo.com | demo token | Invalid token |
| twelvedata.com | — | 404 Not Found |
| financialmodelingprep.com | API | 返回空 |
| Yahoo Finance (GC=F, CL=F, HG=F) | 非授权API | 429 Too Many Requests |
| LME.com | API | 返回空 |
| EIA.gov | API | 返回空 |

### ✅ 可用方案（浏览器）
| 源 | 工具 | 成功率 |
|---|---|---|
| investing.com 黄金页面 | browser_navigate | ✅ 成功（获取了1825字符） |
| MarketWatch 黄金页面 | browser_navigate | ✅ 成功（获取了788字符） |
| CNBC 黄金页面 | browser_navigate | ✅ 成功（获取了5309字符） |
| Kitco.com 首页 | browser_navigate | ⚠️ 返回404，需检查URL |
| Kitco LME价格页 | browser_navigate | ⚠️ 返回404 |

**实战结果**：
- browser_navigate 到 investing.com → 可获取黄金价格文本（需从HTML中解析数字）
- browser_navigate 到 CNBC → 大量内容但需解析
- curl + grep 对 kitco.com 的旧脚本端点返回404

### 📝 浏览器数据解析建议
```bash
# 解析 CNBC 黄金页面的价格（示例）
browser_navigate "https://www.cnbc.com/news/gold-futures"
browser_snapshot
# 然后用 browser_console 在页面上执行 JS 提取数字
```

---

## 新闻/RSS数据

### ❌ 失败来源
| 源 | 原因 |
|---|---|
| Google News RSS | 返回 "Sorry..." 页面（可能被block） |
| Kitco 新闻页 | 超时失败 |

### ✅ 备选方案
- browser_navigate 到 Reuters.com / Bloomberg.com 手动搜索
- 搜索特定关键词：`site:reuters.com power grid insulator 2026`

---

## 客户跟进数据

### ✅ 可用来源
| 源 | 工具 | 成功 |
|---|---|---|
| 会话历史 | session_search | ✅ 可搜索关键词找到客户上下文 |
| cron output 目录 | read_file | ✅ 可读取历史任务输出 |

### ⚠️ 限制
- session_search 返回的是会话摘要（非原始对话），包含18,004字符的会话记录
- 没有结构化CRM，每次需要用 session_search 搜索客户名称
- 客户名称需人工核实（会话中推断的客户名可能不准确）

---

## 总结：2026-06-05 早安简报的实际局限

本次简报中：
- **汇率**：✅ 成功获取（exchangerate-api.com）
- **大宗商品**：⚠️ **全部失败** — 黄金/铜/铝/原油均无法获取，所有数字为"未获取到"
- **市场新闻**：⚠️ **全部失败** — Google News RSS被block，无实时新闻

**结论**：在没有付费API Key的情况下，大宗商品和新闻数据必须依赖浏览器手动查询。简报中不得出现占位符数字，应明确标注"⚠️ 数据未获取，请手动查询 [网站]"。