---
title: The rubber band theorem
header:
  image: nightsky.jpg
use_math: true
---

Here is a little something that I have been wanting to share for some time but never really took the time to do it.
One day after having eaten the lunch I had carried to work in a lousy box which I usually keep closed using two rubber bands, I started playing around with the rubber bands that were now lying on top of the table up to the point where they looked something like this

![alt]({{ site.url }}{{ site.baseurl }}/images/rubbers1.jpg)



As I really enjoy doing differential geometry, I wondered if there were any fundamental mathematical reasons why the inner rubber band had to take that shape. I had quite a bit of fun in the process of finding an answer to this question and it is my desire to share it here.

The simple and short answer is that the inner rubber band is made to fit within a smaller surface. Full stop. We can be a more interesting than that.

In the language of differential geometry, the inner rubber band can be said to change its local curvature along its perimeter. It is possible to give a perfectly rigorous definition of curvature by considering the angle made by the tangent vector to a curve and some arbitrary axis:


![alt]({{ site.url }}{{ site.baseurl }}/images/curvature-1.png)

The curvature is defined as the instantaneous variation of this angle along the curve. That is

\begin{equation}
k(s)=\frac{d\phi}{ds}~,
\end{equation}
where $s$ is a continuous real parameter varying continuously along the curve.

In general, the curvature varies along the curve

![alt]({{ site.url }}{{ site.baseurl }}/images/curvature.gif)

An intuitive way of looking at this definition is to consider that the angle, $\Delta\phi$, spans a small element of curve that we identify as an arc of length $\Delta s$. We can then imagine that this arc is part of a circle tangent to the curve at the point of interest which has radius
\begin{equation}
\frac{1}{R(s)}=\lim_{\Delta s\rightarrow 0}\frac{\Delta\phi}{\Delta s}=\frac{d\phi}{ds}~.
\end{equation}
The curvature is thus the inverse of the radius of curvature.

What I like about this definition of curvature is that this makes apparent a very elegant result about closed curves. The integral of the curvature on a closed curve is called the *total curvature*. On a closed curve, this integral is:
\begin{equation}
\oint_\mathcal{\gamma} k(s)ds=\oint_\mathcal{\gamma}\frac{d\phi}{ds}ds=n~2\pi~,
\end{equation}
where $n$ is an integer counting the number of times the curve winds around itself called the *winding number*.

This seems almost too elegant to be true. And I wanted to check that for a few curves. The above formula for this purpose is not ideal and should be replaced. But first, I wish to have a more general way of parametrising a curve. It is indeed often useful to use a parameter different to its length.

Let a curve be parametrised in the 3-dimensional space in cartesian coordinates as
\begin{equation}
\vec{\mathcal{\gamma}}^T=(\gamma^x(\lambda),\gamma^y(\lambda),\gamma^z(\lambda))~,
\end{equation}
where $\lambda$ denotes any affine parameter that varies continuously and monotonously along the curve. Then the length element of the said curve can be easily interpreted as being
\begin{equation}
ds=|\vec{\mathcal{\gamma}}(\lambda)|d\lambda~.
\end{equation}
Hence the total length of the curve is
\begin{equation}
S=\oint_\mathcal{\gamma}ds=\oint_\mathcal{\gamma}|\vec{\mathcal{\gamma}}(\lambda)|d\lambda~.
\end{equation}
The expression for the curvature changes accordingly to
\begin{equation}
k(\lambda)=\frac{1}{|\vec{\mathcal{\gamma}}(\lambda)|}\frac{d\phi}{d\lambda}~,
\end{equation}
so that it does not alter the form of the formula for the total curvature:
\begin{equation}
\oint_\mathcal{\gamma} k(s)ds=\int_\mathcal{\gamma}\frac{d\phi}{ds}ds=\int_\mathcal{\gamma}\frac{d\phi}{d\lambda}d\lambda~,
\end{equation}

Now onto finding a more suited expression for the curvature. I will only be bothered with curves in 2d so that $\vec{\mathcal{\gamma}}(\lambda)^T=(x(\lambda),y(\lambda))$. Let's define the angle $\phi$ from
\begin{equation}
\frac{x'(\lambda)}{\sqrt{x'^2+y'^2}}=\cos\phi
\end{equation}
\begin{equation}
\frac{y'(\lambda)}{\sqrt{x'^2+y'^2}}=\cos\phi~.
\end{equation}
Then,
\begin{equation}
\frac{d}{d\lambda}\frac{y'(\lambda)}{\sqrt{x'^2+y'^2}}=\cos\phi\frac{d\phi}{d\lambda}=k(\lambda)|\vec{\mathcal{\gamma}}(\lambda)|\cos\phi=k(\lambda)x'(\lambda)~,
\end{equation}
so that
\begin{equation}
k(\lambda)=\frac{y'' x'-y'x''}{(x'^2+y'^2)^{3/2}}~.
\end{equation}
It's finally time to look at a few curves:

Circle
------
The parameter for the curve is naturally taken as the polar angle:  $\vec{\mathcal{\gamma}}(\theta)^T=(r\cos\theta,r\sin\theta)$ so that the curvature is a constant and simply the inverse of the radius of curvature as expected:
\begin{equation}
k(\theta)=\frac{1}{r}~,
\end{equation}
and its integral gives
\begin{equation}
\int_0^{2\pi}\frac{1}{r}~r~d\theta=2\pi
\end{equation}

Ellipse
------
Let's parametrise the ellipsoid as:  $\vec{\mathcal{\gamma}}(\theta)^T=(a\cos\theta,b\sin\theta)$, using the above formula:
\begin{equation}
k(\theta)=\frac{ab}{(b^2\cos^2\theta+a^2\sin^2\theta)^{3/2}}~,
\end{equation}
The integral is most easily computed numerically

![alt]({{ site.url }}{{ site.baseurl }}/images/integral.png)

Nyquist curve
------

![alt]({{ site.url }}{{ site.baseurl }}/images/nyquist-1.png)

This example is less trivial. The curve winds twice on itself and is parametrised as $\vec{\mathcal{\gamma}}(\theta)^T=(\text{Re}[\frac{1}{(-\frac{1}{2}+e^{it})^2}],-\text{Im}[\frac{1}{(-\frac{1}{2}+e^{it})^2}])$ and its curvature is
\begin{equation}
k(t)=-\frac{1}{16} (5-4 \cos (t))^2 (2 \cos (t)-7) \sqrt{-\frac{1}{(4 \cos
   (t)-5)^3}}~.
\end{equation}
The total curvature is obtained by integrating between $0$ and $2\pi$ and its value is:
\begin{equation}
\int_0^{2\pi}k(t)dt=4\pi~,
\end{equation}
as expected for a curve with a winding number $n=2$.
