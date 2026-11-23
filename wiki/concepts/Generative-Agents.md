---
type: concept
name: "Generative Agents"
first_introduced_by: "[[2023_Park_Generative-Agents]]"
tags:
  - concept
  - domain/abm
  - architecture
---

# 生成式代理人 (Generative Agents)

> [!NOTE] 定義與直覺
> 生成式代理人（Generative Agents）是指以大型語言模型（LLM）為核心認知引擎，結合長期記憶儲存、高階反思與動態規劃機制的計算軟體個體。不同於傳統腳本化或固定狀態機的虛擬角色，生成式代理人能以自然語言感知開放環境、記錄生活經歷、提煉自身信念，並展現出符合角色人設與長期生活軌跡的真實行為。

---

## 1. 核心認知三元組架構 (Cognitive Triad)

根據 [[2023_Park_Generative-Agents]]，生成式代理人具備三大不可或缺的認知支柱：

```mermaid
flowchart LR
    A["[[Memory-Stream|記憶串流]]<br>記錄一切感知的資料庫"] --> B["[[Reflection-Mechanism|反思機制]]<br>提煉高階信念與自我認同"]
    B --> C["動態規劃與反應<br>自頂向下分解日程並即時應變"]
    C --> A
```

1. **長期記憶儲存與動態檢索 ([[Memory-Stream]])**：解決語言模型上下文視窗（Context Window）長度限制，透過新鮮度、重要度與相關度三維加權檢索歷史記憶。
2. **抽象反思與高階推論 ([[Reflection-Mechanism]])**：定期從低階原始生活瑣事中抽象出概括性洞見與價值觀，形成反思樹。
3. **遞迴規劃與環境交互 (Planning & Reacting)**：支援自頂向下的日程分解，並根據環境事件（如遇見朋友、物品起火）即時調整下一步行動。

---

## 2. 與傳統代理人（Traditional Agents）之對比

| 評估維度 | 傳統規則型代理人 (Rule-based / FSM) | 傳統強化學習代理人 (RL) | 生成式代理人 (Generative Agents) |
| :--- | :--- | :--- | :--- |
| **知識來源** | 依賴人工手寫腳本與狀態轉換 | 依賴預先設定的數值獎勵函數 | 預訓練模型常識 + 自然語言記憶串流 |
| **開放環境適應性** | 極低（遇到未定義狀態即當機或僵死） | 局限於封閉遊戲（圍棋、Dota 2） | 極高（能以常識應對開放社交情境） |
| **長期行為一致性** | 依賴嚴格規則維護 | 難以建模多天連續生活情境 | 透過記憶串流與反思機制保持連貫 |
| **語言交流能力** | 僅限預設字串或選單樹 | 無法生成自然多樣的語言 | 流暢的全自然語言互動與傳播 |

---

## 3. 典型應用場景
- **社會科學與經濟學模擬 ([[Social-Simulation-ABM]])**：模擬社群動態、資訊擴散、政策衝擊反應。
- **下一代遊戲 NPC**：創造擁有自我意識、記憶與動態人際關係的開放世界居民。
- **人機互動與使用者研究 (HCI Prototyping)**：模擬目標使用者群體的日常習慣，提前驗證產品互動設計。

---

## 4. 關聯頁面 (Related Links)
- 奠基文獻：[[2023_Park_Generative-Agents]]
- 組件技術：[[Memory-Stream]], [[Reflection-Mechanism]], [[Social-Simulation-ABM]]
- 領域綜述：[[LLM-Agent-Based-Modeling]]
