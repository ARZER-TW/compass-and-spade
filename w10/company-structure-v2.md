# Company Structure v2

> 本機未安裝 `tree`，以下為 `.gemini/` 與 root 的純文字 tree。可直接截圖此檔當作 `company-structure-v2.png` 替代。

## `.gemini/` 結構（v2）

```
.gemini/
├── agents/
│   ├── coo.md                ← v2 更新（三問 → 四問、加 Stage 6）
│   ├── route-surveyor.md     ← 不變
│   ├── well-digger.md        ← 不變
│   ├── blade-tester.md       ← v2 輕修（加 Pocket-Spade 駐留前提）
│   └── pocket-spade.md       ← v2 新增（原生型，only-AI-can-exist）
└── commands/
    ├── intake.md             ← 不變
    ├── dispatch.md           ← 不變
    ├── review.md             ← 不變
    ├── deliver.md            ← 不變
    └── handoff.md            ← v2 新增（Stage 6 部署 Pocket-Spade）
```

## Root（v2 全貌）

```
compass-and-spade/
├── README.md
├── spec.md                   ← v2 改 5 區（A/B/C/D/E 全部有結構變化）
├── .gemini/                  ← 上方詳列
├── shared-memory/
│   └── client/
│       ├── current/          ← 清空（新案件用）
│       └── archive/
│           └── 2026-05-25-xiaoyi/   ← Week 9 demo case
├── w9/                       ← Week 9 工作坊產出
│   ├── brief.md
│   ├── deliverable.md
│   ├── reflection.md
│   └── company-screenshot.md
└── w10/                      ← Week 10 工作坊產出
    ├── notes.md
    ├── insights.md
    ├── upgrade-spec.md
    ├── aligned-client-brief.md
    ├── client-brief-v1-output.md
    ├── client-brief-v2-output.md    ← Section 5 產出
    ├── company-structure-v2.md      ← 本檔
    ├── v2-summary.md                ← Section 6 產出
    └── reflection.md                ← Section 5+6 產出
```

## v1 vs v2 結構性差異一覽

| 區塊 | v1 | v2 | 差異類型 |
|------|----|----|---------|
| `.gemini/agents/` | 4 agents | 5 agents | 數量 +1（Pocket-Spade） |
| `.gemini/commands/` | 4 commands | 5 commands | 數量 +1（handoff） |
| spec A 區 manifesto | 「我們陪人挖」 | 「我們在你家裝會挖的東西」 | 隱喻換軸（替代型 → 原生型） |
| spec B 區 套餐 | 一次性交付 | 一次性交付 + Pocket-Spade 駐留期 | 計價邏輯改變 |
| spec D 區 COO 判斷 | 三問 | 四問（加駐留同意） | 篩選機制加新軸 |
| spec D 區 stages | 5 stages | 6 stages（加 Handoff） | 流程加新階段 |
| spec E 區 deliverable | 5 sections | 6 sections（加隨身鏟交接書） | 結構擴增 |
| Final Quality Gate | 5 條 | 6 條（加 Pocket-Spade ping 測試） | 驗收標準擴增 |

5 區裡有 5 區（全部）有結構性變化，達到品質規範「至少 2 區」的條件並超出。
