# 微分方程

## 一阶线性微分方程

### 1. 一阶线性齐次微分方程

对于一阶线性齐次微分方程$y' + P(x)y = 0$，其解法如下：

1. **分离变量**：将方程改写为
   $$
   \frac{dy}{dx} = -P(x)y
   $$
   然后分离变量得到：
   $$
   \frac{dy}{y} = -P(x)dx
   $$

2. **积分求解**：对两边积分：
   $$
   \int \frac{1}{y} \, dy = -\int P(x) \, dx
   $$
   $$
   \ln|y| = -\int P(x)dx + C, C\text{为常数}
   $$

3. **解出y**：对两边取指数函数，得到通解：
   $$
   y = C e^{-\int P(x)dx}
   $$

### 2. 一阶线性非齐次微分方程

对于一阶线性齐次微分方程$y' + P(x)y = Q(x)$，其解法如下：

1. **分离变量**：将方程改写为
   $$\begin{align}
   \frac{dy}{dx} &= Q(x) - P(x)y \\
   \frac{dy}{dx} &= y(\frac{Q(x)}{y} - P(x))
   \end{align}$$
   然后分离变量得到：
   $$
   \frac{dy}{y} = (\frac{Q(x)}{y} - P(x))dx
   $$

2. **积分求解**：对两边积分：
   $$
   \int \frac{1}{y} \, dy = -\int (\frac{Q(x)}{y} - P(x)) \, dx
   $$
   $$
   \ln|y| = -\int (\frac{Q(x)}{y} - P(x))dx + C_1, C_1\text{为常数}
   $$

3. **解出y**：对两边取指数函数，得到通解：
   $$\begin{align}
   y &= C_1 e^{\int \frac{Q(x)}{y} - P(x)dx} \\
     &= C_1 e^{-P(x)dx} \cdot e^{\int \frac{Q(x)}{y}dx}
   \end{align}$$
   其中的$C_1 e^{-P(x)dx}$是一阶线性齐次微分方程$y' + P(x)y = 0$的通解，$e^{\int \frac{Q(x)}{y}dx}$是关于$x$的函数，也即

   $$
   y = C(x) e^{-P(x)dx},\text{其中}C(x)=C_1 \cdot e^{\int \frac{Q(x)}{y}dx}
   $$
