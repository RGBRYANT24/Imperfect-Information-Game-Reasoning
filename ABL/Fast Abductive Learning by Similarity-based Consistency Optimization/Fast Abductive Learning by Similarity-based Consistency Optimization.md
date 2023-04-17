# Fast Abductive Learning by Similarity-based Consistency Optimization

## Problem

在ABL中同时处理输入和符号表示问题需要预训练模型，如果预训练模型很难进行分类处理就会影响ABL的性能

## Goal

提出一种ABLSim的方式，使其能够在一些复杂的neuro-symbolic learning tasks上进行学习。

## Proposed Approach

由于相似的label有相似的特征空间，在反绎（abducting）的过程中加入相似度衡量的方式。

- 将标签聚类，不同类别的标签之间有不同的距离。
- 将逻辑反绎的过程抽象为组合优化问题，引入beam search解决这个问题。
- 将相似度和置信度结合起来，应用于abduct过程中

## Results

在mnist和两个比较困难的符号识别任务上都表现出了sota性能