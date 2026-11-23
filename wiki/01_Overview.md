# 01. 代理人基模型概述 (Overview of Agent-Based Modeling)

## 什麼是代理人基模型 (ABM)？
代理人基模型（Agent-Based Modeling, ABM，或稱個體基模型 Individual-Based Modeling, IBM）是一種「自底向上（Bottom-up）」的計算模擬方法 [Source 1]。其核心精神在於：不直接對系統的宏觀整體設定假設，而是模擬大量具有自主決策能力的「微觀代理人（Agents）」，透過微觀個體的在地互動，自然觀察整個系統宏觀秩序的形成與演化 [Source 1]。

## 歷史與學術淵源
- **理論萌芽**：1940 年代由數學家馮紐曼（John von Neumann）提出「細胞自動機（Cellular Automata）」，證明簡單局部規則能自我複製並產生複雜圖樣 [Source 1]。
- **社會科學奠基**：1970 年代諾貝爾經濟學獎得主湯瑪斯·謝林（Thomas Schelling）利用棋盤硬幣模擬種族居住隔離，開創了微觀偏好引發宏觀隔離的研究範式 [Source 1]。
- **計算普及**：1990 年代起，隨著個人電腦算力躍升與軟體（如 NetLogo、Swarm）發展，ABM 廣泛應用於生態學、流行病傳播、交通流與金融市場模擬 [Source 1]。

## 為什麼需要 ABM？
傳統社會科學往往假設「代表性個體（Representative Agent）」且人人皆具全知理性；然而真實世界充滿了異質性與資訊不對稱。ABM 提供了可控的「計算實驗室」，讓研究者能無害化測試政策衝擊並觀察黑天鵝事件的形成過程 [Source 1]。


## 謝林模型與社會學里程碑
湯瑪斯·謝林在 1971 年發表的《動態隔離模型》（Dynamic Models of Segregation）證明了微觀層面極其溫和的同類偏好（如僅要求 30% 鄰居與自己同族），經過動態搬家連鎖反應後，宏觀層面竟會自發湧現出高達 80% 以上的嚴重隔離社區 [Source 2]。這一里程碑研究奠定了 ABM 揭示「微觀動機與宏觀行為脫節（Micromotives and Macrobehavior）」的核心地位 [Source 2]。


## 複雜適應系統的靈魂：湧現性
ABM 之所以超越傳統還原論（Reductionism），在於它深刻掌握了「湧現（Emergence）」：宏觀系統所展現出的組織形態與相變規律，根本不存在於任何單一代理人內部，而是微觀個體遵循簡單非線性互動後的必然產物 [Source 3]。


## 告別「同質理性人」假說
傳統社會科學假設「所有人皆同質且完全理性」，而 ABM 的根本革命在於承認人性的「異質性（Heterogeneity）」與「有限理性（Bounded Rationality）」——每個人擁有的資訊是不完整的、計算力是有限的，決策是依據滿意化（Satisficing）而非全域最佳化 [Source 4]。
