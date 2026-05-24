# Company Screenshot (Transcript)

> 本機未安裝 Gemini CLI（見 FAQ Q5），整個 Phase C/D 在 Claude 中模擬完成。下方是公司運作 transcript（可截圖此檔當作 `company-screenshot.png` 的替代）。

---

```
$ cd ~/projects/compass-and-spade
$ cat shared-memory/client/current/brief.md | head -5
---
client-name: 小儀
received-at: 2026-05-25
client-type: aligned
package-requested: 全鏟組（待 COO 確認）

$ # 啟動 COO 三問判斷流程
$ /intake

[COO] 收到新 brief: 小儀（aligned client）
[COO] 開始三問判斷...

[COO] Q1: 客戶是否卡在兩個領域中間？
[COO]   → YES。企管 + 資工輔修 + 量化研究目標。標準雙身分。

[COO] Q2: 客戶想動手嗎？
[COO]   → 想動手且要「自己天天用」。原應升級過鏟組。
[COO]   → 但時程只有 7 天，外部測試者來不及調度。
[COO]   → 決定: 全鏟組 + 客戶自我即測試者註記

[COO] Q3: 48 小時內能否交一份有用的下一步？
[COO]   → YES。路線測繪師 24hr 內可交路線圖。

[COO] 派工順序確定:
[COO]   1. route-surveyor  : 5/25-5/26 (24 hr)
[COO]   2. well-digger     : 5/27-5/31 (5 天含陪跑)
[COO]   3. COO 整合 final  : 6/1

[COO] 寫入 intake-decision.md ✓
[COO] 寫入 work-orders/route-surveyor.md ✓
[COO] 啟動 @route-surveyor...

---

[route-surveyor] 收到 work order. 讀 brief...
[route-surveyor] 客戶 persona 確認:
[route-surveyor]   企管大三 + 資工輔修 + Python 入門 + 量化研究碩士目標
[route-surveyor]
[route-surveyor] 開始 skill stack 盤點（底/中/上 3 層）...
[route-surveyor] 查證 agent 產品趨勢:
[route-surveyor]   ✓ Elicit       (elicit.com)
[route-surveyor]   ✓ Consensus    (consensus.app)
[route-surveyor]   ✓ SciSpace     (scispace.com)
[route-surveyor]   ✓ NotebookLM   (notebooklm.google)
[route-surveyor]   ✓ Claude Agent SDK
[route-surveyor]
[route-surveyor] 產出 rot/survive 衝擊圖...
[route-surveyor] 寫 90 天微路線 (3 個 milestone)...
[route-surveyor] 寫「她可能不喜歡聽，但我必須說」段落...
[route-surveyor]
[route-surveyor] Quality Gate 1: 引用 agent 產品 5 個 (>= 3) ✓
[route-surveyor] Quality Gate 2: 每個 milestone 有驗收標準 ✓
[route-surveyor]
[route-surveyor] 草稿寫到 drafts/route-surveyor.md ✓
[route-surveyor] 通知 COO 審稿.

---

[COO] /review route-surveyor

[COO] 審查三問:
[COO]   1. 通過 route-surveyor 自己的 Quality Gate? YES
[COO]   2. 與前一位 specialist 銜接? N/A (首位)
[COO]   3. 回應 brief 具體問題? YES
[COO]      (paper 慢 → rot/survive 圖; 研究主題脈絡 → 60-90 天路線)
[COO]
[COO] APPROVED. 標記到草稿尾端.
[COO] 啟動 @well-digger...

---

[well-digger] 收到 work order. 讀 route-surveyor 草稿...
[well-digger] 客戶切入點選擇: paper 閱讀 agent (對接 30 天 milestone)
[well-digger]
[well-digger] SDK 選擇分析:
[well-digger]   候選: Claude Agent SDK (Py) / LangGraph / OpenAI Assistants
[well-digger]   選定: Claude Agent SDK (Py) + file-based memory
[well-digger]   理由: 客戶 Python 入門、200K context、無向量資料庫負擔
[well-digger]   排除: LangGraph (抽象層太多)、OpenAI (file_search 不夠強)
[well-digger]
[well-digger] 寫 step-by-step 指南 (5 steps + 卡關預警)...
[well-digger]
[well-digger] 陪跑開始:
[well-digger]   5/27 19:00  環境設定: M1 PATH 衝突 (10 min 解)
[well-digger]   5/28 20:30  Hello world 跑通. 客戶: "它真的懂我的研究主題"
[well-digger]   5/29 21:00  Scanned PDF 卡關 → 換 pdfplumber
[well-digger]   5/30 19:30  客戶自加「量表挑選」延伸功能（觀察點）
[well-digger]   5/31 21:30  視訊驗收: 客戶口述通過
[well-digger]
[well-digger] Quality Gate 1: 客戶用自己話講清楚 demo? ✓
[well-digger] Quality Gate 2: Demo 在客戶 M1 Mac 跑得起來? ✓
[well-digger] Quality Gate 3: GitHub repo + README (3 段)? ✓
[well-digger]
[well-digger] 試刀人未啟動 → 補「自我測試 checklist」(7 項)
[well-digger]
[well-digger] 草稿寫到 drafts/well-digger.md ✓
[well-digger] 通知 COO 審稿.

---

[COO] /review well-digger

[COO] 審查三問:
[COO]   1. 通過 well-digger 自己的 Quality Gate? YES
[COO]   2. 與 route-surveyor 銜接?
[COO]      route-surveyor 第 1-30 天 milestone = 跑通 paper agent
[COO]      well-digger 交付 = paper agent demo ✓ 對接
[COO]   3. 回應 brief 具體問題?
[COO]      ✓ paper 閱讀慢 → demo
[COO]      ✓ 研究主題脈絡 → file-based memory
[COO]      ✓ 指導老師 demo → 1 分鐘示範流程
[COO]
[COO] APPROVED. 但採納兩個建議到 final deliverable:
[COO]   - 補上 "Python 中階補課" 提醒 (7 月路線)
[COO]   - "她可能不喜歡聽" callout 移到一頁總結

---

[COO] /deliver

[COO] 讀所有 approved 草稿...
[COO] 整合 deliverable (依 spec.md E 區結構):
[COO]   ✓ 1. 一頁總結（重寫，給指導老師也能看）
[COO]   ✓ 2. 領域 × agent 衝擊圖
[COO]   ✓ 3. SDK Demo
[COO]   ✓ 4. 真實測試（本次未啟動，標註替代方案）
[COO]   ✓ 5. 下一步路線圖（補 Python 補課提醒）
[COO]
[COO] Final Quality Gate (5 項):
[COO]   [x] brief 具體問題都有回應
[COO]   [x] 引用 agent 產品全部真實 (5/5 已查證)
[COO]   [x] 套餐配置 specialists 都有產出
[COO]   [x] 30/60/90 天 milestone
[COO]   [x] 每個 milestone 有最小可驗收標準
[COO]
[COO] APPROVED 5/5. 交付.
[COO] 寫到 shared-memory/client/current/deliverable.md ✓

$ ls shared-memory/client/current/
brief.md             drafts/              review-comments/
deliverable.md       intake-decision.md   work-orders/

$ wc -l shared-memory/client/current/deliverable.md
     156 shared-memory/client/current/deliverable.md
```

---

## 流程摘要

| 階段 | 時間點 | 動作 | 產出 |
|------|--------|------|------|
| Intake | 5/25 19:00 | COO 三問判斷 | intake-decision.md, work-orders/ |
| Specialist 1 | 5/25-5/26 | route-surveyor 盤點 + 路線圖 | drafts/route-surveyor.md |
| Review 1 | 5/26 21:00 | COO 審稿 | 標記 APPROVED |
| Specialist 2 | 5/27-5/31 | well-digger SDK demo + 陪跑 | drafts/well-digger.md |
| Review 2 | 5/31 22:00 | COO 審稿 | 標記 APPROVED + 採納 2 建議 |
| Deliver | 6/01 | COO 整合 + Final QG | deliverable.md (5/5 通過) |
