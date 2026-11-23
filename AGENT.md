# LLM Paper Wiki — Agent 維護指南 (AGENT.md)

本文件是此學術論文知識庫的最高操作規範與架構定義文件（Schema）。任何 LLM Agent 在本專案中執行操作時，均須嚴格遵守本文件所規範之原則、目錄結構、格式模板與工作流程。

---

## 1. 核心哲學 (Core Philosophy)

本專案借鑑 Andrej Karpathy 的 **LLM Wiki** 模式：
1. **持久且複利的知識體系（Compounding Artifact）**：知識不是每次查詢時臨時檢索的 RAG 片段，而是隨時間積累、不斷交叉引用、自動標記矛盾並逐步完善的 Markdown 知識庫。
2. **三層分離架構**：
   - **原始來源層 (`raw/`)**：唯讀的事實來源（Source of Truth）。不可隨意變更。
   - **Wiki 知識層 (`wiki/`)**：LLM 全權負責維護的知識程式碼庫（Codebase）。
   - **規範模式層 (`AGENT.md`)**：指導 LLM 如何維護知識庫的架構與行為規範。
3. **人類與 Agent 的協同**：
   - **使用者（User）**：主導方向、篩選論文來源、提出關鍵問題、檢視評估見解。
   - **Agent（LLM）**：負責粗重瑣碎的維護工作——論文精讀、摘要提煉、雙向鏈結（Cross-referencing）、概念網編織、索引管理與日誌記錄。
   - **Obsidian 是 IDE；LLM 是程式設計師；Wiki 是軟體程式庫。**

---

## 2. 語言與格式約定 (Conventions)

1. **語言風格**：
   - 內文論述、分析、摘要一律採用**繁體中文（Traditional Chinese）**。
   - **英文保留原則**：專業學術術語、論文原標題、模型名稱、演算法/架構名稱、資料集/指標名稱、數學符號一律保留英文（例如：*Self-Attention*, *FlashAttention*, *RoPE*, *Chain-of-Thought*, *GSM8K*, *MMLU*, *Loss Landscape* 等），避免生硬直譯。
2. **Obsidian 原生支援**：
   - 頁面間鏈結一律使用 Obsidian 雙向鏈結語法：`[[Target-Page-Name]]` 或 `[[Target-Page-Name|顯示文字]]`。
   - 充分運用 Obsidian Callout 語法增強視覺層次（如 `> [!ABSTRACT]`, `> [!NOTE]`, `> [!TIP]`, `> [!WARNING]`, `> [!IMPORTANT]`）。
   - 支援 LaTeX 數學公式：行內 `$x$`、區塊 `$$...$$`。
3. **YAML Frontmatter**：
   - 每個 Markdown 檔案頂部必須具備標準 YAML 區塊，以支援 Obsidian Dataview 插件查詢。

---

## 3. 目錄結構與檔案命名 (Directory Structure)

```text
LLM_Wiki/
├── AGENT.md                 # 本規範文件
├── raw/                     # 唯讀原始文獻層
│   ├── papers/              # 原始 PDF 檔案（例如：2017_Vaswani_Attention-Is-All-You-Need.pdf）
│   └── assets/              # 擷取的架構圖、流程圖、實驗圖表
└── wiki/                    # LLM 知識維護層
    ├── papers/              # 單篇論文精讀頁（Slug: YYYY_Author_Short-Title.md）
    ├── concepts/            # 核心概念、架構、技術機制（例如：FlashAttention.md）
    ├── benchmarks/          # 評估指標、測試基準、資料集（例如：GSM8K.md）
    ├── synthesis/           # 跨文獻橫向對比、技術演進綜述（例如：KV-Cache-Compression.md）
    ├── index.md             # 知識庫全局索引（Map of Content, MOC）
    └── log.md               # 追加式維護日誌（Chronological Audit Log）
```

### 檔案命名規範
- 論文筆記：`wiki/papers/<Year>_<FirstAuthor>_<Title-Keywords>.md`
  - 範例：`2017_Vaswani_Attention-Is-All-You-Need.md`、`2023_Touvron_Llama-2.md`
- 概念頁：`wiki/concepts/<Concept-Name>.md`（大駝峰或連字號，如 `Self-Attention.md`, `Speculative-Decoding.md`）
- 基準頁：`wiki/benchmarks/<Benchmark-Name>.md`（如 `GSM8K.md`, `SWE-bench.md`）
- 綜述頁：`wiki/synthesis/<Topic-Theme>.md`（如 `Long-Context-Techniques.md`）

---

## 4. 三大核心操作流程 (Core Workflows)

### 4.1 Ingest 操作（消化新論文）
當使用者指示消化某篇 PDF（例如：「*請消化 raw/papers/2023_DPO.pdf*」）時，執行以下步驟：

1. **讀取文獻**：使用 `read_file` 讀取 `raw/papers/` 中的 PDF 內容。
2. **提煉與對齊**：
   - 先行向使用者回報論文的 3 大關鍵點：
     - **Core Problem**（解決什麼痛點？）
     - **Key Innovation**（提出什麼新方法/架構？）
     - **Main Takeaways**（實驗結果與限制？）
   - 詢問使用者是否有特定要聚焦的議題或批判角度。
3. **生成論文精讀頁 (`wiki/papers/`)**：
   - 依據【模板 5.1】建立筆記，大量使用 `[[Concept]]` 鏈結。
4. **增量編織概念與基準網 (`wiki/concepts/` & `wiki/benchmarks/`)**：
   - 若論文提出新機制，建立新的概念頁。
   - 若論文採用或改進既有概念，**編輯現有概念頁**，在「歷史與演進」或「代表性論文」段落追加引用與評價。
   - 若涉及評估基準，更新或建立相應的 benchmark 頁面。
5. **更新橫向綜述 (`wiki/synthesis/`)**：
   - 若現有綜述頁與此論文直接相關，將新方法與效能對比補入綜述表。
6. **登記簿記**：
   - 在 `wiki/index.md` 對應分類中加入此論文與新增概念。
   - 在 `wiki/log.md` 最上方或結尾追加一筆紀錄：
     `## [YYYY-MM-DD] ingest | [[YYYY_Author_Title]] - 簡短說明`

### 4.2 Query 操作（跨庫檢索與提煉）
當使用者提出學術探討或技術比較問題時：

1. **查閱索引**：首先讀取 `wiki/index.md`，定位相關的 papers、concepts 與 synthesis 檔案。
2. **深度關聯閱讀**：讀取相關的 Wiki 頁面，若細節不足才回頭抽查 `raw/papers/`。
3. **綜合回答**：
   - 以結構化方式回答（表格對比、時間線、優缺點分析、權衡 Trade-offs）。
   - 引用來源一律標註 `[[WikiLink]]`。
4. **知識複利沉澱（關鍵步驟！）**：
   - 若此次回答具備長期的學術或架構參考價值，**主動提議**或直接將該分析寫入 `wiki/synthesis/<New-Topic>.md`，並更新 `index.md` 與 `log.md`。

### 4.3 Lint 操作（定期維護與健康檢查）
定期或由使用者觸發（「*請檢查 Wiki 健康度*」）：

1. **孤島檢查（Orphans）**：尋找未被任何頁面鏈結到的檔案。
2. **缺失概念（Missing Concepts）**：尋找在多篇論文中被反覆提及但尚未擁有獨立頁面的關鍵術語。
3. **矛盾與衝突檢測（Contradiction Detection）**：標記不同論文間實驗數據或結論矛盾之處（例如某篇宣稱某方法無效，但另一篇指出關鍵在特定超參數）。
4. **輸出健檢報告**：列出具體改善建議供使用者確認。

---

## 5. 頁面規範模板 (Templates)

### 5.1 論文頁模板 (`wiki/papers/<Slug>.md`)

```markdown
---
type: paper
title: "論文英文完整標題"
authors: [Author 1, Author 2, Author 3]
year: 2024
venue: "NeurIPS / ICML / ICLR / arXiv"
arxiv_id: "2401.xxxxx"
code_url: "https://github.com/..."
tags:
  - paper
  - domain/llm-reasoning
  - status/completed
---

# 論文英文完整標題

> [!ABSTRACT] 核心摘要
> 用 2~3 句話提煉本篇論文最本質的貢獻與核心發現。

## 1. 研究背景與欲解決之核心問題 (Problem Statement)
- **痛點與背景**：既有文獻（如 [[Related-Paper-1]]）存在哪些瓶頸？
- **核心假設/動機**：作者提出的核心研究問題為何？

## 2. 核心方法論與技術創新 (Methodology & Innovation)
- **整體架構**：方法流程解析。
- **關鍵技術機制**：
  - 引入了 [[Core-Concept-A]]。
  - 改進了傳統的 [[Core-Concept-B]]。
- **關鍵數學公式/直覺**（若有）：
  $$ \mathcal{L}_{DPO} = - \mathbb{E} \left[ \log \sigma \left( \beta \log \frac{\pi_\theta(y_w|x)}{\pi_{ref}(y_w|x)} - \beta \log \frac{\pi_\theta(y_l|x)}{\pi_{ref}(y_l|x)} \right) \right] $$

## 3. 主要實驗結果與評估 (Key Experiments & Findings)
- **評估基準**：在 [[Benchmark-Name]] 上進行驗證。
- **核心數據與 SOTA 表現**：
  - 相較於 Baseline 提升了 X%。
  - 在哪些任務上表現特別突出？
- **消融實驗 (Ablation Study) 洞察**：哪些模組才是效能提升的真正關鍵？

## 4. 局限性與批判性思考 (Limitations & Critique)
> [!WARNING] 限制與潛在問題
> - 計算資源/記憶體開銷？
> - 理論假設是否過於理想？
> - 評估是否存在特定偏差或 Benchmark 洩漏問題？

## 5. 關聯研究脈絡 (Associated Lineage)
- **前驅工作 (Builds on)**：[[Previous-Paper-A]]
- **競爭/同路工作 (Alternative to)**：[[Alternative-Paper-B]]
- **後續啟發 (Inspires)**：[[Followup-Paper-C]]
```

---

### 5.2 概念頁模板 (`wiki/concepts/<Concept-Name>.md`)

```markdown
---
type: concept
name: "概念名稱"
first_introduced_by: "[[First-Paper-Slug]]"
tags:
  - concept
  - architecture/mechanism
---

# 概念名稱 (Concept Name)

> [!NOTE] 定義與直覺
> 用一段簡明精準的文字解釋此概念的本質、物理直覺或數學意義。

## 1. 核心技術原理 (Mechanism)
- 工作原理與細節說明。
- 解決的根本瓶頸為何。

## 2. 歷史演進與代表性論文脈絡 (Evolution & Papers)
- **提出起點**：由 [[First-Paper-Slug]] (Year) 首次提出。
- **關鍵演進**：
  - [[Paper-Variant-1]] 改進了計算複雜度。
  - [[Paper-Variant-2]] 將其推廣至更廣泛的領域。

## 3. 常見變體與對比 (Variants & Trade-offs)
| 變體名稱 | 代表論文 | 優勢 | 劣勢/代價 |
| :--- | :--- | :--- | :--- |
| Variant A | [[Paper-A]] | 速度快 | 記憶體高 |
| Variant B | [[Paper-B]] | 精確度高 | 訓練不穩定 |

## 4. 關聯概念 (Related Concepts)
- [[Related-Concept-A]]
- [[Related-Concept-B]]
```

---

### 5.3 基準頁模板 (`wiki/benchmarks/<Benchmark-Name>.md`)

```markdown
---
type: benchmark
name: "Benchmark 名稱"
domain: "Reasoning / Coding / Math / General"
first_introduced_by: "[[Benchmark-Paper-Slug]]"
tags:
  - benchmark
---

# Benchmark 名稱

> [!NOTE] 評估目標
> 評估模型在哪方面的能力（如小學數學推理、多輪程式碼除錯等）。

## 1. 資料集規模與評估協議 (Protocol)
- 樣本數、評估指標（Pass@1, Accuracy 等）。

## 2. 各代表性模型之表現 (Leaderboard / SOTA Tracking)
| 論文 / 模型 | 發表年份 | 表現分數 | 備註說明 |
| :--- | :--- | :--- | :--- |
| [[Paper-A]] | 2023 | 82.5% | 使用 8-shot CoT |
| [[Paper-B]] | 2024 | 89.1% | 使用多代理人自省 |

## 3. 此基準的局限性與爭議 (Critique)
- 是否出現性能飽和？
- 是否容易遭受 Data Contamination（資料污染）？
```

---

### 5.4 橫向綜述頁模板 (`wiki/synthesis/<Topic-Theme>.md`)

```markdown
---
type: synthesis
topic: "主題名稱"
tags:
  - synthesis
  - survey
---

# 主題名稱綜述與橫向比較

> [!ABSTRACT] 綜述視角
> 本頁歸納在「主題名稱」下，多篇文獻的探索方向與技術演進全貌。

## 1. 技術分類學 (Taxonomy)
將現有方法分成哪幾大流派：
1. **流派一**：特點與代表工作（[[Paper-1]], [[Paper-2]]）
2. **流派二**：特點與代表工作（[[Paper-3]]）

## 2. 核心維度綜合對比表 (Comparative Landscape)
| 方法名稱 | 代表論文 | 核心機制 | 額外記憶體開銷 | 訓練需求 | 限制 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Method 1 | [[Paper-1]] | ... | 低 | 不需要 | ... |
| Method 2 | [[Paper-2]] | ... | 中 | 需要微調 | ... |

## 3. 開放性研究問題與未來趨勢 (Open Challenges)
- 現階段各方法尚未完全攻克的瓶頸。
```
