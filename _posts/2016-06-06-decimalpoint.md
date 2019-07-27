---
title: The decimal point is ambiguous
date: 2016-06-06
excerpt: "let's not use it unless we have to ..."
header:
  overlay_image: /images/math.jpg
  overlay_filter: 0.5
use_math: true
classes: wide
---

Many numbers can be symbolically written in more than one way. For example :

$$1=\frac{1}{1}=\frac{2}{2}=\frac{3}{3}=\cdots$$

The decimal point notation also has its own problems. For example, consider the following perfectly valid identity :

$$1=0.99999999\cdots~,$$

with the series of $9$s repeating *ad infinitum*. There are many ways to prove the above. Here is one.

The right-hand side can be written in a form involving a *geometric progression* :

\begin{equation}
9 \sum_{n=1}^{\infty} 10^{-n}~.
\end{equation}
The series converges in $\mathbb{R}$. Its value can thus be computed using the usual formula

\begin{equation}
\sum_{n=1}^{k} r^n=\frac{r~(1-r^{k})}{1-r}~.
\end{equation}
with $0\leq r<1$,  $r^n\rightarrow 0$, which, in our case gives
\begin{equation}
\sum_{n=1}^{\infty} 10^{-n}=\frac{1}{9}~.
\end{equation}
Which proves the identity.
