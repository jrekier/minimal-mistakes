---
title: The decimal point is ambiguous
header:
  image: /images/nightsky.jpg
use_math: true
---

Many numbers can be symbolically written in more than one way. For example:

$$1=\frac{1}{1}=\frac{2}{2}=\frac{3}{3}=\cdots$$

The decimal point notation also has its own problems. It is common knowledge that

$$1=0.99999999\cdots~,$$

with the series of $9$s repeated ad infinitum. There are many ways to prove the identity. Here is one.

The right-hand side can be written:

\begin{equation}
9 \sum_{n=1}^{\infty} 10^{-n}~.
\end{equation}
The series converges in $\mathbb{R}$ and is just the geometric series of reason $\frac{1}{10}$. Its value can thus be computed using the usual formula

\begin{equation}
\sum_{n=0}^{k-1} r^n=\frac{1-r^k}{1-r}~.
\end{equation}
with $0\leq r<1$,  $r^n\rightarrow 0$ and
\begin{equation}
\sum_{n=1}^{\infty} 10^{-n}=\frac{1}{9}~.
\end{equation}
Which proves the identity. In the end, this is just a matter of playing around with infinity.
