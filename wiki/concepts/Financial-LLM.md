---
type: concept
name: "Financial Large Language Models (Financial LLMs)"
first_introduced_by: "[[2025_Du_NLP-in-Finance-A-Survey]]"
tags:
  - concept
  - model
  - llm
  - generative-ai
  - domain/financial-nlp
---

# 金融大語言模型 (Financial Large Language Models, Financial LLMs)

> [!NOTE] 定義與直覺
> 金融大語言模型（Financial LLMs）是指具有數十億至數千億參數、經過海量通用與金融領域資料預訓練或指令微調（Instruction Tuning）的自回歸生成式 Transformer 模型。相較於早期僅用於分類或標註的小型模型（如 [[FinBERT]]），Financial LLMs 具備長文本理解、複雜數值推理、程式碼生成（代碼化量化分析）與開放式多輪對話能力。

---

## 1. 核心流派與代表性模型 (Paradigms & Models)

依據 [[2025_Du_NLP-in-Finance-A-Survey]] 的梳理，目前 Financial LLMs 呈現三大技術發展流派：

### 1.1 從頭全量預訓練 (Pre-training from Scratch)
- **代表：BloombergGPT (Wu et al., 2023, 50B)**
  - 訓練資料：包含 3,630 億 Tokens 的彭博自有金融文檔（新聞、財報、研究報告、社交文字）加上 3,450 億通用公開語料。
  - 特點：在金融領域 NLP 任務（FSA、NER、QA）均超越當時同等規模的通用模型，但算力成本極為高昂（需數百萬美元雲端訓練成本）。

### 1.2 領域指令微調 (Domain Instruction-Tuning)
- **代表：Instruct-FinGPT / FinGPT 系列 (Zhang et al., 2023)**
  - 做法：基於開源開源基礎模型（如 LLaMA、Flan-T5、Mistral），運用 LoRA 或 QLoRA 等參數高效微調（PEFT）技術，在精心標註的金融指令資料集上微調。
  - 優勢：訓練成本大幅降低，能在消費級或一般企業伺服器上快速適配專屬金融業務。

### 1.3 檢索增強生成與多代理人 (RAG & Multi-Agent)
- 金融領域對**幻覺（Hallucination）是零容忍**的。直接依賴 LLM 的內部權重記憶極容易捏造數據或錯認會計科目。
- 現代主流金融 LLM 系統普遍採用 **RAG（Retrieval-Augmented Generation）** 機制：
  - 先檢索上市公司 SEC 申報原始文件或權威數據庫，將真實上下文連同問題輸入給 LLM。
  - 結合多代理人協同架構（Multi-Agent System）：分別指派資料檢索 Agent、財務比率計算 Agent、風控審核 Agent，相互查核以達到高度可信賴性。

---

## 2. 核心技術挑戰 (Open Challenges)
1. **數值推理與表格處理 (Numerical & Tabular Reasoning)**：純文字 LLM 面對複雜多欄位財報容易出現行/列錯置，需要透過特化訓練或程式碼輔助推理（Program-Aided Language models / Code Interpreter）解決。
2. **法規遵循與資料隱私 (Privacy & Compliance)**：客戶財務資料受到 GDPR、金管法規高度嚴管，模型不能有潛在的資料洩漏或訓練集記憶反求風險。
3. **高延遲與成本**：在即時高頻交易與做市商業務中，LLM 的推論延遲（秒級）遠不如傳統規則或輕量神經網路（毫秒級），因此目前多被定位於非即時策略規劃、投資研究與研究報告生成。

---

## 3. 關聯研究與頁面 (Related Links)
- 綜述文獻：[[2025_Du_NLP-in-Finance-A-Survey]]
- 前身模型：[[FinBERT]]
- 核心應用：[[Financial-Sentiment-Analysis]], [[Financial-Narrative-Processing]]
- 基準評估：[[Financial-QA-Benchmarks]]
- 橫向全景：[[Financial-NLP-Landscape]]
