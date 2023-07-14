# 第5课 课后作业

## 第1题

Q: $KZG$ 多项式承诺方案在 $Setup$ 阶段涉及到计算对秘密评估点 $\tau$ 的幂的承诺，这被称为“可信设置”，通常在被称为“Powers of Tau”的仪式中利用多方计算生成。 假如说有一天，你在一张纸条上找到了 $\tau$ 的值。 你怎么能用它来制作一个假的 $KZG$ 证明呢？

A: 在KZG方案开始时，验证者需要检查：

  - $e(π, [τ − x]_2) = e(C − [y]_1, G_2)$

  - ${f(τ )-y \over τ  -x}(τ − x)= f(τ) -y$
  
    所以我们可以通过构造任意 $y'=f(x')$ 来生成虚假证明 $τ'= {f(τ )-y' \over τ  -x}$
## 第2题

Q: 从 $KZG$ 多项式承诺方案构造一个**向量承诺方案**。 （提示：对于向量 $m=\left(m_{1}, \ldots, m_{q}\right)$，是否存在一个"插值多项式" $I(X)$ 使得 $I\left(x_{i}\right)=y_{i}$？）

A: 我们可以构建一个拉格朗日插值多项式 I(X)，满足以下条件：

  $$
  I(X) = \sum_i m_i L_i(X) = \left\{
  \begin{aligned}
  m_i \:\: if X=i \\
  0 \:\: else
  \end{aligned}
  \right.
  $$

  - KZG.Setup: 等同于提交阶段的设置
  - KZG.Commit $(ck; I(X)) ->C$: for $C=I(\alpha)_1$
  - KZG.Open $(srs, C, m_i, i) → {0, 1}$
  
## 第3题

Q: $KZG$ 多项式承诺方案对关系 $p(x)=$ $y$ 进行披露证明 $\pi$。 你能扩展这个方案来产生一个多重证明 $\pi$，让我们相信 $p\left(x_{i}\right)=y_{i}$ 对于点列表和评估 $\left(x_{i }, y_{i}\right)$ ？ （提示：假设您有一个插值多项式 $I(X)$ 使得 $I\left(x_{i}\right)=y_{i}$）。

A: 构造插值多项式：
  
  $$
  I(X) = \sum_i y_i L_i(X) = \left\{
  \begin{aligned}
  y_i \:\: if X=i \\
  0 \:\: else
  \end{aligned}
  \right.
  $$

  为了将KZG证明扩展到多个点和求值 ${(x_i, y_i)}$， 我们必须保证每个 $x_i$ 是 $π_{multiproof}$ 的分子的根，所以我们可以设置：
  
  $$
  π_{multiproof} := {f(X) - I(X) \over Π(X-x_i)}
  $$
  
  验证者应该检查：
  
  $$
  e(π_{multiproof}, [Π(X-x_i)]_2) = e(C − I(X), G_2) 
  $$
