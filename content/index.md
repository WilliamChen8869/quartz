---
title: 305 實驗室 — 研究與開發進度
publish: true
---

> 最後更新:2026-05-28

這是農地（小黃瓜）採收機器人專案的進度總覽。每個專案頁面都有當前狀態、完成度、目前卡關點與下一步。點任一專案名稱即可進入。

## 專案總覽

| 專案 | 階段 | 進度 | 目前卡關 |
|---|---|---|---|
| [[Projects/CucumberRobot\|小黃瓜採收機器人（主線）]] | Phase 1 環境與感測器評估 | 🟡 進行中 | ROS2 + Isaac 橋接尚未完成 |
| [[Projects/Sensors-PointCloud\|感測器與點雲評估]] | 收斂中 | 🟢 已選定 D405 | 近距離雜訊參數仍可優化 |
| [[Projects/IsaacSim\|Isaac Sim 虛擬場景]] | 建置中 | 🟡 進行中 | 戶外貼圖 Isaac 不支援 |
| [[Projects/ROS2\|ROS2 控制整合]] | 起步 | 🔴 早期 | Gazebo 在 Thor 失敗，改走 Isaac ROS |
| [[Projects/Paper\|頂刊論文]] | 文獻調查 | 🟡 規劃中 | 演算法切入點待定 |
| [[Projects/TaiwanGermany\|台德計畫（行政）]] | 執行中 | 🟢 持續 | — |

圖例：🟢 順利　🟡 進行中　🔴 早期或卡關

## 本週重點（0525–0528）
- OpenUSD：自建溫室＋農地模型難度高，確認沒有現成 asset，改用 Blender + MCP geometry node 自建小黃瓜農田。
- 已下訂模擬用小黃瓜植栽。
- 安裝 Ultralytics 8.4.56 / torch 2.11 / CUDA 12.8，開始蔬果分選模型方向調查。
- ROS2 原生 Gazebo 在 Jetson Thor 有 EGL/GPU 問題 → 改用 Isaac ROS docker，開始學 URDF 做小型自走車、熟悉節點與 pub/sub。

## 整體下一步
1. 完成 ROS2 topic / pub-sub 基礎與 Isaac bridge。
2. 把 D405 串進 ROS2，做 camera stream 整合。
3. 模擬小黃瓜植栽到貨後，開始實機資料收集。
