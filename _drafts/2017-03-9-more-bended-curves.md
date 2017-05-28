---
title: More bended curves
date: 2017-03-9
header:
  image: /images/nightsky.jpg
tags: geometry
use_math: true
---

I am stuck in my work so I give my brain some time off to think of something else before I go back and try solving my problem.

So, let's talk more about differential geometry of curves and stuff.

This post is about the curvature of a circle.

The curvature of a circle of radius $R$ measured **from an euclidian background** is everywhere equal to $\frac{1}{R}$. It is important to emphasise that this definition of the curvature relies on the nature of the euclidian background. Hypothetical 0-dimensional beings living on the surface of the circle wouldn't measure any curvature.

Now lets check that in equations. You will excuse the use of relativist shorthands identifying tensors with their components. This saves me time and effort.

The euclidian background with coordinates $x^\mu=\\{x,y,z\\}$ has its geometry defined by the identity metric read from its line element (in 3D):

\begin{equation}
ds^2=dx^2+dy^2+dz^2~.
\label{eq:ds2}
\end{equation}

Let's define the circle of radius $R$ as the collection of points satisfying:

\begin{equation}
\Phi=x^2+y^2+z^2-R^2=0
\label{eq:condition}
\end{equation}

A single coordinate suffices to locate points on the circle. Using spherical coordinates, one can define a local map to the embedded circle:

$$
\begin{cases}
x = R\cos\phi_0\sin\theta \\
y = R\sin\phi_0\sin\theta \\
z = R\cos\theta
\label{eq:emb}
\end{cases}~.  
$$

One easily checks that it satisfies condition (\ref{eq:condition}). $\phi_0$ is taken as a constant and $y^a=\\{\theta\\}$ is our coordinate on the circle.

Now, the induced metric on the circle in the coordinates $y^a$ is most easily guessed by pluging in the above local map into the line-element (\ref{eq:ds2}). Let's do things more rigorously though and use the definition for the induced metric $\gamma_{\mu\nu}$:

\begin{equation}
\gamma_{\mu\nu}=g_{\mu\nu}-\epsilon n_\mu n_\nu~,
\end{equation}

where $n_\mu$ is the normalised one-form orthogonal to the circle. This is computed from the definition using the constraint (\ref{eq:condition}):

\begin{equation}
n_\mu=\frac{∂\Phi}{∂x^\mu}~,
\end{equation}
and then normalised to $\epsilon = 1$. In case the background metric pseudo-Riemannian, one has $\epsilon=-1$ for space-like surfaces. This is of no concern to us. Here we have:

\begin{equation}
n_\mu=\\{\frac{x}{\sqrt{x^2+y^2+z^2}},\frac{y}{\sqrt{x^2+y^2+z^2}},\frac{z}{\sqrt{x^2+y^2+z^2}}\\}~.
\end{equation}

So that the induced metric has the form:

$$
\gamma_{\mu\nu}=\left(
\begin{array}{ccc}
 \frac{y^2+z^2}{x^2+y^2+z^2} & -\frac{x y}{x^2+y^2+z^2} & -\frac{x z}{x^2+y^2+z^2} \\
 -\frac{x y}{x^2+y^2+z^2} & \frac{x^2+z^2}{x^2+y^2+z^2} & -\frac{y z}{x^2+y^2+z^2} \\
 -\frac{x z}{x^2+y^2+z^2} & -\frac{y z}{x^2+y^2+z^2} & \frac{x^2+y^2}{x^2+y^2+z^2} \\
\end{array}
\right)
$$
