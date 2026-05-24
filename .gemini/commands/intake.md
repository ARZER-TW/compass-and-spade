---
description: 接收新客戶 brief 並啟動 COO 三問判斷流程
---

# /intake

讀取 `shared-memory/client/current/brief.md` 並執行 COO 流程：

1. COO 三問判斷
2. 把判斷結果寫入 `shared-memory/client/current/intake-decision.md`
3. 若決定接案，產出對應 specialist 的 work order 到 `shared-memory/client/current/work-orders/`
4. 啟動第一位 specialist（依套餐：路線測繪師）

## 使用範例

```
/intake
```

## 前置條件

- `shared-memory/client/current/brief.md` 存在且內容完整

## 預期產出

- `shared-memory/client/current/intake-decision.md`
- `shared-memory/client/current/work-orders/route-surveyor.md`（必有）
- `shared-memory/client/current/work-orders/well-digger.md`（全鏟組以上）
- `shared-memory/client/current/work-orders/blade-tester.md`（過鏟組）
