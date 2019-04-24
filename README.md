# 史怀济《数学分析》学习笔记

《数学分析》，史怀济，中国科学大学，视频：共220讲，[B站视频链接](https://www.bilibili.com/video/av18844091)

> 因为此文件包含大量的公式，如果：
>
> * 你在GitHub online查看，建议使用Chrome配合Chrome插件[MathJax Plugin for Github](https://chrome.google.com/webstore/detail/mathjax-plugin-for-github/ioemnmodlmafdkllaclgeombjnmnbima?hl=en)以便查看排版后的LaTeX
> * 你下载此Repo源文件到本地，建议使用[Typora](https://support.typora.io)并开启([Inline Math](https://support.typora.io/Math/#inline-math))后查看。

## 第一章 实数和数列极限

### 1.1 实数

#### 问题1.1

**1. 非负整数 $a$, $b$ 使得 $\frac{a^2 + b^2}{ab + 1}$为整数，求证这个整数必是某一个整数的平方。**

方法一（反证法、[韦达跳跃](https://zh.wikipedia.org/wiki/%E9%9F%8B%E9%81%94%E8%B7%B3%E8%BA%8D)）：

令 
$$
k = \frac{a^2 + b^2}{ab + 1}
$$

- 假设存在一个或更多不是完全平方数的解 $k$ 。
- 对特定 $k$ ，$(x, y) = (A,B)$ 是方程 $x^2 + y^2 - mxy = 0$ 正整数解对。
- 由于 $x^2 + y^2 - mxy - m = 0$ 是关于 x,y 对称的方程，先设 $A \ge B$。
- 再设原整数方程关于 $A$ 的二次方程，即为：$x^2 + b_1^2 - kBx- m = 0$，$x = A$ 是其中一个正整数根。利用[韦达定理](https://zh.wikipedia.org/wiki/%E9%9F%8B%E9%81%94%E5%AE%9A%E7%90%86)，可将另一根表示成$x_2 = kB - A$或是$x_2 = \frac{B^2 – k}{A}$。
- 从 $x_2$的第一个表示式可得$x_2$为整数，第二个表示式可得$x_2 \neq 0$，因为$k$不是完全平方数。进一步，从$\frac{x_2^2 + b^2}{x_2B+1}=k>0$可得$x_2$为正整数。
- 最后，从$A>B$可推出$x_2=\frac{B^2-k}{A}<A$，所以$x_2 + B < A + B$，与$A + B$为最小矛盾。

方法二（[无穷递降法](https://www.zhihu.com/question/60664582)）：

令 $k = \frac{a^2 + b^2}{ab + 1}$
1. 当 $a = b$时，
  - $k = \frac{2a^2}{a^2 + 1} = (2 - k)a^2 > 0$，即： $2 - k > 0, k \in (0, 2)$，因为$k$是整数，那么 $k = 1$
2. 当 $a \neq b$，设 $a > b$，则
  - $k = \frac{a^2 + b^2}{ab + 1} > \frac{a^2 + b^2}{a^2 + 1} > 1$
  - 根据题目条件，得到$a^2 - bka + b^2 - k = 0$, 且该方程必有正整数根 $a$。设另一根为 $a_1$。得到
    - $a^2 - bka + b^2 - k = 0, \tag{1}$
    - $a_1^2 - bka_1 + b^2 - k = 0, \tag{2}$
  - $(1), (2)$两式相减及相加（其实这是[韦达定理](https://zh.wikipedia.org/wiki/%E9%9F%A6%E8%BE%BE%E5%AE%9A%E7%90%86)），可以得到
    - $a + a_1 = bk, \tag{3}$ 
    - $b^2 - k = a a_1, \tag{4}$
    - 根据题目定义，$b, k$ 是整数，所以 $a_1$是整数。
  - 接着证明 $a_1$ 的正负性：
    - 设 $a_1 \leq -1$, 则 $(a_1^2 + b^2) = k(a_1b + 1) \leq k(-b + 1) \leq 0$ 不成立，所以 $a_1 \ge 0$。
    - 所以 $0 \leq a_1 = \frac{b^2 - k}{a} < \frac{b^2}{a} < b < a$
    - 如果 $a_1 = 0$，那么$k$为平方数，所以只用讨论 $0 < a_1 < b < a$的情况
- 对 $k = \frac{a^2 + b^2}{ab + 1}$重复上面的推理，可知存在整数$b_1$满足 $b > a_1 > b_1 \ge 0$，使得 $k = \frac{a_1^2 + b_1^2}{a_1b_1 + 1}$
- 这样回到了原来的情况，不过这时有 $a > b > a_1 > b_1$
- 上述过程可以无限循环，最后必然有一个 $a_i = 0$ 或 $b_i = 0$。不论任何情况，$k$都是一个平方数。

#### 问题1.2

**2.若$a_1 \leq a_2 \leq \cdots \leq a_n$，$b_1 \leq b_2 \leq \cdots \leq b_n$，证明Tchebycheff不等式**：
$$
\sum_{i=1}^n a_i \sum_{i=1}^n b_i  \leq n\sum_{i=1}^n a_i b_i
$$

证明：

由[排序不等式](https://zh.wikipedia.org/wiki/%E6%8E%92%E5%BA%8F%E4%B8%8D%E7%AD%89%E5%BC%8F)可知，最大的和为顺序和：$a_1b_1+ \cdots + a_nb_n$

因此有：
- $a_1b_1 + a_2b_2+ \cdots + a_nb_n = a_1b_1+ a_2b_2+ \cdots + a_nb_n$
- $a_1b_1 + a_2b_2+ \cdots + a_nb_n \ge a_1b_2 + a_2b_3 + \cdots + a_nb_1$
- $a_1b_1 + a_2b_2+ \cdots + a_nb_n = a_1b_3 + a_2b_4 +  \cdots + a_nb_2$
- $\vdots$
- $a_1b_1+ a_2b_2 + \cdots + a_nb_n \ge a_1b_n + a_2b_1 + \cdots + a_nb_{n-1}$

将这$n$个不等式分边相加，同时对右边进行因式分解，便得到：

$n(a_1b_1 + a_2b_2+ \cdots + a_nb_n) \ge (a_1 + a_2 + a_3 + \cdots + a_n)(b_1 + b_2+ \cdots + b_n)$
两边同时处于$n$，即证明了命题。

### 1.2 数列和收敛数列

例四里用到 **几何平均-算术平均不等式**:

$$ \sqrt[n]{x_1 x_2 \cdots x_n} \leq \frac{x_1 + x_2 + \cdots + x_n}{n} $$

### 1.3 收敛数列的性质

练习题 1.3 第3、4、5题

### 1.4 数列极限的推广

练习题 1.4 第3题

### 1.5 单调数列

练习题 1.5 第1题

### 1.6 自然对数的底 e

对于 

$$
e_n = \left(1 + \frac{1}{n}\right)^n
$$

是单调递增数列，并且有上界。

证明用到二项式定理有：
$$
e_n = 1 + \sum_{k=1}^n \binom{n}{k} \frac{1}{n^k}
$$


自然对数 $e$ :
$$
e = \lim_{n\rightarrow \infty} \left(1+\frac{1}{1!}+\frac{1}{2!}+\cdots+\frac{1}{n!}\right)
$$
练习题 1.6 第2题

### 1.7 基本列和Cauchy收敛原理

**基本列的定义**：设$\{a_n\}$是一列实数列。对任意给定的$\epsilon>0$，若存在$N\in N^*$，使得当$m, n\in N^*$且$m,n>N$时，有 $|a_m-a_n|<\epsilon$ 

数列收敛的充分必要条件是，数列是基本列。

**引理**：从任一数列中必可取出一个单调子列。

**定理** Bolzano-Weierstrass定理：从任何有界的数列中必可选出一个收敛的子列。

**定理**：一个数列收敛的充分必要条件是它是基本列。

