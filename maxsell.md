# Maxwell 方程有限元方法  

$$
\begin{aligned}
H(\text{curl};\Omega) = \{\mathbf v \in \mathbf L^2(\Omega), \text{curl }\mathbf v\in\mathbf L^2(\Omega)\}\\
H(\text{div};\Omega) = \{\mathbf v \in \mathbf L^2(\Omega), \text{div }\mathbf v\in\mathbf L^2(\Omega)\}
\end{aligned}\\
H(\text{grad};\Omega) = \{\mathbf v \in \mathbf L^2(\Omega), \text{grad }\mathbf v \in \mathbf L^2(\Omega)\}
$$

用算子 $$d$$ 代表上述三个算子,  则上面三个空间中的范数都可写成如下形式:

$$
\|u\|_{d,\Omega} := (\|u\|^2 + \|du\|^2)^{1\over2}
$$

## $$H(\text{div};\Omega)$$ 空间 

### 三角形单元

边 $$e_{i,j}$$ 上的基函数:

$$
\Phi_{i,j} = \lambda_i \nabla^\perp\lambda_j - \lambda_j \nabla^\perp \lambda_i
$$

其中 $$\nabla^\perp$$ 是一个二维的旋转梯度算子:

$$
\nabla^\perp f = (-\partial_y f, \partial_x f)
$$

对偶基为:

$$
X_{i,j}(\mathbf u) = \int_{e_{i,j}}\mathbf u\cdot \mathbf n_{i,j}\mathrm d s
$$

### 四面体单元

面 $$f_{i,j,k}$$ 上的基函数为:
$$
\Phi_{i,j,k} = 2(\lambda_i\nabla\lambda_j\times\nabla\lambda_k + \lambda_j\nabla\lambda_k\times\nabla\lambda_i+\lambda_k\nabla\lambda_i\times\nabla\lambda_j)
$$

## $$H(\text{curl};\Omega)$$ 空间

### 三角形单元
### 四面体单元
