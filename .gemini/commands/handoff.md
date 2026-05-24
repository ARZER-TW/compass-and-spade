---
description: Week 10 v2 新增。Stage 6 — 部署 Pocket-Spade 到客戶 repo，生成隨身鏟交接書。
---

# /handoff

在 Final Quality Gate 6/6 通過後執行。

把 Pocket-Spade 部署到客戶 repo，並交一份「隨身鏟交接書」（deliverable 的 Section 6）。

## 前置條件

- Final Quality Gate 已 5/6 通過（最後一條 Pocket-Spade ping 要靠這次 handoff 解鎖）
- 客戶已在 Stage 1 Q4 同意 Pocket-Spade 駐留（intake-decision.md 已記錄）
- 客戶 repo 連結已知

## 執行步驟

1. **生成 `.compass-spade/watch.md`**
   - Pocket-Spade 啟動 prompt（從 `.gemini/agents/pocket-spade.md` 改寫）
   - 客戶 milestone 摘要（從 deliverable.md Section 5 抽）
   - 客戶歷次卡關點（從鑿井匠的「卡關 log」抽）

2. **生成 `.compass-spade/milestone.md`**
   - 客戶可編輯的版本
   - 預填 30/60/90 天的 milestone + 每項標 [P]/[Y]
   - 客戶被預期每月修一次（Pocket-Spade 會 ping 提醒）

3. **生成 `.compass-spade/signals/000-hello.md`**
   - Pocket-Spade 部署當天的「我活著」訊號
   - 包含一句話：「我會在每週日 22:00 看你這週做了什麼」
   - 客戶看到這封信、就是 Pocket-Spade 正常啟動的證據

4. **生成 客戶 repo 的 README 補充段落**
   - 標題「This repo has a Pocket-Spade」
   - 1 段說明：它是什麼、住在哪、會看什麼、不會做什麼、怎麼送走它

5. **生成 deliverable 的 Section 6（隨身鏟交接書）**
   - 寫到 `shared-memory/client/current/deliverable.md`

6. **執行 Pocket-Spade 自我 ping 測試**
   - 模擬一次「讀 milestone.md → 寫 signals/000-hello.md」的完整循環
   - 通過 → 把 Final QG 第 6 條打勾
   - 沒通過 → 退回，修正 Pocket-Spade 的 watch.md

7. **整理 handoff package 給客戶**
   - 把整個 `.compass-spade/` 草稿放到 `shared-memory/client/current/handoff-package/`
   - 等客戶簽收後（客戶在 repo 跑一次 git pull + git push）才視為 handoff 完成

## 預期產出

- `shared-memory/client/current/handoff-package/.compass-spade/watch.md`
- `shared-memory/client/current/handoff-package/.compass-spade/milestone.md`
- `shared-memory/client/current/handoff-package/.compass-spade/signals/000-hello.md`
- `shared-memory/client/current/handoff-package/README-supplement.md`
- 在 `deliverable.md` 補上 Section 6
- 在 `intake-decision.md` 末段註明「Handoff completed on YYYY-MM-DD」

## 失敗模式

- 客戶 repo 連結拿不到 → 暫緩 handoff，請 COO 補資訊
- Pocket-Spade ping 測試失敗 → 退回到 pocket-spade.md 修
- 客戶事後反悔不要駐留 → 啟動「降規為 v1.5」流程（COO 須記下退規原因）

## 使用方式

```
/handoff
```
