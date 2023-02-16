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

对于样本空间$\Omega={\alpha,\beta,\gamma,\delta}$有2种划分：$T_1={\alpha\beta, \gamma\delta}$，$T_2={\alpha\beta\gamma,\delta}$，$A=(\alpha\delta)$，$\omega=\alpha$。

所以有：$P_1(\omega)=(\alpha\beta)$，有$A \cap P_1 = (\alpha)$

那么对于参与者1来说，在信息集$T_1$下的$q_1$为：
$$
\begin{equation}\label{eqn:2}
\begin{aligned}
q_1
& = {P(A \cap P_1(\omega))\over P_1(\omega)}\\
& = {(\alpha) \over (\alpha\beta)} \\
& = {1 \over 2}
\end{aligned}
\end{equation}
$$
同理，有：$P_2(\omega)=(\alpha\beta\gamma)$，有$A \cap P_2 = (\alpha)$

那么对于参与者2来说，在信息集$T_2$下的$q_2$为：
$$
\begin{equation}\label{eqn:2}
\begin{aligned}
q_2
& = {P(A \cap P_2(\omega))\over P_2(\omega)}\\
& = {(\alpha) \over (\alpha\beta\gamma)} \\
& = {1 \over 3}
\end{aligned}
\end{equation}
$$
**这里参与者1、2对于相同事件A的后验概率不同，是因为他们的信息集划分不同。**这里体现的也是不完美信息博弈的一个特点。
