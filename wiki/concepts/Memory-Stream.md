---
type: concept
name: "Memory Stream"
first_introduced_by: "[[2023_Park_Generative-Agents]]"
tags:
  - concept
  - memory
  - architecture
  - domain/abm
---

# 記憶串流 (Memory Stream)

> [!NOTE] 定義與直覺
> 記憶串流（Memory Stream）是生成式代理人架構中儲存長期經歷的核心資料結構。它以時間為序列，將代理人在虛擬世界中的所有感知、觀察、對話、計劃與反思，統一以自然語言（Natural Language）記錄成記憶物件（Memory Objects）。

---

## 1. 記憶物件的結構 (Memory Object Schema)
在記憶串流中，每個記憶條目包含以下核心欄位：
- **內容描述 (Description)**：以自然語言紀錄事件（如「John 在花園遇見兒子 Eddy 並詢問作業進度」）。
- **建立時間戳 (Creation Timestamp)**：模擬世界的虛擬時間。
- **最後訪問時間戳 (Last Access Timestamp)**：該記憶最近一次被檢索或啟用的時間。
- **重要度分數 (Importance Score)**：在記憶誕生時由 LLM 評定的核心權重（1~10 分）。

---

## 2. 三維動態檢索演算法 (Three-Dimensional Retrieval)

面對龐大的記憶歷史，系統在每個決策時間步必須精準提取最關鍵的記憶輸入至 LLM 的 Prompt 中。檢索公式如下：

$$ \text{Retrieval Score} = \alpha_{\text{recency}} \cdot \text{Recency} + \alpha_{\text{importance}} \cdot \text{Importance} + \alpha_{\text{relevance}} \cdot \text{Relevance} $$

各維度經過 Min-Max 正規化至 $[0, 1]$ 區間：

1. **新鮮度 (Recency)**：
   - 採用指數衰減（Exponential Decay）：$f(\Delta t) = 0.995^{\Delta t}$（$\Delta t$ 為上次被檢索以來的虛擬小時數）。
   - 確保剛發生的事件（如幾分鐘前的對話）優先停留在代理人的注意力焦點內。
2. **重要度 (Importance)**：
   - 區分日常瑣碎雜訊與人生關鍵時刻。
   - 透過 Prompt 讓 LLM 自動評定：「*在 1 到 10 的刻度上，1 代表極其平庸（如刷牙），10 代表極其刻骨銘心（如告白、大學錄取），請為這段記憶打分。*」
3. **相關度 (Relevance)**：
   - 將當前情境（Query）與每條記憶的文字描述轉換為密集向量（Text Embedding）。
   - 計算餘弦相似度（Cosine Similarity），找出語意與當前任務高度關聯的歷史經歷。

---

## 3. 與傳統 RAG 向量資料庫的差異
- 傳統 RAG 僅依賴語義相似度（即單純的 Relevance）。
- **記憶串流引入了認知心理學的遺忘曲線（Recency）與情感刺激權重（Importance）**，避免代理人反覆被遠古但相似的無關瑣事干擾，展現出更逼真的人性化注意力配置。

---

## 4. 關聯頁面 (Related Links)
- 代表論文：[[2023_Park_Generative-Agents]]
- 搭配機制：[[Reflection-Mechanism]], [[Generative-Agents]]
