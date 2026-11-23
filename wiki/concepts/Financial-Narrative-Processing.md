---
type: concept
name: "Financial Narrative Processing (FNP)"
first_introduced_by: "[[2025_Du_NLP-in-Finance-A-Survey]]"
tags:
  - concept
  - domain/financial-nlp
  - summarization
  - information-extraction
---

# 金融敘事處理 (Financial Narrative Processing, FNP)

> [!NOTE] 定義與直覺
> 金融敘事處理（FNP）是金融 NLP 的重要核心子領域，專門聚焦於從企業非結構化的長篇敘事文本（如財報 MD&A 管理階層討論與分析、法說會問答逐字稿、永續報告書）中，提取無法直接藉由數值報表量化，但對企業經營、風險與估值具有重大影響的關鍵故事、因果關係與質化揭露。

---

## 1. 核心任務分類 (Core Task Categorization)

依據 [[2025_Du_NLP-in-Finance-A-Survey]] 的分類，FNP 主要涵蓋兩大核心任務：

### 1.1 金融文本自動摘要 (Financial Text Summarization)
- **抽取式摘要 (Extractive Summarization)**：從長篇年報（數百頁）中選取最具代表性的語句或章節段落。常用方法包括 TF-IDF + K-Means 分群、Sentence-BERT 句向量分群、基於章節權重的 K-Maximal Word Allocation。
- **生成式摘要 (Abstractive Summarization)**：以神經網路或 LLM 重新組織語句，產出精簡、無冗餘的高密度摘要。
- **混合式與跨模態架構 (Hybrid & Table-Text)**：如 FINDSum 與 ECTSum 基準，融合財報表格數據與敘事文字生成重點條列式（Telegram-style）摘要。

### 1.2 金融資訊擷取 (Information Extraction, IE)
- **企業事件抽取 (Corporate Event Extraction)**：自動識別併購（M&A）、融資、破產、法律訴訟、高層異動等關鍵事件（如 SENTiVENT 語料庫）。
- **實體與因果關係辨識 (Entity & Causal Extraction)**：
  - 金融專用命名實體辨識（FinNER）：自動標記公司代號、監管機構、法規條款、幣別、財報項目。
  - 因果關係挖掘（Causality Detection）：從新聞串流中推導「事件 A 導致市場變數 B 波動」的因果網絡（如 FinCausal 競賽、Predictive Causal Graph）。
- **知識圖譜整合 (Knowledge Graph Integration)**：將抽取出的實體、關係與事件構建為關係圖譜（如關聯方交易網絡、供應鏈網絡），輔助詐欺偵測與事件驅動量化交易。

---

## 2. 歷史代表性研究與工作坊 (Key Milestones)
- **FNP Workshop 系列**：自 2018 年起每年於 LREC / EMNLP 等頂級 NLP 會議舉辦，推動了 FNS Shared Task 等基準資料集的普及。
- **DiMSum & LLM-based Summarization**：引入少樣本 RAG 機制，輔助 LLM 精確識別財報中的「敘事性段落」與「非敘事性格式」，顯著提升摘要品質。

---

## 3. 關聯研究與頁面 (Related Links)
- 綜述文獻：[[2025_Du_NLP-in-Finance-A-Survey]]
- 相關技術：[[Financial-LLM]], [[FinBERT]]
- 評估指標：ROUGE-1, ROUGE-2, ROUGE-L, F1-Score
- 橫向全景：[[Financial-NLP-Landscape]]
