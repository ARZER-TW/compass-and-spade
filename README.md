# compass-and-spade 羅盤與鐵鍏

> 一人 agent 顧問公司，陪同齡學生挖出「自己現在的領域哪裡會被 agent 吃掉、哪裡還能留著當鏟子」。

I4581 Week 9 個人工作坊作業 by James, 大同大學資工系大三。

## 公司精神

我們不教人用 AI，我們陪人挖：挖自己現在的領域哪裡會被 agent 吃掉、哪裡還能留著當鏟子。

## 服務套餐

| 套餐 | 內容 | 時程 |
|------|------|------|
| 半鏟組 Half-Spade | 1 次對談 + 路線圖 | 48 hr |
| 全鏟組 Full-Spade | 路線圖 + agent SDK demo | 1 週 |
| 過鏟組 Tested-Spade | 路線圖 + demo + 真實使用測試 | 2 週 |

## 公司結構

```
compass-and-spade/
├── spec.md                      公司 spec（Phase B 產出）
├── reflection.md                300 字反思（Phase D）
├── README.md                    本檔
├── company-screenshot.md        公司運作 transcript（代替 PNG，見下方說明）
├── .gemini/
│   ├── agents/
│   │   ├── coo.md               COO（公司營運長）
│   │   ├── route-surveyor.md    路線測繪師
│   │   ├── well-digger.md       鑿井匠
│   │   └── blade-tester.md      試刀人
│   └── commands/
│       ├── intake.md            /intake：接 brief 啟動 COO 三問
│       ├── dispatch.md          /dispatch：派下一位 specialist
│       ├── review.md            /review：COO 審稿
│       └── deliver.md           /deliver：整合最終 deliverable
└── shared-memory/
    └── client/
        ├── current/             進行中案件
        │   ├── brief.md
        │   ├── intake-decision.md
        │   ├── work-orders/
        │   ├── drafts/
        │   ├── review-comments/
        │   └── deliverable.md
        └── archive/             已結案案件
```

## 4 個 agent 一句話

- **COO**：gatekeeper。三問決定接不接、派誰、何時退稿
- **路線測繪師 Route Surveyor**：盤點 skill stack，畫 rot/survive 衝擊圖
- **鑿井匠 Well Digger**：48 小時帶客戶從 0 跑通第一個 agent SDK demo
- **試刀人 Blade Tester**：找 3 個非技術朋友踢 demo，寫失敗點目錄

## Demo Brief 跑完結果

本作業以 demo 客戶「小儀」（企管系大三、輔修資工、想做行銷量化研究碩士）跑完一次全鏟組流程。

最終 deliverable 在 `shared-memory/client/current/deliverable.md`，含 5 個 section：
1. 一頁總結
2. 領域 × agent 衝擊圖
3. SDK demo（Claude Agent SDK + paper 閱讀 agent）
4. 真實測試（本次未啟動，以自我測試 checklist 替代）
5. 30/60/90 天路線圖

## 關於 `company-screenshot.png`

作業要求繳交一張「公司運作中」的 screenshot。本機未安裝 Gemini CLI，整個 Phase C/D 在 Claude（claude.ai 模式）中模擬完成——這是作業 FAQ Q5 允許的 fallback 方式。

替代產出：`company-screenshot.md` — 完整 transcript，呈現 COO 三問判斷、specialist 派工、草稿審查、final deliver 整個流程。reflection.md 已說明此 fallback。

## 已知缺口（v1）

- 計價邏輯只是隱喻，未實際定價
- 試刀人尚未在真實 case 啟動過
- 「3 個非技術測試者」的調度機制未建
- 半鏟組的「免費 vs 對價」拉扯未解

預計 W2-W4 對齊型客戶測試會逼出更多缺口。

## 繳交清單

| 檔案 | 狀態 |
|------|------|
| spec.md | done |
| company-screenshot.md（代 PNG） | done |
| shared-memory/client/current/brief.md | done |
| shared-memory/client/current/deliverable.md | done |
| reflection.md | done |
