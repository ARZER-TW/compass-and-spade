---
description: 派發下一位 specialist 開始工作（在前一位通過 Quality Gate 後）
---

# /dispatch

依套餐順序，啟動下一位待命的 specialist：

- 全鏟組：路線測繪師 approved → 啟動鑿井匠
- 過鏟組：鑿井匠 approved → 啟動試刀人

## 使用方式

```
/dispatch
```

## 前置條件

- 至少有一位 specialist 已交稿且通過 COO Quality Gate
- 套餐配置中還有 specialist 未啟動

## 預期產出

- 該 specialist 讀取 work order 開始工作
- 草稿存到 `shared-memory/client/current/drafts/{specialist}.md`
