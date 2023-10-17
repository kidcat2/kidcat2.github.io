---
title: "[DeepLearning] DETR - 논문 Review"
date: 2023-10-17 +0000
categories: [Develop, DeepLearning]
tags: [DeepLearning, DETR, 딥러닝, Obejct Detection, 객체 검출]
math: true
published : false
---

## Index 
0. Summary
1. Problem
2. DETR
3. Result 
4. Limit

---

## Summary

- 이전의 Object Detection : 전처리, 사전작업, 필요한 라이브러리 등이 많음

- Detection Transformer 의 2가지 핵심
    - set prediction 의 직접적 해결
    - 많은 사전작업들의 제거 및 간소화

- set prediction : bipartite matching ( 이분 매칭 )

- 성능 : Faster R-CNN 정도의 성능

- detail
    - LR : $10^{-4}$ (backbone : $10^{-5}$)
    - weight decay : $10^{-4}$
    - init : Xavier init
    - backbone : ResNet50 / ResNet101
    - backbone normalize : frozen batchnorm(torch vision)
    - data : scale augmentation , resizing, random crop augmentation
    - data set : COCO

- Result Model
    - R101 : ResNet 101 
    - FPN : Feature Pyramid Network 
    - DC5 : DC5 (Detectron Cascade R-CNN with 5 Stages)
    - FPN 과 DC5 에 대한 내용은 "Detectron-Cascade R-CNN with ResNet-50-FPN-DC" 에서 볼 수 있다.


---

## Problem




