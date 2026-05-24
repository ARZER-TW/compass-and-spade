# 路線測繪師草稿 — 小儀

## 客戶 persona（一句話）

企管系大三、輔修資工、Python 入門級、目標申請美國行銷量化研究碩士的學生，當前最痛是讀 paper 慢。

## 技能 stack 盤點

### 底層通用能力（survive 機率高）

- 英文閱讀（可讀完 30 頁 paper，瓶頸不在英文）
- 商管研究框架思維（5C、4P、SWOT 這類結構化拆解能力）
- 學習韌性（願意硬讀 4-5 小時）

### 中層領域知識

- 消費者行為理論（survive）
- 量化研究方法論（survive，但要會操作工具才有競爭力）
- 統計基礎（介於 rot 與 survive，看她走到多深）

### 上層具體工具

- Python 入門（hello world 級）：survive 機率視乎她接下來的選擇
- 沒用過任何資料分析工具（R、SPSS、Stata）：這是該補的洞
- 沒用過任何 agent / LLM SDK：這是這次的切入點

## rot / survive 衝擊圖

| 客戶現有 | 3 年 rot 機率 | 對應 agent / AI 威脅 | 建議行動 |
|---------|--------------|--------------------|---------|
| 硬讀 paper 整理 | 80% | Elicit, Consensus, SciSpace | 從現在開始用，並學會「指導 agent 找重點」 |
| 寫 literature review 摘要 | 70% | Elicit 已能做到 80% 品質 | 學會用 agent 起草、自己審稿、補關鍵脈絡 |
| 設計問卷量表 | 30% | 有 AI 助力但專業判斷仍重要 | 持續累積，但用 AI 加速「文獻支持的量表挑選」 |
| 量化分析（迴歸、SEM） | 20% | AI 在執行端加速，但理解仍需自己 | 持續學，用 AI 解釋輸出 |
| 商業 insight 與消費者敘事 | 10% | 高度仰賴人類脈絡 | 這是她未來的護城河 |

## 引用的 agent 產品（查證連結）

1. **Elicit** (elicit.com) — 學術研究 agent，主打找 paper、做 literature review
2. **Consensus** (consensus.app) — 從 paper 中抽出「研究結論」並標註統計強度
3. **SciSpace** (scispace.com) — 整篇 paper 解釋 + Q&A，介面對非技術背景友善
4. **Claude Agent SDK** (anthropic.com) — 她要自己做的話最適合的起點
5. **NotebookLM** (notebooklm.google) — 已存在的免費版本，可作為 baseline 對照

## 90 天微路線

### 第 1-30 天（6 月）：跑通她自己的 paper agent

- **Milestone**: 她在自己 M1 Mac 上跑通 Claude Agent SDK 的 demo，能輸入一篇 PDF 輸出「對她研究主題的相關度」
- **驗收標準**: 6/2 meeting 上能對指導老師示範 1 分鐘 input → output

### 第 31-60 天（7 月）：把 demo 變成她日常工具

- **Milestone**: Demo 進化成命令列工具，她每讀一篇 paper 都跑一次，累積一個 paper note 資料夾
- **驗收標準**: 累積至少 15 篇 paper 的處理紀錄，且她能說出「哪 3 篇 agent 抓的重點和她重讀後判斷不同」

### 第 61-90 天（8 月）：拿一份成果出去

- **Milestone**: 把累積的 paper note 整理成研究計畫初稿（給碩士申請用），其中至少 5 處引用「她用 agent 找出但學長姐沒提過的 paper」
- **驗收標準**: 指導老師對研究計畫給出實質意見（不是「再修一下」這種敷衍評語）

## 她可能不會喜歡聽，但我必須說

1. **學長姐說「硬讀」是錯的——但她們不會承認。** 她要做好心理準備：當她用 agent 加速 paper 閱讀並開始進步時，學長姐圈會出現「你這樣不紮實」的聲音。這聲音的真實內容不是「你做錯了」，是「我當年沒這樣做」。她要學會分辨。

2. **她的 Python 不夠。** Hello world 級別撐不過第 60 天。建議在 6 月底前補完 Python 中階（list comprehension、檔案 I/O、基本 OOP），否則第 31-60 天會卡死。

## 給 COO 的備註

- 我刻意沒寫進路線圖：她該不該轉資工系（這是她的決定，不是路線圖該回答的）
- 我擔心她把 agent 工具當「捷徑」而不是「放大鏡」。鑿井匠交付時，建議在 README 用一句話標清楚：「這個 demo 是讓你看得快，不是讓你不用想」

---

[APPROVED by COO @ 2026-05-26 21:00]

**COO 審查紀錄**：通過 Quality Gate 1（引用 5 個產品，超出 3 個下限）、Quality Gate 2（3 個 milestone 都有驗收標準）。「她可能不會喜歡聽」段落很關鍵，整合到 deliverable 一頁總結的 callout。
