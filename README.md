# Vitual XRing Bank 0.1.0

银行平台源码。

## 目录

- `web/bank.html`：银行前端，部署在 `https://bank-xsmmc.caldson.us.ci`
- `worker/bank.js`：Bank API 模块，挂载 `/api/bank/*`

## 功能

- 创建银行卡（`XXXX-XXXX-XXXX-XXXX`）
- 充值：VTX 余额 → 银行卡
- 提现：银行卡 → VTX 余额
- 交易记录
- 充值和提现需要 VTX 账户密码

## 部署说明

Bank 目前复用主站 Cloudflare Worker 的 `ACCOUNTS_KV` 和账户体系：

1. `worker/bank.js` 由主仓库 `Vitual XRing/worker/index.js` 导入，路由 `/api/bank/*`；
2. `web/bank.html` 由 `bank-xsmmc.caldson.us.ci/*` Worker 路由返回；
3. 前端调用主 API `https://xsmmc.caldson.us.ci/api/bank/*`。

主仓库对应文件：

- `Vitual XRing/bank.html`
- `Vitual XRing/worker/bank.js`
- `Vitual XRing/worker/index.js`

## 验证

```bash
node --check worker/bank.js
```

线上：

- https://bank-xsmmc.caldson.us.ci
- https://xsmmc.caldson.us.ci/api/health
