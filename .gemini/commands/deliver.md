---
description: COO 整合所有 approved 草稿，產出最終 deliverable，並執行 Final Quality Gate
---

# /deliver

當所有套餐配置中的 specialist 都已 approved，COO 執行最後整合：

1. 讀取所有 approved 草稿
2. 依 spec.md E 區結構整合
3. 重寫一頁總結（用客戶語言）
4. 補上「下一步 30/60/90 天路線圖」
5. 執行 Final Quality Gate 5 項勾選
6. 全勾後寫到 `shared-memory/client/current/deliverable.md`

## 使用方式

```
/deliver
```

## 前置條件

- 套餐配置中所有 specialist 都 approved
- `shared-memory/client/current/drafts/` 內所有檔案尾端都有 `[APPROVED by COO]` 標記

## 預期產出

- `shared-memory/client/current/deliverable.md`
- 將整個 case folder 移到 `shared-memory/client/archive/{date}-{client-name}/`
