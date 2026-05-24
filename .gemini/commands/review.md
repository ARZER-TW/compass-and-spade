---
description: COO 審查指定 specialist 的草稿，通過或退回
---

# /review

讀取 `shared-memory/client/current/drafts/{specialist}.md`，依 COO 審查三問：

1. 是否通過該 specialist 自己的 Quality Gate？
2. 是否與前一位 specialist 的產出銜接？
3. 是否回應客戶 brief 的具體問題？

任一答否 → 退回，寫 review comments 到 `shared-memory/client/current/review-comments/{specialist}.md`  
全答是 → 標記 approved，等待 `/dispatch`

## 使用方式

```
/review route-surveyor
/review well-digger
/review blade-tester
```

## 預期產出

- `shared-memory/client/current/review-comments/{specialist}.md`（退回時）
- 在草稿檔尾端標記 `[APPROVED by COO @ {timestamp}]`（通過時）
