---
title: Isaac Sim 虛擬場景
publish: true
tags: [isaac, simulation, usd, blender]
---

> 最後更新:2026-05-26

## 目標
在 Isaac Sim 建立溫室／農地模擬場景，供自走車與手臂在虛擬環境中測試。

## 進度
- [x] Isaac Sim 5.1 安裝（注意：必須解壓到 `C:\isaacsim`，否則解壓縮失敗）
- [x] Quickstart 教學完成
- [x] infinigen（wsl + docker）生成地表 → 轉 usdc → 匯入 Isaac
- [x] Blender + MCP 用 geometry node 建小黃瓜農田模型
- [ ] 場景貼圖在 Isaac 正常顯示
- [ ] 自走車在場景中移動 + 控制迴路

## 目前卡關 / blocker
- **Isaac 開 infinigen 戶外模型貼圖失敗**：官方似乎只支援室內模型貼圖，戶外不支援。
- OpenUSD 自建模型 + 材質難度高；查無現成的「溫室 + 農地」USD asset，確定需自建。

## 影像紀錄
Blender infinigen 渲染：
![[blender_infinigen_render.png]]

Isaac 匯入 infinigen（貼圖問題）：
![[isaac_sim_infinigen.png]]

Blender 小黃瓜農田：
![[blender_cucumber.png]]

## 決策
場景建置先求堪用，優先把學習重心移到 ROS2 控制與真實資料收集，見 [[Projects/ROS2]]。
