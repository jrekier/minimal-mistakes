---
title: Motion of planets
date: 2017-01-27
header:
  image: /images/nightsky.jpg
use_math: true
---

The study of the motion of a particle in a central potential is a classical exercise of dynamics. I first go through the computation using Newtonian physics.

The starting point is the Lagrangian of a particle with mass m subjected to the central potential V(r) in polar coordinates:
\begin{equation}
\mathcal{L}=\frac{1}{2}m(\dot{r}^2+r^2\dot{\theta}^2)-V(r)~,
\end{equation}
This does not depend explicitely on $$\theta$$ and so the following quantity is conserved and identified as the angular momentum
\begin{equation}
L=mr^2\dot{\theta}~.
\end{equation}

Writing the potential as $$V(r)=\frac{-\alpha}{r}$$ The equations of motion are
\begin{equation}
m\ddot{r}+\frac{\alpha}{r^2}-\frac{L^2}{mr^3}=0~,
\end{equation}
\begin{equation}
r\ddot{\theta}+2\dot{r}\dot{\theta}=0~.
\end{equation}
The first one can be solved easily and then inserted into the second one.
Textbooks, at that point, usually pursue the analytical computation to show that the particle moves in an ellipse or a parabola depending if it is bound to the potential or not. Here we will just solve these equations numerically and see how the motion changes with the value of free parameters.

We first set the axes. We will set up our study in the fashion of a standard scattering problem. The motion is 2 dimensional so we only need coordinates $$x$$ and $$y$$. We take the initial value of the $$y$$-coordinate $$y_0$$ as the *impact parameter*. Corresponding to the distance by which the particle would miss the centre of coordinate if there was no potential there.  

![alt]({{ site.url }}{{ site.baseurl }}/images/capture_orbit1.png){: .align-center}
