---
layout: post
title:  "about those pesky Levi-Civita identities"
date:   2016-02-25 13:14:00 +0100
categories: post
tags: [math, physics, rug, msc]
---
<style>body {text-align: justify}</style>
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

The first case describes  exchange of rows (permutation of indices), and the second case describes repeated rows (repeated indices). This is exactly the definition of the antisymmetric *Levi-Civita tensor* on $$\mathbb{E}^3$$;

$$
\epsilon_{ijk}\equiv\det(E_{ijk})
$$

With this in mind we can derive some useful identities.

---

$$
\begin{align*}
	\epsilon_{ijk}\epsilon^{lmn} &=\det(E_{ijk})\det(E^{lmn})\\
	&=\det(E_{ijk}E^{lmn})\\
%
%	&=\left|\begin{pmatrix}
%		\mathbf{e}_{i}\\\mathbf{e}_{j}\\\mathbf{e}_{k}
%	\end{pmatrix}\left(\mathbf{e}^{l}\,\mathbf{e}^{m}\,\mathbf{e}^{n}\right)
%	\right|\\
%
	&=\left|\begin{matrix}
		\delta_{i}^{l} & \delta_{i}^{m} & \delta_{i}^{n} \\
		\delta_{j}^{l} & \delta_{j}^{m} & \delta_{j}^{n} \\
		\delta_{k}^{l} & \delta_{k}^{m} & \delta_{k}^{n}
	\end{matrix}\right|
\end{align*}
$$

Where we used $$\delta_i^j=\mathbf{e}_i\mathbf{e}^j$$. All Levi-Civita identities follow from this determinant, so we will expand it;

$$
\begin{split}
	\epsilon_{ijk}\epsilon^{lmn} &= \delta_{i}^{l}\delta_{j}^{m}\delta_{k}^{n} +
	\delta_{i}^{m}\delta_{j}^{n}\delta_{k}^{l}+\delta_{i}^{n}\delta_{j}^{l}\delta_{k}^{m}\\
	&\quad\quad-\delta_{i}^{n}\delta_{j}^{m}\delta_{k}^{l}-\delta_{i}^{m}\delta_{j}^{l}\delta_{k}^{n}-
	\delta_{i}^{l}\delta_{j}^{n}\delta_{k}^{m}
\end{split}\label{1}\tag{1}
$$

---
To prove

$$
\epsilon_{ijk}\epsilon^{lmk}=\delta_{i}^{l}\delta_{j}^{m}-\delta_{i}^{m}\delta_{j}^{l}\label{2}\tag{2}
$$

we set $$n=k$$ in equation $$\eqref{1}$$;

$$
\begin{split}
\epsilon_{ijk}\epsilon^{lmk} &=3\delta_{i}^{l}\delta_{j}^{m}+\delta_{i}^{m}\delta_{j}^{l}+\delta_{i}^{m}\delta_{j}^{l}\\
&\quad\quad-\delta_{i}^{l}\delta_{j}^{m}-3\delta_{i}^{m}\delta_{j}^{l}-\delta_{i}^{l}\delta_{j}^{m}\\
&=\delta_{i}^{l}\delta_{j}^{m}-\delta_{i}^{m}\delta_{j}^{l}
\end{split}
$$

---
To prove

$$
\epsilon_{ijk}\epsilon^{ljk}=2\delta_{i}^{l}\tag{3}\label{3}
$$

we use $$m=j$$ in equation $$\eqref{2}$$;

$$
\begin{split}\epsilon_{ijk}\epsilon^{ljk} &=3\delta_{i}^{l}-\delta_{i}^{l}\\
&=2\delta_{i}^{l}
\end{split}
$$

---
Lastly, to prove

$$
\epsilon_{ijk}\epsilon^{ijk}=6\label{4}\tag{4}
$$

we let the final set of indices be the same in equation $$\eqref{3}$$.
