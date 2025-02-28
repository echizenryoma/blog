# 洛必达

## 递归正弦

### 发现

$$
\frac{2}{\pi}=\sqrt{\frac{1}{2}}\cdot\sqrt{\frac{1}{2}+\frac{1}{2}\sqrt{\frac{1}{2}}}\cdot\sqrt{\frac{1}{2}+\frac{1}{2}\sqrt{\frac{1}{2}+\frac{1}{2}\sqrt{\frac{1}{2}}}}\cdot\cdots
$$

### 意义

首次发现$\pi$不仅仅和几何有关，而且和无穷乘积有关系

### 思考

1. 迭代使用倍角正弦公式
2. 构造重要极限
3. 迭代使用半角余弦公式

### 证明

$$\begin{align}
\sin{2\theta} &= 2\cos{\theta}\sin{\theta} \\
\sin{2^2\theta} &= 2\cos{2\theta}\sin{2\theta} \\
                &= 2^2\cos{2\theta}\cos{\theta}\sin{\theta} \\
\sin{2^3\theta} &= 2\cos{2^2\theta}\sin{2^2\theta} \\
                &= 2^2\cos{2^2\theta}\cos{2\theta}\sin{2\theta} \\
                &= 2^3\cos{2^2\theta}\cos{2\theta}\cos{\theta}\sin{\theta} \\
\cdots  \\
\therefore \sin{2^n\theta} &= 2^n\cos{2^{n-1}\theta}\cdots\cos{2\theta}\cos{\theta}\sin{\theta} \\
\text{令} x &= 2^n\theta \\
\sin{x} &= 2^n\cos{\frac{x}{2}}cos{\frac{x}{2^2}}\cdots\cos{\frac{x}{2^n}}\sin{\frac{x}{2^n}} \\
\frac{\sin{x}}{\frac{x}{2^n}} &= \frac{2^n\cos{\frac{x}{2}}cos{\frac{x}{2^2}}\cdots\cos{\frac{x}{2^n}}\sin{\frac{x}{2^n}}}{\frac{x}{2^n}} \\
2^n\frac{\sin{x}}{x} &= \frac{2^n\cos{\frac{x}{2}}cos{\frac{x}{2^2}}\cdots\cos{\frac{x}{2^n}}\sin{\frac{x}{2^n}}}{\frac{x}{2^n}} \\
\frac{\sin{x}}{x} &= \cos{\frac{x}{2}}cos{\frac{x}{2^2}}\cdots\cos{\frac{x}{2^{n-1}}}\frac{\sin{\frac{x}{2^n}}}{\frac{x}{2^n}} \\
\lim_{n\to\infty} \frac{\sin{x}}{x} &= \lim_{n\to\infty} \cos{\frac{x}{2}}cos{\frac{x}{2^2}}\cdots\cos{\frac{x}{2^{n-1}}}\frac{\sin{\frac{x}{2^n}}}{\frac{x}{2^n}} \\
\frac{\sin{x}}{x} &= \lim_{n\to\infty} \cos{\frac{x}{2}}cos{\frac{x}{2^2}}\cdots\cos{\frac{x}{2^{n-1}}}\frac{\sin{\frac{x}{2^n}}}{\frac{x}{2^n}} \\
\frac{\sin{x}}{x} &= \lim_{n\to\infty} \cos{\frac{x}{2}}cos{\frac{x}{2^2}}\cdots\cos{\frac{x}{2^{n-1}}}\lim_{n\to\infty} \frac{\sin{\frac{x}{2^n}}}{\frac{x}{2^n}} \\
\because \lim_{n\to\infty}\frac{x}{2^n} &= 0 \\
\therefore \lim_{n\to\infty}\sin{\frac{x}{2^n}} &= 0 \\
\because \lim_{x\to0}\frac{\sin{x}}{x} &= 1 \\
\therefore \lim_{n\to\infty} \frac{\sin{\frac{x}{2^n}}}{\frac{x}{2^{n-1}}} &= 1 \\
\therefore \frac{\sin{x}}{x} &= \lim_{n\to\infty} \cos{\frac{x}{2}}cos{\frac{x}{2^2}}\cdots\cos{\frac{x}{2^n}} \\
\frac{\sin{x}}{x} &= \cos{\frac{x}{2}}cos{\frac{x}{2^2}}\cdots \\
\text{令} x &= \frac{\pi}{2} \\
\frac{\sin{\frac{\pi}{2}}}{\frac{\pi}{2}} &= \cos{\frac{\pi}{2}}\cos{\frac{\frac{\pi}{2}}{2}}cos{\frac{\frac{\pi}{2}}{2^2}}\cdots \\
\frac{2}{\pi} &= \cos{\frac{\pi}{2}}\cos{\frac{\pi}{2^2}}cos{\frac{\pi}{2^3}}\cdots \\
\because \cos{2\theta} &= 2\cos^2{\theta} - 1, \theta \in \left[0,\frac{\pi}{2}\right) \\
\therefore \cos{\theta} &= \sqrt{\frac{1}{2}+\cos{2\theta}}  \\
\therefore \cos{\frac{\pi}{2^3}} &= \sqrt{\frac{1}{2}+\cos{\frac{\pi}{2^2}}} = \sqrt{\frac{1}{2}+\sqrt{\frac{1}{2}}} \\
\therefore \cos{\frac{\pi}{2^4}} &= \sqrt{\frac{1}{2}+\cos{\frac{\pi}{2^3}}} = \sqrt{\frac{1}{2}+\sqrt{\frac{1}{2}+\sqrt{\frac{1}{2}}}} \\
\cdots  \\
\therefore \frac{2}{\pi} &= \sqrt{\frac{1}{2}}\cdot\sqrt{\frac{1}{2}+\frac{1}{2}\sqrt{\frac{1}{2}}}\cdot\sqrt{\frac{1}{2}+\frac{1}{2}\sqrt{\frac{1}{2}+\frac{1}{2}\sqrt{\frac{1}{2}}}}\cdot\cdots
\end{align}$$