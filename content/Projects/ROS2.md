---
title: ROS2 控制整合
publish: true
tags: [ros2, jetson, isaac-ros, urdf]
---

> 最後更新:2026-05-28　·　階段：起步

## 目標
以 ROS2 整合感測器、模擬與控制；先用小型自走車跑通節點架構，再接手臂。

## 進度
- [x] 安裝 ROS2 Jazzy（Ubuntu 24.04 / Jetson Thor）
- [ ] 用 URDF 製作小型自走車模型
- [ ] 跑通 topic / pub-sub / 節點訂閱與公告機制
- [ ] ROS2（Thor）↔ Isaac（Windows）橋接
- [ ] 串接 D405 相機

## 目前卡關 / blocker
- **ROS2 原生 + Gazebo 在 Jetson Thor 失敗**（EGL/GPU 問題）。
- 對策：改用 **Isaac ROS docker**，在容器內學 URDF 與節點運作。

## 候選硬體
- UGV：playrobot AMR（CAN bus 通訊，提供 SDK 與 ROS package）。

## 下一步
完成 URDF 自走車 + 基本 pub/sub，再做 Isaac bridge，最後串 D405。
