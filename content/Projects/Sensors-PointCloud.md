---
title: 感測器與點雲評估
publish: true
tags: [sensor, pointcloud, depth-camera]
---

> 最後更新:2026-05-18　·　結論：選定 Intel RealSense D405

## 結論（一句話）
測過 OAK 三款與 RealSense 兩款深度相機後，**Intel D405 雜訊最少、結構最穩定、近距離效果最好**，選為主力感測器。後續重心轉向 ROS2 控制與真實資料收集。

## 比較總表
| 相機 | 點雲結構 | 雜訊 | 備註 |
|---|---|---|---|
| OAK TOF | 穩定、可用 | 多（尤其近距離） | 測 40 / 60 / 120 / 120+ cm；參數可再調降雜訊 |
| OAK-D Pro | 看不出物體結構 | — | FPS 低且不穩，不適用 |
| OAK-D LR | 受 FOV／角度影響 | 視角度而定 | 測 5 / 10 / 15 cm baseline；論壇指不同 FOV 誤差不同 |
| RealSense D435if | 較穩 | 比 OAK 少 | — |
| **RealSense D405** | **穩定** | **最少** | **近距離佳，選定** |

## 影像紀錄
OAK TOF：
![[TOF1.png]]
![[TOF2.png]]

RealSense D405（選定）：
![[d405_1.png]]
![[d405_2.png]]

RealSense D435if：
![[d435i_1.png]]

## 待辦
- [ ] D405 串進 ROS2 camera stream
- [ ] 收集小黃瓜實物點雲資料集
- [ ] （可選）OAK TOF 近距離雜訊參數優化

## 參考
- OAK-D LR 規格與 FOV 誤差：Luxonis 官方文件與論壇討論。
