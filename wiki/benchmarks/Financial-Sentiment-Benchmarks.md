---
type: benchmark
name: "Financial Sentiment Benchmarks"
domain: "Financial Sentiment Analysis (FSA)"
first_introduced_by: "[[2025_Du_NLP-in-Finance-A-Survey]]"
tags:
  - benchmark
  - sentiment-analysis
  - domain/financial-nlp
---

# 金融情緒分析基準測試 (Financial Sentiment Benchmarks)

> [!NOTE] 評估目標
> 評估自然語言處理模型與演算法在金融專業語境下，判讀語句情緒極性（正面 Positive、負面 Negative、中立 Neutral）或預測精確情緒連續分數的能力。

---

## 1. 三大經典基準資料集 (Major Benchmarks)

依據 [[2025_Du_NLP-in-Finance-A-Survey]] 所述，金融情緒分析研究主要收斂在以下三大知名基準：

### 1.1 Financial PhraseBank (Malo et al., 2014)
- **資料來源**：從 LexisNexis 取得的 4,845 條英文財經新聞標題與句子。
- **標註方式**：由 16 位具有金融與經濟專業背景的研究員獨立標註情感標籤（Positive, Neutral, Negative）。
- **協商同意切分**：
  - 100% Agreement（所有標註者一致同意）
  - 75% Agreement
  - 66% Agreement
  - 50% Agreement
- **評估指標**：Accuracy, Macro-F1。
- **指標表現**：
  - 傳統機器學習（SVM/LR）：Accuracy 約 76% ~ 83%
  - [[FinBERT]] (Araci 2019 / Liu 2020)：Accuracy 達 86% ~ 94%, F1 達 0.93
  - LLM Zero-shot (ChatGPT / GPT-4)：Accuracy 約 80% ~ 96%（依 Prompting 設計而異）

### 1.2 SemEval 2017 Task 5 (Cortis et al., 2017)
- **評估任務**：微網誌（Microblogs, 如 StockTwits）與財經新聞標題的細粒度情緒連續分數預測（區間為 $[-1.0, 1.0]$）。
- **特點**：強調短文字、非正規縮寫（如 \$AAPL、ticker symbols）與目標層面級（Target-level）情緒。
- **評估指標**：加權餘弦相似度（Weighted Cosine Similarity, WCS）。
- **指標表現**：
  - 傳統特徵工程模型：WCS 約 0.70 ~ 0.77
  - 深度混合模型與預訓練模型（RoBERTa / FinBERT）：WCS 提升至 0.84+

### 1.3 FiQA 2018 Task 1 (Maia et al., 2018)
- **評估任務**：針對金融論壇貼文與財經新聞標題，進行目標實體之層面級情緒評分（Aspect-level Sentiment Analysis）。
- **評估指標**：均方誤差（Mean Squared Error, MSE）、判定係數（$R^2$）。
- **指標表現**：[[FinBERT]] 與經過金融多源知識注入的微調模型（Du et al., 2023）達到極低 MSE（$\approx 0.049$）。

---

## 2. 評估指標公式定義 (Evaluation Metrics)

### 加權餘弦相似度 (Weighted Cosine Similarity, WCS)
$$ \text{WCS} = \frac{|P|}{|G|} \times \frac{\sum_{i=1}^n (G_i \times P_i)}{\sqrt{\sum_{i=1}^n G_i^2} \times \sqrt{\sum_{i=1}^n P_i^2}} $$
其中 $P$ 為模型預測情緒向量，$G$ 為人工標註真實向量。

---

## 3. 關聯頁面 (Related Links)
- 綜述文獻：[[2025_Du_NLP-in-Finance-A-Survey]]
- 關聯技術：[[Financial-Sentiment-Analysis]], [[FinBERT]], [[Financial-LLM]]
