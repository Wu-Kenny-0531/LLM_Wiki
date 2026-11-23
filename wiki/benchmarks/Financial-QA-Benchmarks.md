---
type: benchmark
name: "Financial Question Answering Benchmarks"
domain: "Financial Question Answering & Numerical Reasoning"
first_introduced_by: "[[2025_Du_NLP-in-Finance-A-Survey]]"
tags:
  - benchmark
  - question-answering
  - numerical-reasoning
  - domain/financial-nlp
---

# 金融問答與數值推理基準測試 (Financial QA Benchmarks)

> [!NOTE] 評估目標
> 一般閱讀理解（如 SQuAD）只需在文本中精確比對並抽取答案字串（Span Extraction）。然而金融領域的問答大多涉及**「多步算術計算（加減乘除、複合成長率）」**以及**「文字與表格混合（Hybrid Table-Text）的結構理解」**。本類別基準用於評估模型跨異質資訊的深層數值推理能力。

---

## 1. 核心代表性基準資料集 (Key Datasets)

依據 [[2025_Du_NLP-in-Finance-A-Survey]]，金融 QA 最具挑戰性的基準包括：

### 1.1 FinQA (Chen et al., EMNLP 2021)
- **資料來源**：美國標準普爾 500（S&P 500）企業公開 10-K 財報。
- **任務設計**：給予包含文字段落與財務表格的財報頁面，回答需要多步計算的專業財務問題。
- **特色**：包含人工標註的完整數學計算符號程式（Domain Specific Language / Python-like Program）。
- **評估指標**：
  - **執行準確率 (Execution Accuracy)**：程式運算結果是否與標準答案一致。
  - **程式準確率 (Program Accuracy)**：生成的符號運算樹是否在數學邏輯上等價。
- **代表性模型表現**：
  - RoBERTa-large + FinQANet：Execution Accuracy 達約 61.2%，Program Accuracy 達 58.9%。

### 1.2 TAT-QA (Zhu et al., ACL 2021)
- **資料來源**：真實企業財務報告。
- **任務形式**：專注於混合型內容（Tabular And Textual content）。問題類型涵蓋：數值單點抽取、多格數值比較、聚合運算（Sum, Average）、多步算術運算。
- **評估指標**：完全匹配精確率（Exact Match, EM）、考量數值偏差的 Numeracy-focused F1。
- **代表性模型**：
  - TAGOP：能夠在文字與表格混合結構上進行序列標註、聚集運算元選擇與尺度縮放預測，達到 EM 50.1%, F1 58.0%。

### 1.3 ConvFinQA (Chen et al., EMNLP 2022)
- **任務升級**：將 FinQA 擴展為**「多輪交談式金融問答（Conversational Financial QA）」**。
- **核心挑戰**：模型必須追蹤上一輪的計算結果、代名詞指涉與上下文狀態，形成一條連貫的多步數值推理鏈（Chain of Numerical Reasoning）。

---

## 2. 評估指標說明 (Metrics)
- **Exact Match (EM)**：預測字串完全等於真實答案時得 1 分，否則 0 分。
- **Numeracy-focused F1**：專為數值問答設計，當數值出現任何細微錯誤或有效位數不符時，該項 F1 嚴格歸零，避免單純依靠語言平滑度獲得虛假高分。

---

## 3. 關聯頁面 (Related Links)
- 綜述文獻：[[2025_Du_NLP-in-Finance-A-Survey]]
- 關聯技術：[[Financial-LLM]], [[Financial-Narrative-Processing]]
- 橫向全景：[[Financial-NLP-Landscape]]
