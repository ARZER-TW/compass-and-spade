# 鑿井匠草稿 — 小儀

## SDK 選擇與理由

**選定**：Claude Agent SDK (Python) + 輕量 file-based memory

**理由**：
- 她會 Python（雖然只到 hello world，但語法不會擋路）
- Anthropic Claude 在「長 PDF 理解」上是當前最強的（200K token context 一篇 30 頁 paper 綽綽有餘）
- Agent SDK 支援 file system tool，能讓 agent 自己讀 PDF
- File-based memory 比向量資料庫簡單 10 倍，她現階段不需要 RAG

**沒選 LangGraph 的原因**：抽象層太多，她現階段會被 graph / state / node 這些概念淹沒，反而學不會 agent 的本質。

**沒選 OpenAI Assistants 的原因**：file_search 對學術 PDF 的效果經實測在 Anthropic 之下，而且她要做的是「持續累積 paper 脈絡」，Anthropic 的 long context + memory file 模式更直觀。

## Step-by-step 指南

### Step 1：環境設定（預期 15 分鐘）

```bash
# Mac
brew install python@3.11  # 若已有可略
python3 -m venv ~/paper-agent-env
source ~/paper-agent-env/bin/activate
pip install anthropic pypdf
```

**卡關預警**：M1 Mac 用 brew 安裝 Python 時可能出現 PATH 衝突。如果 `which python3` 指向系統 Python，要重新打開 terminal 或加 `export PATH="/opt/homebrew/bin:$PATH"` 到 `.zshrc`。

### Step 2：取得 Anthropic API key（預期 10 分鐘）

到 console.anthropic.com 註冊，前往 API keys 頁面建立一把 key。

```bash
export ANTHROPIC_API_KEY="sk-ant-..."
# 加到 ~/.zshrc 才不會每次重開都要設
```

**卡關預警**：免費額度約 $5，跑一篇 30 頁 paper 約消耗 $0.05-0.10。她預算內可跑 50-100 篇。額度用完前要記得儲值，否則 demo 會無聲失敗。

### Step 3：Hello world demo（預期 30 分鐘）

最小可跑版本 `paper_agent.py`：

```python
import anthropic
from pypdf import PdfReader
import sys
import json
from pathlib import Path

client = anthropic.Anthropic()

# 客戶研究主題（之後可改成從檔案讀）
RESEARCH_TOPIC = """
我研究的主題：消費者面對 AI 推薦時的信任形成機制。
特別關心：(1) 演算法透明度的影響、(2) 推薦失敗後的修復、(3) 跨文化差異。
"""

def read_pdf(pdf_path: str) -> str:
    reader = PdfReader(pdf_path)
    return "\n".join(page.extract_text() for page in reader.pages)

def analyze_paper(pdf_path: str):
    text = read_pdf(pdf_path)
    response = client.messages.create(
        model="claude-sonnet-4-6",
        max_tokens=2000,
        system=f"""你是小儀的 paper 閱讀助手。她的研究主題：

{RESEARCH_TOPIC}

針對她丟給你的每一篇 paper，輸出三件事：
1. 100 字摘要
2. 相關度評分 (0-10) 與理由
3. 她該重點看的 3 段（用 paper 原文標示 section 名稱）
""",
        messages=[{"role": "user", "content": f"以下是 paper 內容：\n\n{text}"}]
    )
    return response.content[0].text

if __name__ == "__main__":
    result = analyze_paper(sys.argv[1])
    print(result)
    # 同時存到 notes/ 累積
    notes_dir = Path("notes")
    notes_dir.mkdir(exist_ok=True)
    note_path = notes_dir / f"{Path(sys.argv[1]).stem}.md"
    note_path.write_text(result)
    print(f"\n[Saved to {note_path}]")
```

跑法：
```bash
python paper_agent.py path/to/some_paper.pdf
```

**卡關預警**：
1. PDF 是 scanned image（圖片，不是真文字）時 pypdf 會回空字串。要先在 paper 上 Ctrl+F 試能不能搜尋——能搜尋才有文字層。
2. 部分舊 paper 的 PDF 編碼會讓 pypdf 抓到亂碼。發生時建議用 pdfplumber 替代。
3. API key 沒設正確時，錯誤訊息是 401 但訊息細節不明顯。第一次跑請先 `echo $ANTHROPIC_API_KEY` 確認。

### Step 4：客戶領域客製化（預期 90 分鐘）

升級點 1：研究主題從外部檔案讀，方便她隨時改。

```python
RESEARCH_TOPIC = Path("research_topic.md").read_text()
```

升級點 2：累積讀過的 paper 名單作為 context。

```python
# 讀 notes/ 內所有歷史筆記，當 context 給 agent
def get_history() -> str:
    notes = Path("notes").glob("*.md")
    return "\n---\n".join(f"# {n.stem}\n{n.read_text()}" for n in notes)
```

把 `get_history()` 加到 system prompt，告訴 agent「以下是她讀過的 paper 摘要」，這就是她要的「持續記得脈絡」。

升級點 3：相關度低於 5 分的 paper 自動標記「可跳過」存到 `notes/skip/`，不污染主筆記。

### Step 5：Demo 給人看（預期 30 分鐘）

對指導老師示範流程（1 分鐘）：

1. 開 terminal，cd 到 paper-agent 資料夾
2. 拖一篇 paper PDF 到 terminal（自動填 path）
3. `python paper_agent.py [path]`
4. 等 10 秒，看 output
5. 開 `notes/[paper-name].md` 顯示已存的筆記
6. 列 `notes/` 整個資料夾，顯示「她至今累積的 paper 脈絡」

## 客戶 GitHub repo

`https://github.com/[小儀-github]/paper-agent-mvp`

README 結構：
- Section 1：這個 demo 在做什麼（給指導老師看的版本，純白話）
- Section 2：怎麼跑（給她未來自己重看用）
- Section 3：我卡關過的 3 個點（M1 PATH、scanned PDF、API key 401）

## 客戶自我測試 checklist

| # | 項目 | 通過判準 |
|---|------|---------|
| 1 | 全新 terminal 跑 `python paper_agent.py [paper.pdf]` | 60 秒內看到 output |
| 2 | 跑 3 篇與研究主題相關的 paper | 相關度評分都 >= 6 |
| 3 | 跑 1 篇不相關的 paper（隨便挑一篇其他領域的） | 相關度評分 <= 4 |
| 4 | 改 `research_topic.md` 後再跑同一篇 paper | output 的相關度判斷不同 |
| 5 | 連續跑 5 篇後，看第 6 篇時 agent 是否引用前 5 篇脈絡 | system prompt 內有 history |
| 6 | 對指導老師示範 1 分鐘流程 | 老師看完沒問「這在幹嘛」 |
| 7 | 一篇 scanned PDF（故意找一篇） | 看到友善錯誤訊息，不是 crash |

她在 6/1 一天內跑完這 7 項，6/2 就有底氣去 meeting。

## 跑通證明

（陪跑 log 見下方）

## 客戶口述 demo 內容紀錄

5/31 21:30，小儀視訊：「這個 demo 會吃 PDF，看完整篇 paper 之後給我三件事：摘要、跟我研究主題的相關度、它覺得我該重點看哪三段。背後它記得我之前讀過哪些 paper，所以判斷會越用越準。」

[通過 Quality Gate 1：她沒看筆記、用自己的話講清楚]

## 陪跑 log

- **5/27 19:00**：環境設定。卡在 PATH，10 分鐘解。
- **5/28 20:30**：跑 hello world，第一篇 paper 成功。她興奮喊「它真的懂我的研究主題」。提醒她那是因為 system prompt 寫了主題。
- **5/29 21:00**：scanned PDF 卡關。換 pdfplumber 解。她學會「PDF 不是 PDF」的概念。
- **5/30 19:30**：客製化升級。她自己加了第 4 個 output（「這篇 paper 提到的 3 個量表，我該不該用？」）——這是我沒想到的延伸，記下來給 COO。
- **5/31 21:30**：對我視訊 1 分鐘示範通過。

## 給 COO 的備註

- 她自己加的「量表挑選」延伸功能，是個信號：她下個套餐可能會升級到「自己改 agent」。記在客戶檔案。
- 我擔心的：她的 Python 還是太弱，第 31-60 天要做「累積資料夾管理」時會撞牆。建議 deliverable 一頁總結提醒她 6 月底前補 Python 中階。
- 試刀人沒啟動，自我測試 checklist 是替代品。但這只能驗證她自己的使用——真正的「給朋友用」測試還是缺，她未來如果想推給同學用，要回頭補過鏟組。

---

[APPROVED by COO @ 2026-05-31 22:00]

**COO 審查紀錄**：通過所有 Quality Gate。陪跑 log 寫得實。「她可能不喜歡聽」段落沒漏（自我測試第 4 項就是逼她面對「改主題會改判斷」這個事實）。給客戶的 Python 補課提醒採納，整合到 deliverable 下一步路線圖。
