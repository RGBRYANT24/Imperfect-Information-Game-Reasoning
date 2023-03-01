# SDRL: Interpretable and Data-Efficient Deep Reinforcement Learning Leveraging Symbolic Planning

## Problem

深度强化学习在一些任务上取得了巨大的成功，神经网络需要的输入通常具有较高的维度，但是也因为如此其在可解释性和数据利用效率方面存在一定的问题。特别是缺乏对子任务的解释，在分层决策中，子任务的可解释性对增加深度强化学习（DRL）的透明度至关重要，也可以帮助人类理解DRL的规划。



## Goal

作者在深度强化学习系统中加入了符号规划（Symbolic Planning），同时提出了一个符号深度强化学习框架，使其可以同时处理高维度的输入和进行符号规划。将动作符号与选项相关联，在任务层级上实现了可解释性。此外，这个框架采用了planner-controller-meta-controller，通过三者交互，将学习到的子任务和符号规划能力与符号知识还有从高维感官输入进行的端到端强化学习结合在一起。

## Proposed Approach

作者将顺序决策过程建模为马尔科夫决策过程五元组MDP（S,A,P,R,$\gamma$）。目标是学习一系列的子任务和相应的子策略，逐个执行每个子任务对应的子策略时可以获得最大的累积奖励。

**建立符号框架**：通过专家知识建立起符号表示框架，用于表述环境规则：捕捉对象、状态转移以及他们的值是如何变化的。SDRL的主要框架如下图：

![Figure 1: Architecture illustration](https://pdf.cdn.readpaper.com/parsed/fetch_target/3543084130dfef8b4227ca9c869b8884_3_Figure_1_785371879.png)

- controller和环境进行交互，产生的是高级规划。然后生成外部奖励给meta-controller用于学习子任务

### SDRL的执行过程如下：

- 符号求解器（Symbolic Planner）产生高维规划（High-level Plan）。比如包含潜在奖励的一系列子任务
- 这里引入了内在奖励（intrinsic reward）和外在奖励（extrinsic reward）来评估两个层级（子任务、总任务）任务的学习
- 基于内在奖励（因为他对应的是子任务）通过DRL进行子任务对应子策略的学习
- 在子任务学习到一定程度的时候，去评估学习到的子策略。当达到一定的阈值，使用外部奖励，元控制器（Meta-controller）反映长期学习到的奖励，并反馈给符号求解器。

### 符号表示

通过元组$(I, G, D)$来表示符号规划问题

- $I$表示初始状态
- $G$表示内在目标，并且包含以下线性约束：其中$\rho$表示的是价值

$$
quality > quality(\Pi) \\
quality(\Pi) = \Sigma \rho(s_i, a_i), <s_i, a_i, s_{i+1}> \in \Pi
$$

- $D$是动作表述

### 从符号表示到选项

构造从符号表示到动作选项的映射

- 通过预训练模型能够判断当前智能体的状态（在雅达利游戏中是否完成子任务等）
- 由此可以构建一个半马尔科夫选项(semi-Markov option)？用三元组$(I, \pi, \beta)$表示
  - $I$表示初始状态
  - $\pi$策略 
  - $\beta(s)$表示当前状态是不是终止状态

### 奖励

奖励分为动作层级（action level）和任务层级（task level）

**action level**对应的就是内在奖励**intrinsic reward**

**task level**对应外在奖励**extrinsic reward**

当且仅当奖励之和最大时，规划$\Pi$达到了最优

### 规划和学习

<img src="C:\Users\Adrin\AppData\Roaming\Typora\typora-user-images\image-20230301203009917.png" alt="image-20230301203009917" style="zoom:50%;" />

- 对于每一个episode$t$，符号规划器（symbolic planner）产生一个规划$\Pi_t$
- 每一个规划$\Pi_t$对应一个子任务，让controller通过DQN去学习子策略。
- 根据子任务的完成情况，再通过R-learning更新Meta-controller。
- 对当前规划$\Pi_t$进行评估，并更新内在奖励
