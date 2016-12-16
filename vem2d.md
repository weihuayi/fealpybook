# 二维虚单元法

## 1. 符号


| Notation | Meaning |
| -------|---------|
|$$\mathbb{R}^2$$ | 二维欧氏空间 |
|$$\mathcal{D}$$ | 二维区域 |
|$$\bf{x}_{\mathcal{D}}$$ | 区域 $$D$$ 的 重心 |
|$$\mathcal{P}_k(\mathcal{D})$$ | 区域 $$D$$ 上 $$k$$次多项式空间| 
|$$E$$ | 多边形区域  |
|$$N^V$$ | $$E$$ 的顶点个数 |
|$$\bf{x}_i$$ |  第 $$i$$ 个顶点坐标|
|$$|E|$$ | $$E$$ 的面积 |
| $$W=\begin{pmatrix}0&-1\\1 & 0 \end{pmatrix}$$ | 旋转矩阵, 作用在二维列向量上表示逆时针旋转该向量$$90^\circ$$ |
|$$\alpha=(\alpha_1, \alpha_2)$$ | 二重指标 |
|$$\mathcal{M}_k(\mathcal{D})$$ | 单项式空间 |
|$$V_k(E)$$ | $$k$$ 次的虚单元空间 |  
|$$\Pi^\nabla_{*,E}: V_k(E) \rightarrow \mathcal{P}_k(E)$$ | $$k$$ 次虚单元空间到 $$k$$ 次多项式空间的的投影算子| 
|$$\Pi^\nabla_E: V_k(E) \rightarrow V_k(E) $$ | 投影算子  | 
|$$ n_k = (k+1)(k+2)/2$$ | $$k$$ 次多项式空间维数 |
|$$ N_k = \text{dim} V_k(E) = N^Vk+(k-1)k/2$$ | $$k$$ 次虚单元空间的维数 |

## 2. 模型

$$
\begin{cases}
-\Delta u = f, & \text{ in } \Omega \\
u = g, & \text{ on } \partial\Omega 
\end{cases}
$$

找到 $$ u \in H^1_g(\Omega)$$:
$$
(\nabla u, \nabla v) = (f, v),\quad\forall v in H^1_0(\Omega)
$$

## 单项式空间

|$$\alpha$$ | $$n_k$$ | 单项式  $$m_\alpha$$ | $$\nabla m_{\alpha}$$ |
|--------|---------|
|(0, 0)  | 1|  1 |  (0, 0) |
|(1, 0)  | 2| $$\frac{x - x_E}{h_E}$$ | $$(\frac{1}{h_E}, 0)$$|
|(0, 1)  | 3| $$\frac{y - y_E}{h_E}$$ | $$(0, \frac{1}{h_E})$$|
|(2, 0)  | 4| $$(\frac{x - x_E}{h_E})^2$$ | $$(\frac{2(x - x_E)}{h_E^2}, 0)$$|
|(1, 1)  | 5| $$\frac{(x - x_E)(y - y_E)}{h_E^2}$$ | $$(\frac{y - x_E}{h_E^2}, \frac{x - x_E}{h_E^2})$$
|(0, 2)  | 6| $$(\frac{y - y_E}{h_E})^2$$ |$$(0, \frac{2(y - y_E)}{h_E^2})$$ |
|(3, 0)  | 7| $$(\frac{x - x_E}{h_E})^3$$ | $$(\frac{3(x - x_E)^2}{h_E^3}, 0)$$|
|(2, 1)  | 8| $$\frac{(x - x_E)^2(y - y_E)}{h_E^3}$$ |$$(\frac{2(x - x_E)(y - y_E)}{h_E^3}, \frac{(x - x_E)^2}{h_E^3})$$  |
|(1, 2)  | 9| $$\frac{(x - x_E)(y - y_E)^2}{h_E^3}$$ |$$(\frac{(y - y_E)^2}{h_E^3}, \frac{2(x - x_E)(y - y_E)}{h_E^3})$$  |
|(0, 3)  | 10|$$(\frac{y - y_E}{h_E})^3$$ | $$(0, \frac{3(y - y_E)^2}{h_E^3})$$|


## 3. 投影算子

定义 $$\Pi^\nabla: V_k(E)\rightarrow \mathcal{P}_k(E)$$ 如下: 给定  $$ v_h \in
V_k(E)$$, 找到 $$\Pi^\nabla v_h \in \mathcal{P}_{E}$$ 满足:

$$
\begin{equation}
(\nabla \Pi^\nabla v_h, \nabla p_k) = (\nabla v_h, \nabla p_k), \forall p_k\in\mathcal{P}_{E}
\end{equation}
$$

投影 $$\Pi^\nabla v_h$$ 关于常数唯一.  可以定义投影 $$ P_0: V_k(E) \rightarrow
\mathcal{P}_0(E)$$:

$$
\begin{equation}
P_0(\Pi^\nabla v_h - v_h) = 0
\end{equation}
$$

具体定义如下: 
$$
\begin{align}
P_0 v_h :=& \frac{1}{N^V}\sum_{i=1}^{N^V} v_h(x_i)\text{ for } k=1\\
P_0 v_h :=& \frac{1}{|E|} \int_{E}v_h = \frac{1}{E} (1, v_h)_E\text{ for } k\geq 2
\end{align}
$$

下面考虑上述投影的矩阵表示形式:

$$
\begin{equation}
G = 
\begin{pmatrix}
P_0 m_1 & P_0m_2 & \ldots & P_0 m_{n_k} \\
0 & (\nabla m_2, \nabla m_2)_{0,E} & \cdots & (\nabla m_2, \nabla m_{n_k})_{0,E}\\
\cdots & \cdots & \cdots & \cdots \\
0 & (\nabla m_{n_k}, \nabla m_2)_{0,E} & \cdots & (\nabla m_{n_k}, \nabla m_{n_k})_{0,E}
\end{pmatrix}
\end{equation}
$$

$$
\begin{aligned}
B =& 
\begin{pmatrix}
P_0\varphi_1 & \cdots & P_0\varphi_{N_k}\\
(\nabla m_2, \nabla\varphi_1)_{0, E} & \cdots & (\nabla m_2, \nabla\varphi_{N_k})_{0, E}\\
\cdots & \cdots & \cdots \\
(\nabla m_{n_k}, \nabla\varphi_1)_{0, E} & \cdots & (\nabla m_{n_k}, \nabla\varphi_{N_k})_{0, E}\\
\end{pmatrix}\\
=& \begin{pmatrix}
P_0\varphi_1 & \cdots & P_0\varphi_{N_k}\\
-(\Delta m_2,\varphi_1)_{0, E} & \cdots & -(\Delta m_2,\varphi_{N_k})_{0, E}\\
\cdots & \cdots & \cdots \\
-(\Delta m_{n_k}, \varphi_1)_{0, E} & \cdots & -(\Delta m_{n_k},\varphi_{N_k})_{0, E}\\
\end{pmatrix}\\
& +\begin{pmatrix}
0 & \cdots & 0\\
(\frac{ \partial m_2}{\partial n},\varphi_1)_{\partial E} & \cdots & (\frac{\partial m_2}{\partial n},\varphi_{N_k})_{\partial E}\\
\cdots & \cdots & \cdots \\
(\frac{\partial m_{n_k}}{\partial n}, \varphi_1)_{\partial E} & \cdots & (\frac{\partial m_{n_k}}{\partial n}, \varphi_{N_k})_{\partial E}\\
\end{pmatrix}\\
\end{aligned}
$$

$$
\begin{equation}
D = \begin{pmatrix}
dof_1(m_1) & dof_1(m_2) & \cdots & dof_1(m_{n_k}) \\
dof_2(m_1) & dof_2(m_2) & \cdots & dof_2(m_{n_k}) \\
\cdots & \cdots & \cdots & \cdots \\
dof_{N_K}(m_1) & dof_{N_K}(m_2) & \cdots & dof_{N_K}(m_{n_k}) 
\end{pmatrix}
\end{equation}
$$

$$\Pi^\nabla_*: V_k(E)\rightarrow \mathcal{P}_k(E)\subset V_k(E)$$ 的矩阵表示如下: 

$$\Pi^\nabla_* = G^{-1}B$$

由于

$$
\begin{equation}
\begin{aligned}
\Pi^{\nabla} (\varphi_1, \varphi_2, \cdots, \varphi_{N_K}) =& (m_1, m_2, \cdots, m_{n_k}) G^{-1}B\\
= &(\varphi_1, \varphi_2, \cdots, \varphi_{N_K})DG^{-1}B
\end{aligned}
\end{equation}
$$

所以 $$\Pi^{\nabla}: V_k(E)\rightarrow V_k(E) $$ 的矩阵表示如下:

$$
\begin{equation}
\mathbf{\Pi}^{\nabla}=DG^{-1}B
\end{equation}
$$

另外, 易证 $$G = BD$$ 
$$
\begin{aligned}
&\begin{pmatrix}
(\nabla\Pi^\nabla\varphi_1, \nabla\Pi^\nabla\varphi_1) & (\nabla\Pi^\nabla\varphi_1, \nabla\Pi^\nabla\varphi_2) & \cdots & (\nabla\Pi^\nabla\varphi_1, \nabla\Pi^\nabla\varphi_{N_K})\\
(\nabla\Pi^\nabla\varphi_2, \nabla\Pi^\nabla\varphi_1) & (\nabla\Pi^\nabla\varphi_2, \nabla\Pi^\nabla\varphi_2) & \cdots & (\nabla\Pi^\nabla\varphi_2, \nabla\Pi^\nabla\varphi_{N_K})\\
\cdots & \cdots & \cdots & \cdots \\
(\nabla\Pi^\nabla\varphi_{N_K}, \nabla\Pi^\nabla\varphi_1) & (\nabla\Pi^\nabla\varphi_{N_K}, \nabla\Pi^\nabla\varphi_2) & \cdots & (\nabla\Pi^\nabla\varphi_{N_K}, \nabla\Pi^\nabla\varphi_{N_K})\\
\end{pmatrix}\\

=&\nabla\Pi^\nabla \begin{pmatrix} \varphi_1\\ \varphi_2 \\ \vdots\\\varphi_{n_k} \end{pmatrix} \left(\nabla\Pi^\nabla \begin{pmatrix} \varphi_1\\ \varphi_2 \\ \vdots\\\varphi_{n_k} \end{pmatrix} \right)^T \\
=& [\Pi_*^\nabla]^T \begin{pmatrix}
\nabla m_1^T \\ \nabla m_2^T \\\vdots\\ \nabla m_{n_k}^T
\end{pmatrix}
\begin{pmatrix}
\nabla m_1 & \nabla m_2 & \cdots & \nabla m_{n_k}
\end{pmatrix} \Pi_*^\nabla \\
= & [\Pi_*^\nabla]^T \tilde{G} \Pi_*^\nabla
\end{aligned}
$$


$$
\begin{equation}
K_E^h = [\Pi_*^\nabla]^T \tilde{G} \Pi_*^\nabla + (I - \Pi^\nabla)^T(I - \Pi^\nabla)
\end{equation}
$$

 ## 4.$$L^2$$投影
$$
\begin{equation}
H = \begin{pmatrix}
(m_1, m_1) & (m_1, m_2) & \cdots & (m_1, m_{n_k}) \\
(m_2, m_1) & (m_2, m_2) & \cdots & (m_2, m_{n_k}) \\
\vdots & \vdots & \vdots & \vdots \\ 
(m_{n_k}, m_1) & (m_{n_k}, m_2) & \cdots & (m_{n_k}, m_{n_k}) 
\end{pmatrix}
\end{equation}
$$

$$
\begin{equation}
\begin{aligned}
C = & \begin{pmatrix}
(m_1, \varphi_1) & (m_1, \varphi_2) & \cdots & (m_1, \varphi_{N_K}) \\
(m_2, \varphi_1) & (m_2, \varphi_2) & \cdots & (m_2, \varphi_{N_K})\\
\vdots & \vdots & \vdots & \vdots \\
(m_{n_k}, \varphi_1) & (m_{n_k}, \varphi_2) & \cdots & (m_{n_k}, \varphi_{N_K})
\end{pmatrix}\\
=& \begin{pmatrix}
C_{n_{k-2}\times kN^V} & C_{n_{k-2}\times n_{k-2}}\\
C_{(n_{k} - n_{k-2})\times kN^V} & C_{(n_{k} - n_{k-2})\times n_{k-2}}
\end{pmatrix}
\end{aligned}
\end{equation}
$$

其中:
$$
\begin{equation}
\begin{aligned}
C_{n_{k-2}\times kN^V} = & 0 \\
C_{n_{k-2}\times n_{k-2}} = &|E| I\\
(C_{(n_{k} - n_{k-2})\times kN^V}, C_{(n_{k} - n_{k-2})\times n_{k-2}}) = & HG^{-1}B[n_{k-2}+1:n_k,1:N_K]
\end{aligned}
\end{equation}
$$

$$
\begin{equation}
C_{\alpha i} = 
\begin{cases}
|E|, &i = kN^V+\alpha\\
(HG^{-1}B)_{\alpha i}, &n_{k-2} < \alpha \leq n_k\\
0, & \text{others}
\end{cases}
\end{equation}
$$


记 
$$\Pi^0: V_k(E) \rightarrow V_k(E)$$ 和 $$\Pi^0_*: V_k(E) \rightarrow \mathcal{P}_k(E)$$

$$
\begin{equation}
\Pi^0 = DH^{-1}C = D\Pi^0_*
\end{equation}
$$

## 4. 质量矩阵

$$
\begin{equation}
M_E^h = C^TH^{-1}C + |E|(I - \Pi^0)^T(I - \Pi^0)
\end{equation}
$$

## 5. 左端项

$$
\begin{equation}
F = \begin{pmatrix}
(f, \Pi^0_k\varphi_1) \\
(f, \Pi^0_k\varphi_2) \\
\vdots\\
(f, \Pi^0_k\varphi_{N^{dof}})
\end{pmatrix}
=(\Pi^0_*)^T\begin{pmatrix}
(f, m_1)\\ (f, m_2) \\ \vdots \\ (f, m_{n_k})
\end{pmatrix}
\end{equation}
$$

## 6. 2维空间中的例子
### 6.1 单项式积分

|$$\alpha$$ |$$n_k$$ | Momonial $$m_\alpha$$ | $$\nabla m_{\alpha}$$ |
|--------|---------|
|(0, 0)  | 1|  1 |  (0, 0) |
|(1, 0)  | 2| $$\frac{x - x_E}{h_E}$$ | $$(\frac{1}{h_E}, 0)$$|
|(0, 1)  | 3| $$\frac{y - y_E}{h_E}$$| $$(0, \frac{1}{h_E})$$|
|(2, 0)  | 4| $$(\frac{x - x_E}{h_E})^2$$ | $$(\frac{2(x - x_E)}{h_E^2}, 0)$$|
|(1, 1)  | 5| $$\frac{(x - x_E)(y - y_E)}{h_E^2}$$ | $$(\frac{y - x_E}{h_E^2}, \frac{x - x_E}{h_E^2})$$
|(0, 2)  | 6| $$(\frac{y - y_E}{h_E})^2$$ |$$(0, \frac{2(y - y_E)}{h_E^2})$$ |
|(3, 0)  | 7| $$(\frac{x - x_E}{h_E})^3$$ | $$(\frac{3(x - x_E)^2}{h_E^3}, 0)$$|
|(2, 1)  | 8| $$\frac{(x - x_E)^2(y - y_E)}{h_E^3}$$ |$$(\frac{2(x - x_E)(y - y_E)}{h_E^3}, \frac{(x - x_E)^2}{h_E^3})$$  |
|(1, 2)  | 9| $$\frac{(x - x_E)(y - y_E)^2}{h_E^3}$$ |$$(\frac{(y - y_E)^2}{h_E^3}, \frac{2(x - x_E)(y - y_E)}{h_E^3})$$  |
|(0, 3)  | 10|$$(\frac{y - y_E}{h_E})^3$$ | $$(0, \frac{3(y - y_E)^2}{h_E^3})$$|



### 6.2  k= 1

$$
\begin{equation}
\begin{aligned}
G = &
\begin{pmatrix}
P_0 m_1 & P_0m_2 &  P_0 m_{3} \\
0 & (\nabla m_2, \nabla m_2)_{0,E} &  (\nabla m_2, \nabla m_{3})_{0,E}\\
0 & (\nabla m_{3}, \nabla m_2)_{0,E} &  (\nabla m_{3}, \nabla m_{3})_{0,E}
\end{pmatrix}\\
= & \begin{pmatrix}
1 & \sum_{i=1}^{N^V} \frac{x_i - x_{c,E}}{h_EN^V} & \sum_{i=1}^{N^V} \frac{y_i - y_{c,E}}{h_EN^V}\\
0 & 1 & 0\\
0 & 0 & 1
\end{pmatrix}\\
=& \begin{pmatrix}
1 & 0 & 0\\
0 & 1 & 0\\
0 & 0 & 1
\end{pmatrix}
\end{aligned}
\end{equation}
$$

$$
\begin{equation}
\begin{aligned}
B =& 
\begin{pmatrix}
P_0\varphi_1 & \cdots & P_0\varphi_{N^{V}}\\
(\nabla m_2, \nabla\varphi_1)_{0, E} & \cdots & (\nabla m_2, \nabla\varphi_{N^{V}})_{0, E}\\
(\nabla m_{3}, \nabla\varphi_1)_{0, E} & \cdots & (\nabla m_{3}, \nabla\varphi_{N^{V}})_{0, E}\\
\end{pmatrix}\\
=& \begin{pmatrix}
P_0\varphi_1 & \cdots & P_0\varphi_{N^{V}}\\
-(\Delta m_2,\varphi_1)_{0, E} & \cdots & -(\Delta m_2,\varphi_{N^{V}})_{0, E}\\
-(\Delta m_{3}, \varphi_1)_{0, E} & \cdots & -(\Delta m_{3},\varphi_{N^{V}})_{0, E}\\
\end{pmatrix}\\
& +\begin{pmatrix}
0 & \cdots & 0\\
(\frac{ \partial m_2}{\partial n},\varphi_1)_{\partial E} & \cdots & (\frac{\partial m_2}{\partial n},\varphi_{N^{V}})_{\partial E}\\
(\frac{\partial m_{3}}{\partial n}, \varphi_1)_{\partial E} & \cdots & (\frac{\partial m_{3}}{\partial n}, \varphi_{N^{V}})_{\partial E}\\
\end{pmatrix}\\
=&\begin{pmatrix}
\frac{1}{N^V} & \cdots & \frac{1}{N^V}\\
(\frac{ \partial m_2}{\partial n},\varphi_1)_{\partial E} & \cdots & (\frac{\partial m_2}{\partial n},\varphi_{N^{V}})_{\partial E}\\
(\frac{\partial m_{3}}{\partial n}, \varphi_1)_{\partial E} & \cdots & (\frac{\partial m_{3}}{\partial n}, \varphi_{N^{V}})_{\partial E}\\
\end{pmatrix}\\
=&\begin{pmatrix}
\frac{1}{N^V} \cdots \frac{1}{N^V}\\
\frac{1}{h_E}\sum_e n_e(\int_e\varphi_1, \cdots, \int_e\varphi_{N^V_P})
\end{pmatrix}\\
=& \begin{pmatrix}
\frac{1}{N^V} & \cdots & \frac{1}{N^V}\\
\frac{1}{h_E}\vec{d}_1 & \cdots & \frac{1}{h_E} \vec{d}_{N_E^V}\\
\end{pmatrix}\\
\end{aligned}
\end{equation}
$$

其中 $$\vec{d}_{i} = \frac{1}{2}W^T(X_{i+1} - X_{i-1})$$ . 

$$
\begin{equation}
\begin{aligned}
D = &\begin{pmatrix}
dof_1(m_1) & dof_1(m_2) &  dof_1(m_{3}) \\
dof_2(m_1) & dof_2(m_2) &  dof_2(m_{3}) \\
\vdots & \vdots & \vdots \\
dof_{N^{v}}(m_1) & dof_{N^{v}}(m_2) & dof_{N^{v}}(m_{3}) 
\end{pmatrix}\\
=& \begin{pmatrix}
1 & \frac{x_1 - x_{c,E}}{h_E} &  \frac{y_1 - y_{c,E}}{h_E} \\
1 & \frac{x_2 - x_{c,E}}{h_E} &  \frac{y_2 - y_{c,E}}{h_E} \\
\vdots & \vdots & \vdots \\
1 & \frac{x_{N^V} - x_{c,E}}{h_E} & \frac{y_{N^V} - y_{c,E}}{h_E}
\end{pmatrix}
\end{aligned}
\end{equation}
$$

$$
\begin{equation}
H = \begin{pmatrix}
(m_1, m_1) & (m_1, m_2) &  (m_1, m_{3}) \\
(m_2, m_1) & (m_2, m_2) &  (m_2, m_{3}) \\
(m_{3}, m_1) & (m_{3}, m_2) & (m_{3}, m_{3}) 
\end{pmatrix}
\end{equation}
$$

$$
\begin{equation}
\begin{aligned}
C =& \begin{pmatrix}
(m_1, \varphi_1) & (m_1, \varphi_2) & \cdots & (m_1, \varphi_{N^{V}}) \\
(m_2, \varphi_1) & (m_2, \varphi_2) & \cdots & (m_2, \varphi_{N^{V}})\\
(m_{3}, \varphi_1) & (m_{3}, \varphi_2) & \cdots & (m_{3},\varphi_{N^{V}})
\end{pmatrix}\\
=& HG^{-1}B
\end{aligned}
\end{equation}
$$
