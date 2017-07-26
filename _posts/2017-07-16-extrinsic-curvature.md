---
title: An example in using the Riemann package
date: 2017-07-15
header:
  image: /images/math.jpg
use_math: true
---

I started a Mathematica package to performs computations of Riemannian geometry. As an exercise in using it, I present here the computation of the curvature of a 2-sphere embedded in the euclidean space. The package is in development and its content is not meant to be exhaustive. This suffices however to perform most common computations on (pseudo-)Riemannian real manifolds. It is available from its own [GitHub repository](https://github.com/jrekier/Riemann) along with the notebook for the computation.

For something more general, I recommend you take a look at [SageManifolds](http://sagemanifolds.obspm.fr/).

Start by defining a background 3-dimensional euclidean space by providing a set of coordinates $\{x,y,z\}$ and a metric in the form of a squared line-element:
\begin{equation}
ds^2=dx^2+dy^2+dz^2~.
\end{equation}
\begin{align}
g=\left(
\begin{array}{ccc}
 1 & 0 & 0 \\\\\\
 0 & 1 & 0 \\\\\\
 0 & 0 & 1 \\\\\\
\end{array}
\right)~.
\end{align}

One way to embed in the 2-sphere of radius $R$ is by imposing that
\begin{equation}
\Phi \equiv x^2+y^2+z^2 - R^2 = 0~,
\end{equation}
with $R>0$. One parametrisation satisfying this constraint is
\begin{align}
x&=R \sin{\theta}\cos{\phi}~,\\\\\\
y&=R \sin{\theta}\sin{\phi}~,\\\\\\
z&=R \cos{\theta}~,
\label{eq:mapSigma}
\end{align}
with $\{\theta, \phi\}$ taking up the role of local ordinates on the 2-sphere thus described which we will denote $\Sigma$ for simplicity.

The components of the one-form normal to $\Sigma$ are obtained as follows
\begin{equation}
n_\alpha = \frac{\partial \Phi}{\partial x^\alpha}~.
\end{equation}
Once it has been normalised, this turns out to be

$$
\{\frac{x}{\sqrt{x^2+y^2+z^2}},\frac{y}{\sqrt{x^2+y^2+z^2}},\frac{z}{\sqrt{x^2+y^2+z^2}}\}
$$

The general expression of the projector onto $\Sigma$ is
\begin{equation}
P_{\alpha\beta}=g_{\alpha\beta}-n_\alpha n_\beta~.
\end{equation}
Here this gives:

\begin{align}
\left(
\begin{array}{ccc}
 \frac{y^2+z^2}{x^2+y^2+z^2} & -\frac{x y}{x^2+y^2+z^2} & -\frac{x
   z}{x^2+y^2+z^2} \\\\\\
 -\frac{x y}{x^2+y^2+z^2} & \frac{x^2+z^2}{x^2+y^2+z^2} & -\frac{y
   z}{x^2+y^2+z^2} \\\\\\
 -\frac{x z}{x^2+y^2+z^2} & -\frac{y z}{x^2+y^2+z^2} &
   \frac{x^2+y^2}{x^2+y^2+z^2} \\\\\\
\end{array}
\right)
\end{align}

Finally, the extrinsic curvature is the Lie derivative of this tensor along the normal vector defined above:

\begin{equation}
K_{\alpha\beta}=-\frac{1}{2}L_n P_{\alpha\beta}~.
\end{equation}
Here this gives:

\begin{align}
\left(
\begin{array}{ccc}
 -\frac{y^2+z^2}{\left(x^2+y^2+z^2\right)^{3/2}} & \frac{x
   y}{\left(x^2+y^2+z^2\right)^{3/2}} & \frac{x
   z}{\left(x^2+y^2+z^2\right)^{3/2}} \\\\\\
 \frac{x y}{\left(x^2+y^2+z^2\right)^{3/2}} &
   -\frac{x^2+z^2}{\left(x^2+y^2+z^2\right)^{3/2}} & \frac{y
   z}{\left(x^2+y^2+z^2\right)^{3/2}} \\\\\\
 \frac{x z}{\left(x^2+y^2+z^2\right)^{3/2}} & \frac{y
   z}{\left(x^2+y^2+z^2\right)^{3/2}} &
   -\frac{x^2+y^2}{\left(x^2+y^2+z^2\right)^{3/2}} \\\\\\
\end{array}
\right)
\end{align}

The mean curvature is given by the trace of this tensor and here is found to be
\begin{equation}
\text{Tr}~K=-\frac{2}{R}
\label{eq:trK}
\end{equation}

All the above was done using only vectors (and one-forms) belonging to the (co-)tangent bundle of the surrounding $\mathbb{R}^3$ without any explicit reference to the local coordinates on $S^2$. The extrinsic curvature also has a representation on $S^2$.

From (\ref{eq:mapSigma}), one constructs the *vielbein*:
\begin{equation}
e^\alpha_a=\frac{\partial x^\alpha}{\partial y^a}~,
\end{equation}
where $x^\alpha$ denotes the coordinates on $\mathbb{R}^3$, $$\{x,y,z\}$$ and $y^a$ are the coordinates on $S^2$, $$\{\theta,\phi\}$$. In the matrix form, this reads on our case:
\begin{align}
\left(
\begin{array}{cc}
 R \cos (\theta ) \cos (\phi ) & -R \sin (\theta ) \sin (\phi ) \\\\\\
 R \cos (\theta ) \sin (\phi ) & R \cos (\phi ) \sin (\theta ) \\\\\\
 -R \sin (\theta ) & 0 \\\\\\
\end{array}
\right)
\end{align}

The induced metric on $\Sigma$ can then be computed with
\begin{equation}
\gamma_{ab} = e^\alpha_ae^\beta_bg_{\alpha\beta}~,
\label{eq:inducedgamma}
\end{equation}
which here gives:
\begin{align}
\left(
\begin{array}{cc}
 R^2 & 0 \\\\\\
 0 & R^2 \sin ^2(\theta ) \\\\\\
\end{array}
\right)
\end{align}
Applying a transformation similar to (\ref{eq:inducedgamma}) to the extrinsic curvature gives
\begin{align}
\left(
\begin{array}{cc}
 -R & 0 \\\\\\
 0 & -R \sin ^2(\theta ) \\\\\\
\end{array}
\right)
\end{align}
and so we recover (\ref{eq:trK}) by taking the trace ($\gamma^{ab}K_{ab}$).
