---
title: 小黃瓜採收機器人（主線）
publish: true
tags: [robot, cucumber, main]
---

> 最後更新:2026-05-28　·　階段：Phase 1 — 環境與感測器評估

## 目標
建立小黃瓜自動採收系統：在溫室／農地環境下，以視覺感測辨識小黃瓜，規劃採收順序，並以機械手臂 + end-effector 完成採收。

## 完成度
- [x] 工作站與感測器環境建置（Jetson Thor、5080 PC、NAS）
- [x] 多款深度相機點雲評估（OAK 系列 / RealSense）→ 選定 Intel D405
- [x] Isaac Sim 安裝與 quickstart
- [x] Blender 建立小黃瓜農田場景（geometry node）
- [ ] ROS2 基礎（topic / pub-sub / URDF 自走車）
- [ ] ROS2 ↔ Isaac bridge
- [ ] D405 camera stream 串進 ROS2
- [ ] 機械手臂控制
- [ ] 視覺伺服（visual servoing）
- [ ] End-effector 設計
- [ ] 實機資料收集（待模擬植栽到貨）

## 目前卡關 / blocker
- ROS2 與 Isaac 的橋接尚未打通，節點架構仍在熟悉中。
- Isaac 對戶外場景貼圖支援差，見 [[Projects/IsaacSim]]。

## 下一個里程碑
完成 ROS2 topic/pub-sub + Isaac bridge + D405 stream 整合，讓模擬車能在 Isaac 場景中跑起來並收到相機資料。

## 相關
- 感測器結論：[[Projects/Sensors-PointCloud]]
- 模擬場景：[[Projects/IsaacSim]]
- 控制整合：[[Projects/ROS2]]
- 參考文獻：Human-centered approach for an efficient cucumber harvesting robot system（harvest ordering / visual servoing / end-effector）
