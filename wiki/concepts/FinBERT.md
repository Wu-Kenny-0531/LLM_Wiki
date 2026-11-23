---
type: concept
name: "FinBERT"
first_introduced_by: "[[2025_Du_NLP-in-Finance-A-Survey]]"
tags:
  - concept
  - model
  - transformer
  - domain/financial-nlp
---

# FinBERT

> [!NOTE] 定義與直覺
> FinBERT 是將通用預訓練語言模型（BERT）透過大規模金融專業領域語料庫（包括路透社財經新聞、Yahoo Finance 資訊、上市公司 10-K / 10-Q 財報與法說會電話會議逐字稿）進行持續領域適應性預訓練（Domain-adaptive Pre-training）所衍生的一系列金融專用語言模型。

---

## 1. 核心動機與工作原理 (Motivation & Architecture)
- **通用 BERT 在金融領域的缺陷**：
  - 一般詞彙與金融專有名詞分詞切分不合理（Tokenization 碎裂問題）。
  - 對於具備強烈金融語境偏差的詞彙（如 *bearish*, *bullish*, *default*, *underperform*, *long/short*）無法掌握其真實含義。
- **代表性版本演進**：
  1. **FinBERT (Araci, 2019)**：聚焦在金融情感分類，在 Financial PhraseBank 基準測試上大幅勝過原始 BERT 與 LSTM 架構。
  2. **FinBERT (Liu et al., IJCAI 2020)**：採用更龐大的金融語料庫進行預訓練，釋出開源權重，並擴展至 FinNER（實體辨識）與金融文字分類等多項下游任務。
  3. **FinBERT-MRC (Zhang & Zhang, 2023)**：將金融命名實體抽取轉化為機器閱讀理解（Machine Reading Comprehension, MRC）框架，顯著改善金融實體抽取的精確度。
  4. **FinBERT-ESG (Schimanski et al., 2024)**：特化用於環境、社會與公司治理（ESG）揭露議題的分類與評估。

---

## 2. 效能優勢與局限性 (Strengths & Limitations)
- **優勢**：
  - 參數量小（~110M 參數），推論速度極快，硬體門檻低，適合高頻量化管線與私有伺服器低延遲部署。
  - 在短文本情緒分類任務上準確度極高，甚至在特定專門基準上優於未經微調的大型通用模型（如 GPT-3）。
- **局限性**：
  - 模型容量與上下文長度（Context Window）受限於標準 BERT 架構（512 Tokens），難以直接閱讀完整長篇財報。
  - 缺乏像現代 [[Financial-LLM]] 一樣的複雜數值推理、長鏈思考（CoT）與自然多輪對話能力。

---

## 3. 關聯研究與頁面 (Related Links)
- 綜述文獻：[[2025_Du_NLP-in-Finance-A-Survey]]
- 相關概念：[[Financial-Sentiment-Analysis]], [[Financial-Narrative-Processing]], [[Financial-LLM]]
- 評估基準：[[Financial-Sentiment-Benchmarks]]
