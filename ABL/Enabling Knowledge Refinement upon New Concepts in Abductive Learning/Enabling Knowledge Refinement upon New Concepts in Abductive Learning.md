# Enabling Knowledge Refinement upon New Concepts in Abductive Learning

## Problem 

ABL在实际应用中，其训练时给定的知识库往往是不全面的，或者是和实际有冲突的。这就限制了ABL的性能。

## Goal

在ABL中引入一种知识库冲突解决或者知识库增强的方法。

## Proposed Approach

引入知识图谱来学习新的concepts，并且将new concepts按照出现情况分为perception level和reasoning level。

#### Perception Level

- 在预测阶段出现new concepts，分类器$f$并不能识别这个玩意，所以要更新分类器$f$
- 学习新的规则并且更新KB
- 在知识图谱KG中加入新的实体

#### Reasoning Level

- 更新推理模型的标签$Y =  Y_{new} \cup Y$空间

- 同样，用$Y_{new}$作为$ ground \space truth$更新预测模型$f$

### $ABL_{nc}的组成$

整个$ABL_{nc}$分为3个组成部分

#### New Concepts Detection

冲突模型$g$首先roughly检测数据中有没有新的concepts

#### Knowledge Refinement

如果出现了新concepts：

- 首先尝试学习新规则R（关于新concepts的）
- Inductive Logic Programming（ILP）检测新规则R和知识库KB是否冲突
- 如果冲突，引入冲突检测模块进行修改

#### Abductive Learning

通过最小化KB和pseudo-labels的距离来进行推理。

## Result

#### Less-Than with New Digits

数字比较大小。

在所知数字不全的情况下比较大小

#### Chess with New Pieces

学习新棋子的可以移动的范围