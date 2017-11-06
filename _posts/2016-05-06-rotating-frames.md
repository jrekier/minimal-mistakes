---
title: Dynamics in non-inertial reference frames
date: 2016-05-06
excerpt: "Throwing balls on a spinning plate"
header:
  overlay_image: /images/nightsky.jpg
  overlay_filter: 0.5
use_math: true
---

At work, we have to solve dynamical problem in non-inertial reference frames all the time. This simplifies the statement of the problem. But sometimes it makes it difficult to understand the solution as you can't build your interpretation on habits that you have that are only valid in an inertial frame.

At first it was sometimes quite difficult for me to make sense of any answer computed in a rotating frame, for instance.

So I thought I would go back to basics and do a bit of point-particle mechanics in such frames before moving on to more interesting stuff.

In the absence of external forces, the Lagrange function is the kinetic energy of the particle with its total velocity written as a combination of its own velocity plus the contribution to the rotation of the whole frame:

\begin{align}
L &= \frac{1}{2}m\left|~\dot{\vec{r}}+\vec{\omega}\times\vec{r}~\right|^2\\\\\\
  &= \frac{1}{2}m\left|\dot{\vec{r}}\right|^2+m~\vec{\omega}\cdot\left(\vec{r}\times\dot{\vec{r}}\right)+\frac{1}{2}m\left[\omega^2r^2-(\vec{\omega}\cdot\vec{r})^2\right]
\end{align}

Setting $~\vec{\omega}^{T}=\left(0,0,\omega\right)$ constrains the motion in the xy-plane by conservation of angular momentum. The Lagrangian becomes

$$
L = \frac{1}{2}\left(\dot{x}^2+\dot{y}^2\right)+m\omega(x\dot{y}-y\dot{x})+\frac{1}{2}\omega^2(x^2+y^2)
$$

The motion in the two directions can then be derived by using the Euler-Lagrange equations. These give a system of first order differential equations with an interesting shape:

\begin{align}
\frac{d}{dt}
\begin{pmatrix}
x\\\\\\
\dot{x}\\\\\\
y\\\\\\
\dot{y}
\end{pmatrix}
=
\begin{pmatrix}
0&1&0&0\\\\\\
\omega^2&0&0&2\omega\\\\\\
0&0&0&1\\\\\\
0&-2\omega&\omega^2&0
\end{pmatrix}
\begin{pmatrix}
x\\\\\\
\dot{x}\\\\\\
y\\\\\\ \dot{y}
\end{pmatrix}
\end{align}

Call the solution array $X(t)$ and the matrix on the right-hand-side $A[\omega]$, the formal solution to the system is

$$
X(t)=e^{A[\omega]t}\cdot X(0)
$$

The matrix exponential on the right-hand-side being the **propagator**. Here is its full expression:

\begin{align}
e^{A[\omega]t}=\left(
\begin{array}{cccc}
 \cos (t \omega )+t \omega  \sin (t \omega ) & t \cos (t \omega ) & \
\sin (t \omega )-t \omega  \cos (t \omega ) & t \sin (t \omega ) \\\\\\
 t \omega ^2 \cos (t \omega ) & \cos (t \omega )-t \omega  \sin (t \
\omega ) & t \omega ^2 \sin (t \omega ) & t \omega  \cos (t \omega )+\
\sin (t \omega
) \\\\\\
 t \omega  \cos (t \omega )-\sin (t \omega ) & -t \sin (t \omega ) & \
\cos (t \omega )+t \omega  \sin (t \omega ) & t \cos (t \omega ) \\\\\\
 -t \omega ^2 \sin (t \omega ) & -t \omega  \cos (t \omega )-\sin (t \
\omega ) & t \omega ^2 \cos (t \omega ) & \cos (t \omega )-t \omega  \
\sin (t
\omega ) \\\\\\
\end{array}
\right)\
\end{align}

To see the effect of this matrix better, you can apply it to some initial conditions where the particle starts at the centre and start its motion in the x-direction with unit velocity: $X(0)^T=(0,1,0,0)$. The motion then looks something like this :
![alt]({{ site.url }}{{ site.baseurl }}/images/trajectory1.jpg)
In the above, the trajectory is shown in blue and the velocity vector at some given time values is shown in red. The figure was obtained after setting $\omega=1$ and solving from $t=0$ to $t=20$. Interestingly, one can see that the end position in the x-direction is 20, which is also the position that the particle would reach if it was moving in a straight-line along the x-direction with constant velocity 1. This is what we would see from the inertial frame.

For more fun, let's find the initial conditions to reach the centre of coordinates from some outside point ($x_0,y_0$) after a time $t_c$ (*central time*). These read

\begin{align}
v_x^0&=-\frac{x_0-y_0\omega t_c}{t_c}\\\\\\
v_y^0&=-\frac{y_0+x_0\omega t_c}{t_c}
\end{align}

You can understand these better by setting $y_0=0$. which give

\begin{align}
v_x^0&=-\frac{x_0}{t_c}\\\\\\
v_y^0&=-\omega x_0
\end{align}

The first of these is the mean velocity necessary to reach the centre in the time $t=t_c$. The second is the velocity necessary to counteract the velocity of rotation at a distance $x_0$ from the centre.

Setting $x_0=1$, the position vector of the particle reads

$$
\vec{r}=(1-\frac{t}{t_c})\cos \omega t~\vec{e}_x - (1-\frac{t}{t_c})\sin \omega t~\vec{e}_y
$$

As an exercise, let's write this vector in the inertial frame. The vector basis of the rotating frame {$\vec{e}_x$,$\vec{e}_y$} written in terms of the inertial frame basis {$\vec{X}$,$\vec{Y}$} looks like

\begin{align}
\begin{pmatrix}
\vec{e}_x\\\\\\
\vec{e}_y
\end{pmatrix}
=
\begin{pmatrix}
\cos\omega t & \sin\omega t\\\\\\
-\sin\omega t & \cos\omega t \end{pmatrix}\begin{pmatrix}\vec{X}\\\\\\
\vec{Y}
\end{pmatrix}
\end{align}

which gives the final result :

$$
\vec{r}=\left(1+v_x^0t\right)\vec{X}
$$

This is indeed the correct expression for a particle moving in a straight line with a constant velocity.

The next picture shows the comparison between the trajectory as seen from the rotating and inertial frames with the corresponding velocity vectors :
![alt]({{ site.url }}{{ site.baseurl }}/images/trajectory2.jpg)

The velocity of the particle is not zero when it reaches the centre of coordinates so that it does not just stay in place.

The last picture shows the motion of the particle after it has reached the centre. Note that it is symmetrical and also a *lovely* way to close this post.
![alt]({{ site.url }}{{ site.baseurl }}/images/trajectory3.jpg)
