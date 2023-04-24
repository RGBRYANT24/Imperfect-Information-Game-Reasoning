# Abductive Knowledge Induction From Raw Data

## Problem

推理模型需要一个完善的知识库，但是实际应用中不现实

## Goal

设计一种推理模型（abduction），将神经网络模型和逻辑归纳统一，能够直接从raw data中提取知识。

## Proposed Approach

将问题抽象为如下：

在给定知识库$B$，输入$x$，reasoning model$H$，预测模型$\theta$的情况下，求一组参数$(H^*, \theta^*)$使得在这些条件下得到ground truth $y$和中间隐藏的结果$z$（在文章中是手写数字识别）的概率最大。

就是在给定条件下求一组参数，使得得到正确结果的概率最大。

![img](https://static.cdn.readpaper.com/aiKnowledge/screenshot/2023-04-24/05bcc4fadfc845a191d7b6a45fc930f7/8e3b8227-55ff-42a4-b68e-30266e665b6f.png)

这种方法使用了最大似然估计，用迭代的方法（$EM$）来求解这组参数。