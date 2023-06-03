## Learning for Reasoning

### Abstracting unstructured data into symbols

#### Neuro-Symbolic Concept Learner (NS-CL)

使用neural symbolic reasoning去学习视觉概念、单词、句子语义解析，而且不需要监督学习。

包含3个模块

- visual perception：将图像中的场景变成基于对象的符号表示
- semantic parsing : 将问题转换成可执行程序
- symbolic reasoning：根据上面两个模型的表示进行推理得到答案

![Fig. 11. An illustration of NS-CL. The perception module begins by parsing visual scenes into object-based deep representations, while the semantic parser parse sentences into executable programs. A symbolic reasoning process bridges two modules.](https://pdf.cdn.readpaper.com/parsed/fetch_target/e69045c7e81cb793fef37ffad1fdd494_8_Figure_11_-510955174.png)



## Reasoning for Learning

### Regularization Models:

#### HDNN

采取知识蒸馏的方法，用teacher network学习规则和标记好的数据，引导student network进行学习。这样student network就可以被规则约束。

 图中表示 student的输入是labeled data，但是他不是直接受到规则的影响，而是通过平衡teacher student的输出去更新student的参数$\theta$



![Fig. 12. Overview of the HDNN framework. At each iteration, the teacher network is obtained by projecting the student network to a rule-regularized subspace (red dashed arrow), while the student network is updated to balance between emulating the teacher’s output and predicting the true labels (black/blue solid arrows). The figure is adapted from reference [65].](https://pdf.cdn.readpaper.com/parsed/fetch_target/e69045c7e81cb793fef37ffad1fdd494_9_Figure_12_1275814309.png)