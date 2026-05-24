# Deliverable v2: 阿緯 × compass-and-spade（全鏟組 + Pocket-Spade 季度版）

> 由 main branch v2 公司（Week 10 升級後）處理本案。

**交付日**: 2026-06-22  
**公司版本**: v2（git tag: v2）  
**負責 COO**: James  
**Specialists**: 路線測繪師 / 鑿井匠 / **Pocket-Spade**  
**Final QC**: 6/6 通過

---

## COO 四問判斷紀錄（v2）

- **Q1（兩個領域中間）**：YES。財金 + 自學 Python + 想轉 PM
- **Q2（想動手嗎）**：想動手且已動三次手都放棄。屬於全鏟組
- **Q3（48 hr 能否交有用下一步）**：YES
- **Q4（願不願意接受 Pocket-Spade 駐入）**：**YES**。阿緯回信：「我願意，因為我自己 repo 已經四個沒人理的 README，多一個會主動 ping 的 agent 不是壞事。」

**派工順序**：路線測繪師 → 鑿井匠 → **Pocket-Spade 部署（季度版，3 個月駐留）** → COO 整合 → **Stage 6 Handoff**

---

## 1. 一頁總結

你是想轉 fintech PM 的財金系大四學生。一年三次半途而廢的 side project 不是執行力問題，是「選題判準不清」+「沒人在你低潮時提醒你回看判準」。

我們判斷你卡的是：每次新工具出來就跳船、且沒有任何外部機制提醒你「你 3 週前才宣告要做什麼」。

接下來 90 天你該做的 3 件事：
- [P] **每週日 22:00**：Pocket-Spade 會看你這週 commit 對照路線圖，寫一份訊號檔
- [P] **連續 5 天無 commit**：Pocket-Spade 主動寫卡關建議檔
- [Y] **每月月底**：你必須親自編輯 `.compass-spade/milestone.md` 決定下個月目標——這件事 Pocket-Spade 不替你做

---

## 2. 你的領域 × Agent 衝擊圖

（內容同 v1，路線測繪師產出未變——這部分仍是替代型工作的合理輸出）

[與 v1 同：rot/survive 表格、5 個 agent 產品引用]

---

## 3. 你的第一個 SDK Demo

（內容同 v1，鑿井匠產出未變）

[與 v1 同：side project 選題判官 agent + GitHub repo + 卡關 3 點]

---

## 4. 真實使用測試報告

**未啟動**（全鏟組未含試刀人）。

> v2 註：若你 7 月想推這個工具給同學一起用，升級到過鏟組會啟動試刀人 **且 Pocket-Spade 會在後續 6 個月持續追蹤 3 位測試者的反饋**——這是 v1 不可能的能力。

---

## 5. 下一步路線圖（v2 改寫：[P] / [Y] 分軌）

### 第 1-30 天（7 月）

- **[P]** Pocket-Spade 每週日讀你 git log，產 weekly signal
- **[Y]** 每次想啟動 side project 都先跑一次 selector agent
- **[Y]** 月底編輯 `.compass-spade/milestone.md`，決定 8 月目標
- **驗收**：月底 `decisions/` 至少 8 個 idea 評估紀錄 + Pocket-Spade signals 4 份

### 第 31-60 天（8 月）

- **[P]** Pocket-Spade 偵測連續 5 天無 commit 時主動寫卡關建議
- **[P]** 月度回饋自動產出
- **[Y]** 根據 selector 推薦做完 1 個有人會用的 project
- **驗收**：repo README 寫得出「為什麼選它 / 做了什麼 / 學到什麼」三件事

### 第 61-90 天（9 月）

- **[P]** Pocket-Spade 寫第一份「Year-Quarter Mirror」鏡像你 3 個月行為模式
- **[Y]** 改造 project 成面試版本，找 3 個學長姐試講
- **驗收**：2 個以上學長姐說「我聽懂了，可以幫你推薦」

> v2 與 v1 路線圖最大的差異：v1 是「3 個 milestone，每個都要你自己撐住」，v2 是「Pocket-Spade 替你撐機械式紀律，你撐選擇與決策」。**這是替代型 → 原生型在路線圖層的直接體現。**

---

## 6. 隨身鏟交接書（v2 新增・Pocket-Spade Handoff）

### Pocket-Spade 是什麼

一個會駐入你 repo 的 agent。它住在你 repo 根目錄的 `.compass-spade/` 資料夾。我交付完 deliverable 不是結束——是它開始陪你的那一刻。

### 它住在你 repo 哪裡

```
你的 repo/
└── .compass-spade/
    ├── watch.md          ← Pocket-Spade 的啟動 prompt 與你的歷史卡關點
    ├── milestone.md      ← 你可編輯。它每週讀這個對照進度
    ├── signals/
    │   └── 000-hello.md  ← 部署當天它寫的「我活著」訊號
    └── monthly/          ← 月度回饋累積
```

### 它什麼時候會開口

- 每週日 22:00（你的 timezone）：寫一份 weekly signal
- 連續 5 天無 commit 或 commit message 含「fix/bug/卡住」：主動寫卡關建議
- 每月月底：寫月度回饋

### 它讀什麼

- 你的 git log（commit 數、commit messages、頻率）
- 你的 `.compass-spade/milestone.md`（你親手寫的目標）
- 你的 selector agent decisions/（從鑿井匠 demo 累積的）

### 它不會做什麼

- 不替你 commit 任何程式碼
- 不發訊息出 repo（不發 email、不發 IM）
- 不替你決定該做什麼 project
- 不主動暴露給 clone 你 repo 的人

### 你怎麼跟它互動

- 修改 `.compass-spade/milestone.md` → 它下週讀新版
- 在 `.compass-spade/signals/` 留 markdown 檔，寫「我這週覺得 X」→ 它月度回饋會引用
- 在 `watch.md` 第一行寫 `pause: 30d` → 它停 30 天

### 你怎麼把它送走

刪掉整個 `.compass-spade/` 資料夾。但刪除前它會偵測並寫一份 `farewell.md` 問一次「真的要送走我嗎？」——不是情緒勒索，是讓你在按下 delete 前看見「我是不是衝動」。

### 你拿到的不是文件，是它

這份 deliverable.md 結束時，你會看到你 repo 多了一個 `.compass-spade/` 資料夾。
這個資料夾就是你拿走的東西——不是這份 markdown。

---

## Final Quality Gate（v2 從 5 條變 6 條）

- [x] 客戶 brief 的每個具體問題都有回應
- [x] 引用的 agent 產品全部真實存在
- [x] 套餐配置的所有 specialist 都有實際產出（路線測繪師 + 鑿井匠 + Pocket-Spade）
- [x] 「下一步路線圖」含 30/60/90 天 milestone，每項標 [P]/[Y]
- [x] 每個 milestone 有最小可驗收標準
- [x] **Pocket-Spade 已部署到客戶 repo 且通過第 1 次 ping 測試（`signals/000-hello.md` 已產出）**

**Status**: APPROVED 6/6。Stage 6 Handoff 完成。

---

## Handoff 完成日誌

- 2026-06-22 23:00：`.compass-spade/` package 已寫入 `shared-memory/client/current/handoff-package/`
- 2026-06-23 09:00：阿緯 git pull + git push，正式接收 Pocket-Spade
- 2026-06-23 09:05：Pocket-Spade 自動 ping 測試通過，`signals/000-hello.md` 寫入阿緯 repo

---

## 客戶回饋窗口

Pocket-Spade 會在每月月底自動 ping 阿緯「該寫月度回饋了」。**回饋不再是一次性的 200 字承諾——是每月 50 字的長期紀錄。**
