# [Source 1] 代理人基模型 (Agent-Based Modeling, ABM) 基礎與核心架構

## 1. 什麼是代理人基模型 (ABM)？
代理人基模型（Agent-Based Modeling, 簡稱 ABM，有時亦稱 Individual-Based Modeling, IBM）是一種自底向上（Bottom-up）的計算模擬方法。與傳統自頂向下（Top-down）假設整體處於均衡或遵循單一宏觀方程式的方法不同，ABM 聚焦於模擬一群具有自主決策能力的「微觀個體（Agents）」，並在給定的環境中相互互動，進而觀察整個系統自發產生的宏觀現象。

ABM 的思想根源可追溯至馮紐曼（John von Neumann）在 1940 年代提出的細胞自動機（Cellular Automata），以及 1970 年代諾貝爾經濟學獎得主湯瑪斯·謝林（Thomas Schelling）的空間動態研究。隨著 1990 年代個人電腦算力普及，ABM 迅速成為複雜系統科學、計算社會科學、生態學與流行病學的核心研究工具。

## 2. ABM 的核心三要素 (The Triad of ABM)
任何一個完整的 ABM 模型均由以下三大核心組件構成：
1. **代理人 (Agent)**：
   - 系統中的基本運作單元，代表真實世界中的人、企業、動物或車輛。
   - 代理人具有內部狀態（如位置、財富、健康狀況、偏好）、行為準則（Decision Rules）與感知範圍（Sensing Horizon）。
2. **環境 (Environment)**：
   - 代理人生存與活動的空間媒介。
   - 可以是離散的二維網格（Grid/Lattice，如棋盤世界）、連續的幾何空間，或者是抽象的拓撲社群網路（Social Network）。
   - 環境本身可以具有動態屬性，例如資源生長、障礙物阻隔或氣候變化。
3. **互動機制 (Interaction Rules)**：
   - 定義代理人之間、以及代理人與環境之間如何交換資訊或物資。
   - 互動通常是局部的（Local Interaction），代理人僅能與其視野內（Moore 或 von Neumann 鄰域）的鄰居或相連網路節點發生接觸。

## 3. ABM 的核心價值
傳統社會科學往往假設「代表性個體（Representative Agent）」且每個人完全理性；然而真實社會是由成千上萬具有不同背景、資訊不完全且相互影響的個體所組成。ABM 提供了一座「計算實驗室」，讓研究人員可以在不傷害真實社會的前提下，透過調控微觀規則來測試政策效果與預測系統性崩潰。
