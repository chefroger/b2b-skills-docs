# 南非公司 OSINT 调研参考

## 关键发现（2026-05-16 [Prospect Company] TRADING 案例）

### 域名发现流程（最重要）

南非公司名通常含 `PTY LTD` / `PTY (LTD)`，WHOIS 无法直接识别为域名格式：
- 目标：`[Prospect Company] TRADING ENTERPRISE (PTY)LTD`
- 构造方法：公司名去掉所有空格/PTY/LTD → `[prospect company]trading.co.za`
- 用 `dig +short` 验证：NS/A/MX 有记录的即为真实注册域名

### DNS 探测命令

```bash
# 验证域名是否存在
dig +short NS [prospect company]trading.co.za
dig +short A [prospect company]trading.co.za
dig +short MX [prospect company]trading.co.za

# 从 SOA 推断注册时间（serial 格式 YYYYMMDDxx）
dig +short SOA [prospect company]trading.co.za
# 例: 2025102709 = 2025-10-27 注册

# 获取 IP 详情
curl -s https://ipinfo.io/<IP>/json
```

### 常见南非托管商

- **HOSTAFRICA**（host-ww.net）- 南非本土主流，便宜新注册域名
- IP 段：102.130.123.x, 102.218.215.x 等
- 约翰内斯堡数据中心是南非新公司的典型托管地

### 域名注册信息

南非 .co.za 域名 WHOIS 被 ZADNA 重定向至 IANA，标准 whois 命令只能拿到 zone 数据：
- 用 `dig +short soa <domain>` 查 SOA serial
- 用 `whois <domain> -h whois.registry.net.za` 无效
- 直接查 NS/A/MX 更可靠

### 网站内容判断

南非新注册 .co.za 域名典型内容：
- "Website coming soon"
- "This Domain Has Been Successfully Registered!"（HostaAfrica 提供）
- 均为占位页，真实运营公司会有真实内容

### 南非公司注册（CIPC）

- 官网：https://www.cipc.co.za/ （当前自动访问受限）
- 注册编号格式：2019/XXXXXXX/07
- PTY LTD = 私有有限公司（Private Limited）
- 验证方式：人工访问 CIPC eServices，输入公司名或注册编号

### LinkedIn 访问注意

LinkedIn 在未登录状态下：
- 搜索公司页会直接跳转登录页
- 直接猜测 URL 访问（如 /company/[prospect company]-trading-enterprise-pty-ltd）会返回 404
- 验证需要登录状态或通过 browser_navigate 实际登录

### 快速检查清单

1. dig +short NS/A/MX 探测域名
2. SOA serial 判断注册时间
3. ipinfo.io 查 IP 归属（南非/约翰内斯堡 = 合理）
4. 浏览器访问 [prospect company]trading.co.za 看内容
5. 检查 SSL 证书（Let's Encrypt = 正常）
6. LinkedIn 搜索（需登录）
7. 要求对方提供 CIPC 注册编号人工验证