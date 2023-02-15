# 论文 Agreeing to Disagree

## 公共知识

### 非形式化描述





### 形式化定义

对于样本空间$\Omega$，$T_1, T_2$是对样本空间的两个划分（partition），并且有$T_1 \cup T_2$不为空。如果世界的真实状态是$\omega$，那么对于参与者$i$来说，如果参与者$i$知道$w$的发生，那么说明在参与者$i$的信息集划分$T_i$中存在一个包含$w$的元素$P_i(\omega)$。对于样本空间$\Omega$中给定的$\omega$，如果事件$E$包含了$T_1\cap T_2$中包含$\omega$的元素，那么称$E$是在$\omega$处的公共知识。

对于事件$A$来说，$q_i$是参与者$i$在给定信息集划分$T_i$下的后验概率$p(A|T_i)$。如果$\omega \in \Omega$，则有：
$$
q_i(\omega)={p(A \cap\ P_i(\omega))\over p(P_i(\omega))}
$$
举例：

对于样本空间$\Omega={\alpha,\beta,\gamma,\delta}$有2种划分：$T_1={\alpha\beta, \gamma\delta}$，$T_2={\alpha\beta\gamma,\delta}$，
