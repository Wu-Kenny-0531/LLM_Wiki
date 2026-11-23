# 三層迴圈工作流審查日誌 (Check Log)

本文件依據作業規定，完整記錄【Loop 1：逐篇 Ingest 與邊界檢查迴圈】、【Loop 2：簡報大綱審查與提前把關迴圈】與【Loop 3：HTML 簡報生成與渲染自檢迴圈】的每次檢查結果、錯誤發現與修改紀錄。

---

## 初始環境準備 (Environment Setup)
- 建立 `sources/` 資料夾，放置 5 篇核心 ABM 來源文件：
  - `sources/source_1.md`：ABM 基礎與核心三要素 (Agent, Environment, Interaction)
  - `sources/source_2.md`：謝林隔離模型 (Schelling's Segregation Model) 詳解
  - `sources/source_3.md`：複雜系統核心機制：非線性、回饋與湧現 (Emergence)
  - `sources/source_4.md`：個體行為特徵：異質性與有限理性 (Bounded Rationality)
  - `sources/source_5.md`：ABM vs. 方程式模型，以及傳統 ABM 與現代 LLM Agent 的本質邊界
- 建立 `template.html` 基礎簡報模板（內建可互動的謝林隔離模型 Canvas 模擬器）。


## [Loop 1 - Round 1] Ingest Source 1 (`sources/source_1.md`)
- **整合範圍**：`wiki/01_Overview.md` ~ `wiki/06_ABM_vs_LLMAgent.md`
- **知識重點**：ABM 定義、自底向上思想、馮紐曼細胞自動機起源、三要素（Agent、Environment、Interaction）
- **[檢查點 1 - 邊界審查結果]**：
  1. `[Source 1]` 引用標記：✅ 全部段落均正確標註來源標籤 `[Source 1]`。
  2. 現代 LLM Agent 混淆排查：✅ `01` 至 `05` 均維持傳統 ABM 純淨定義，無任何 AutoGPT 或 LLM Agent 概念混入；`06` 確立了傳統極簡規則個體 vs. 現代語言代理人的明確邊界。
- **結論**：審查通過，執行 Git Commit。


## [Loop 1 - Round 2] Ingest Source 2 (`sources/source_2.md`)
- **整合範圍**：`wiki/01_Overview.md` ~ `wiki/06_ABM_vs_LLMAgent.md`
- **知識重點**：謝林隔離模型詳細機制（2D 網格、Moore 鄰域、門檻值 $T$、滿意度檢查、骨牌搬家連鎖效應）、微觀溫和偏好 vs 宏觀極端隔離。
- **[檢查點 1 - 邊界審查結果]**：
  1. `[Source 2]` 引用標記：✅ 全部新增段落均精準標註 `[Source 2]`。
  2. 現代 LLM Agent 混淆排查：✅ `01` 到 `05` 嚴守傳統謝林模型的純規則演算設定（二元標籤與數值比例），未混入任何 LLM 或 Agent 工具鏈名詞；`06` 進一步明確對比了謝林純數值邏輯 vs LLM 語言代理人的層次差異。
- **結論**：審查通過，執行 Git Commit。


## [Loop 1 - Round 3] Ingest Source 3 (`sources/source_3.md`)
- **整合範圍**：`wiki/01_Overview.md` ~ `wiki/06_ABM_vs_LLMAgent.md`
- **知識重點**：湧現（Emergence）生活比喻（水分子成漩渦、神經元生意識、Boids 鳥群避障）、非線性、正負回饋循環、臨界點（Tipping Points）與相變。
- **[檢查點 1 - 邊界審查結果]**：
  1. `[Source 3]` 引用標記：✅ 全部新增段落均已打上 `[Source 3]` 標籤。
  2. 現代 LLM Agent 混淆排查：✅ `01` 到 `05` 維持純粹複雜適應系統（CAS）與傳統鳥群/網格物理模擬，無任何 LLM 混入；`06` 清晰劃分了「空間規則湧現」與「語用語意湧現」的層級差異。
- **結論**：審查通過，執行 Git Commit。


## [Loop 1 - Round 4] Ingest Source 4 (`sources/source_4.md`)
- **整合範圍**：`wiki/01_Overview.md` ~ `wiki/06_ABM_vs_LLMAgent.md`
- **知識重點**：個體異質性（Heterogeneity）生活比喻（股市多空分歧才能撮合）、有限理性（Bounded Rationality）、滿意化原則（Satisficing vs Maximizing）、糖原模型（Sugarscape）湧現財富不平等。
- **[檢查點 1 - 邊界審查結果]**：
  1. `[Source 4]` 引用標記：✅ 全部新增段落均已打上 `[Source 4]` 標籤。
  2. 現代 LLM Agent 混淆排查：✅ `01` 到 `05` 專注於有限理性理論（Herbert Simon）與傳統 Sugarscape 代謝參數，未混入現代 LLM Agent 機制；`06` 清楚區隔了「靜態數值參數異質性」vs「自然語言人設/記憶異質性」。
- **結論**：審查通過，執行 Git Commit。


## [Loop 1 - Round 5] Ingest Source 5 (`sources/source_5.md`)
- **整合範圍**：`wiki/01_Overview.md` ~ `wiki/06_ABM_vs_LLMAgent.md`
- **知識重點**：ABM vs 方程式模型（EBM）全維度矩陣（自頂向下 vs 自底向上、生成式解釋、空間拓撲、路徑依賴）、傳統極簡規則 Agent vs 現代 LLM Agent（如 AutoGPT）之嚴格邊界界定與現代融合。
- **[檢查點 1 - 邊界審查結果]**：
  1. `[Source 5]` 引用標記：✅ 全部新增段落均已打上 `[Source 5]` 標籤。
  2. 現代 LLM Agent 混淆排查：✅ `01` 到 `05` 嚴格恪守傳統科學計算與方程式模型之對比，無任何現代 Agent 溢出；`06` 建立了全維度對比矩陣與邊界紅線警示，徹底杜絕了將 AutoGPT 誤認為傳統 ABM 的學術混淆。
- **結論**：審查通過，Loop 1 全部 5 輪 Ingest 與邊界檢查圓滿達成！執行 Git Commit。


## [Loop 2 - Round 1 審查] 簡報大綱提前把關 (Check 2 - Beginner & Fact-Check)
- **審查標的**：`outline.md` (初版 8 頁大綱)
- **審查角色**：【事實查核員】+【零基礎初學者】
- **審查結果**：❌ **未通過（退回修改）**
- **發現缺陷與原因**：
  1. **超出 Wiki 邊界檢查**：✅ 通過。所有 8 頁投影片之主題均可對應至 `wiki/01_Overview.md` ~ `06_ABM_vs_LLMAgent.md`。
  2. **初學者友善度與生活比喻檢查**：❌ **不合格**。
     - **Slide 5 (湧現)**：僅列出「整體大於部分之和」，缺乏生活化比喻，初學者無法理解為何微觀個體沒有的屬性會在宏觀產生。需補充「水分子與漩渦」或「鳥群避障」比喻。
     - **Slide 6 (非線性與異質性)**：術語過於學術硬核。需為「非線性」補上「火苗跨過臨界點釀成森林大火」或「加倍投入不等於加倍收穫」比喻；為「異質性」補上「菜市場買賣雙方需求互補才形成市場生態」比喻。
     - **Slide 4 (謝林模型)**：需補充「鄰居搬家引發鄰里比例改變的骨牌效應」生動描述。
- **後續行動**：退回重新修訂 `outline.md`，將生活比喻深度融入各頁大綱，進行 Round 2 複審。


## [Loop 2 - Round 2 複審] 簡報大綱二次審查 (Check 2 - Verified)
- **審查標的**：`outline.md` (修訂版 8 頁大綱)
- **審查角色**：【事實查核員】+【零基礎初學者】
- **修改前後差異 (Diff & Improvements)**：
  1. **Slide 2**：補入「買早餐滿意化原則」生活比喻，生動解釋 Herbert Simon 的有限理性。
  2. **Slide 3**：補入「大富翁與模擬市民」積木比喻，闡明 Agent 與 Grid 環境。
  3. **Slide 5**：針對「湧現」，全面補齊三大生活化生動案例（水分子成漩渦、神經元生意識、Boids 鳥群避天敵）。
  4. **Slide 6**：針對「非線性」補上「火苗跨過臨界點引爆森林大火」；針對「異質性」補入「股市多空分歧才能維持流動性」比喻。
  5. **Slide 7**：強化「極簡數值規則 vs 語言智慧大腦」的邊界警示，符合防混淆紅線要求。
- **審查結論**：✅ **完全通過！** 零基礎讀者可毫無障礙理解，且完全錨定於 `wiki/` 知識庫。
- **後續行動**：執行 Git Commit，進入 Loop 3 生成最終 HTML 簡報。


## [Loop 3 - 終審自檢] HTML 簡報生成與渲染自檢 (Check 3 - Rendering & Integrity)
- **審查標的**：`index.html` (依據通過審查的 `outline.md` 與 `template.html` 產生)
- **審查項目與結果**：
  1. **投影片頁數檢查**：✅ 嚴格符合 8 頁規格（Slide 1 至 Slide 8），無多餘或遺漏頁面。
  2. **底部 Wiki 來源標註**：✅ 頁面底部整合動態連動模組，隨投影片切換自動顯示精確來源（如 Slide 1 顯示 `wiki/01_Overview.md`、Slide 4 顯示 `wiki/04_Classic_Models.md`、Slide 7 顯示 `wiki/06_ABM_vs_LLMAgent.md`）。
  3. **謝林隔離模型 Canvas 模擬器實裝**：✅ 於 Slide 4 成功實裝原生 HTML5 Canvas 模擬引擎，支援 35x35 網格、即時調整同類門檻滑桿（預設 30%）、即時統計滿意度與隔離指數，並具備開始/暫停與重置按鈕。
  4. **JavaScript 與排版溢位排查**：✅ 語法檢查通過無報錯；CSS 具備響應式網格與 `overflow: hidden` 保護機制，杜絕文字溢位與排版崩塌。
- **結論**：✅ **完全通過！** 執行 Git Commit，完成三層迴圈全部歷程。
