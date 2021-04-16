---
layout: post
title:  "about those pesky Levi-Civita identities"
date:   2016-02-25 13:14:00 +0100
modified_date: 2021-04-14 18:04:29 +0600
categories: post
tags: [math, msc, physics, rug]
---
Let $$E_{ijk}$$ be the matrix formed by using the $$\mathbb{E}^3$$ base vectors $$\mathbf{e}_1,\mathbf{e}_2,\mathbf{e}_3$$ as its rows;

$$
\begin{align*}
  E_{ijk} &=
  \begin{pmatrix}
    \mathbf{e}_i\\
    \mathbf{e}_j\\
    \mathbf{e}_k
  \end{pmatrix}\\
  \Rightarrow(E_{ijk})^T &= \left(\mathbf{e}^i\,\mathbf{e}^j\,\mathbf{e}^k\right)\equiv E^{ijk}
\end{align*}
$$

Now consider the determinant of $$E_{ijk}$$;

$$
  \det(E_{ijk})=
  \begin{cases}
    (-1)^{\sigma(ijk)}\\
    0
  \end{cases}
$$

The first case describes exchange of rows (permutation of indices), and the second case describes repeated rows (repeated indices). This is exactly the definition of the antisymmetric *Levi-Civita tensor* on $$\mathbb{E}^3$$,

$$
\epsilon_{ijk}\equiv\det(E_{ijk})
$$

I found this *extremely* helpful for proving and remembering the Levi-Civita identities, which we can now easily derive---they're just a product of determinants. Consider the product,

$$
\begin{align*}
  \epsilon_{ijk}\epsilon^{lmn} &=\det(E_{ijk})\det(E^{lmn})\\
  &=\det(E_{ijk}E^{lmn})\\
  &=\left|\begin{matrix}
    \delta_{i}^{l} & \delta_{i}^{m} & \delta_{i}^{n} \\
    \delta_{j}^{l} & \delta_{j}^{m} & \delta_{j}^{n} \\
    \delta_{k}^{l} & \delta_{k}^{m} & \delta_{k}^{n}
  \end{matrix}\right|
\end{align*}
$$

Where we used $$\mathbf{e}_i\mathbf{e}^j=\delta_i^j$$. Expanding this determinant we have,

$$
\begin{aligned}
  \epsilon_{ijk}\epsilon^{lmn}=\delta_{i}^{l}\delta_{j}^{m}\delta_{k}^{n}
  &+\delta_{i}^{m}\delta_{j}^{n}\delta_{k}^{l}
  +\delta_{i}^{n}\delta_{j}^{l}\delta_{k}^{m}\\
  &-\delta_{i}^{n}\delta_{j}^{m}\delta_{k}^{l}
  -\delta_{i}^{m}\delta_{j}^{l}\delta_{k}^{n}
  -\delta_{i}^{l}\delta_{j}^{n}\delta_{k}^{m}
\end{aligned}\tag{1}\label{1}
$$

Now, if we set $$n=k$$ in equation $$\eqref{1}$$ we get

$$
\begin{aligned}
  \epsilon_{ijk}\epsilon^{lmk}=3\delta_{i}^{l}\delta_{j}^{m}
  &+\delta_{i}^{m}\delta_{j}^{l}
  +\delta_{i}^{m}\delta_{j}^{l}\\
  &-\delta_{i}^{l}\delta_{j}^{m}
  -3\delta_{i}^{m}\delta_{j}^{l}
  -\delta_{i}^{l}\delta_{j}^{m}\\
\end{aligned}
$$

Which proves the identity

$$
\epsilon_{ijk}\epsilon^{lmk}=\delta_{i}^{l}\delta_{j}^{m}
-\delta_{i}^{m}\delta_{j}^{l}
\tag{2}\label{2}
$$

Setting $$m=j$$ in equation $$\eqref{2}$$ yields

$$
\epsilon_{ijk}\epsilon^{ljk}=3\delta_{i}^{l}-\delta_{i}^{l}\\
$$

Proving the identity

$$
\epsilon_{ijk}\epsilon^{ljk}=2\delta_{i}^{l}\tag{3}\label{3}
$$

Letting the last set of indices be the same in equation $$\eqref{3}$$, the final Levi-Civita identity is obtained

$$
\epsilon_{ijk}\epsilon^{ijk}=6\tag{4}\label{4}
$$


