# Week 10 升級規格書

## 鑰匙：最戳的那一句洞見

> 替代型公司交一份報告，原生型公司交一個能持續陪伴客戶的東西。

整份升級規格書，都圍繞這句話打。

---

## spec.md 五區改造計畫

### A 精神

**要改。**

- 改成什麼：「我們不教人用 AI，我們陪人挖」→「我們不送你一張地圖，我們在你家裝一個會持續挖的東西」。Manifesto 的隱喻從「陪挖者」變成「種下持續挖的工具」。
- 為什麼：原版的「陪挖」隱喻是替代型——一個人類老師也能做的事。原生型應該是「我走了之後，那個會挖的東西還在」。

### B 服務目錄

**要改。**

- 改成什麼：每個套餐都加「隨身鏟交接」階段。半鏟組是「一份路線圖 + 一個 1 週期會 ping 你的 agent」、全鏟組是「路線圖 + SDK demo + 一個會看你 commit 提醒你偏離的 agent」、過鏟組是「全鏟組 + 一個會把 3 位測試者反饋持續累積進你 repo 的 agent」。
- 為什麼：原版套餐都終止於「交付」——這是替代型的計價邏輯（依工時 / 工件計價）。原生型計價邏輯應該是「永久關係的啟動費」。

### C specialists

**要改、要新增。**

- 試刀人：不刪，但職責收窄（過鏟組才出場、且要把測試結果寫進 Pocket-Spade）
- 路線測繪師、鑿井匠：精神保留，但 deliverable 模板要加「給 Pocket-Spade 的種子資料」section
- 新增 1 位「Pocket-Spade（隨身鏟）」——這是核心改造

### D COO 工作流

**要改。**

- 三問判斷加第 4 問：「客戶願不願意接受一個 agent 駐留在他的 repo / 環境？」
- 為什麼：駐留是原生型設計的核心契約。如果客戶不願意，那他要的是替代型服務，需要明確告知「我們不適合」或降規為「一次性版本」（折扣價、但承認這是退而求其次）。
- COO 工作流加一個新階段：Handoff（隨身鏟交接）。Final QC 之後不是結束，是 Pocket-Spade 部署到客戶環境。

### E deliverable 結構

**要改。**

- 原本 5 個 section（一頁總結 / 衝擊圖 / SDK demo / 真實測試 / 路線圖）→ 改成 6 個 section
- 新增 Section 6：隨身鏟交接書（Pocket-Spade Handoff）——說明這個 agent 是什麼、住在客戶哪裡、會做什麼、會在什麼時機開口、客戶怎麼跟它互動、怎麼把它養大。
- 並且把 Section 5「下一步路線圖」改寫為「Pocket-Spade 會幫你看著的事 + 你必須親自決定的事」——分清楚「agent 自動陪你」與「只有你能做」的邊界。

---

## specialist 檔案改造計畫

### 要重寫的 specialist

- 檔名：`.gemini/agents/coo.md`
  - 為什麼：要加第 4 問判斷、要加 Handoff stage、要把 Final QC 從 5 條變 6 條（多一條：Pocket-Spade 是否已部署且通過第 1 次 ping 測試）

### 要砍的 specialist

- 無。但試刀人的「我何時被啟動」段要修，加上「過鏟組客戶必須先同意 Pocket-Spade 駐留」前提。

### 要新增的 specialist

- 新檔名：`.gemini/agents/pocket-spade.md`
- 核心職責：
  1. 在客戶 repo 駐留（以一份 `.compass-spade/watch.md` 放在客戶 repo 根部當 home base）
  2. 每週讀一次客戶 git log，比對「90 天路線圖 milestone」，產出「你這週做的事 vs 目標的偏離度」訊號
  3. 客戶卡關時主動建議「回看你過鏟交接書第 X 段」
  4. 把客戶 6 個月內的互動模式累積，回傳一份「Year-end Mirror」給 compass-and-spade shared-memory
  5. 服務結束契約：客戶可以隨時把 `.compass-spade/` 整個刪掉，但刪掉前 Pocket-Spade 會問一次「真的要走？」（離婚協議式）

- 為什麼這個 specialist「只有 AI 在場才存在」：
  - **沒有 AI 不可能存在**：一個人類顧問不可能 24/7 駐在客戶的 repo、不可能每週主動讀客戶的 git log、不可能在沒有勞動成本前提下持續陪跑 6 個月
  - **它讀的是「客戶實際在做的事」，不是「客戶口頭說的計畫」**——這是人類顧問的盲點，agent 的優勢
  - **它的存在本身改寫了顧問業的計價邏輯**——服務不再是工時，是「常駐契約」

---

## workflow 與 COO 改造計畫

### 要新增的 slash command

- workflow 名稱：`/handoff`
- 做什麼：在 Final QC 通過後執行，把 Pocket-Spade 部署到客戶 repo（生成 `.compass-spade/watch.md` + 客戶 repo 的 commit hook 建議），並交一份「隨身鏟交接書」給客戶

### COO 工作流要不要改

**要改。**

- 三問判斷 → 改為四問判斷（加駐留同意）
- Stage 4 整合 deliverable → 加 Section 6（隨身鏟交接書）
- Stage 5 Final QG → 從 5 條變 6 條（多 Pocket-Spade 部署驗證）
- 增加 Stage 6：Handoff（執行 `/handoff`）

---

## 我刻意不改的（避免替代型合理化）

- 套餐名稱（半鏟 / 全鏟 / 過鏟）不改：這些名字是公司精神的延伸，不是替代型徵兆
- 公司名 compass-and-spade 不改：羅盤與鐵鍏這個隱喻仍成立，只是現在「鐵鍏」會留在客戶家
- 學生互助制不改：對價邏輯（咖啡 / 便當 / 火鍋）不是這次升級的重點

這幾項不改的理由都寫出來了，沒有跳過。
