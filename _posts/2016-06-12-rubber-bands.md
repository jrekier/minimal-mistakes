---
title: The rubber band theorem
date: 2016-08-30
header:
  image: nightsky.jpg
use_math: true
---

Here is a little something that I have wanted to share for a long time.
One day I had carried to work in a lousy box which kept closed with two rubber bands, I started playing around with these until they looked like this

![alt]({{ site.url }}{{ site.baseurl }}/images/rubbers1.jpg){: .align-center}


I wondered if there were any mathematical reasons why the inner rubber band had to take that shape.

The simple and short answer is that the inner rubber band is made to fit within a smaller surface. But I really wanted to know the reason for this bulge in the inner curve.

In the language of differential geometry, the inner rubber band changes its curvature along its perimeter. It is possible to give a definition of curvature by looking the angle made by the tangent vector to a curve and some arbitrary axis:

![alt]({{ site.url }}{{ site.baseurl }}/images/curvature-1.png){: .align-center}

The curvature is defined as the instantaneous variation of this angle along the curve. That is

\begin{equation}
k(s)=\frac{d\phi}{ds}~,
\end{equation}
where $s$ is a continuous real parameter varying continuously along the curve.

The curvature varies and changes sign with concavity.

![alt]({{ site.url }}{{ site.baseurl }}/images/curvature.gif){: .align-center}

An intuitive way to look at this is to consider that the angle, $\Delta\phi$, spans a small element of curve that we identify as an arc of length $\Delta s$. Imagine then that this arc is part of a circle tangent to the curve at the point of interest. That circle has radius of
\begin{equation}
\frac{1}{R(s)}=\lim_{\Delta s\rightarrow 0}\frac{\Delta\phi}{\Delta s}=\frac{d\phi}{ds}~.
\end{equation}
The curvature at a point is then the inverse of the radius of curvature of the imaginary circle tangent to the curve at this point.

What I like about this definition of curvature is that this makes apparent a very elegant result about closed curves. The integral of the curvature along a closed curve (*total curvature*) is
\begin{equation}
\oint_\mathcal{\gamma} k(s)ds=\oint_\mathcal{\gamma}\frac{d\phi}{ds}ds=n~2\pi~,
\end{equation}
where $n$ is an integer counting the number of times the curve winds around itself called the *winding number*.

This seems too beautiful to be true. So I wanted to check with some examples. The above formula for the curvature is not ideal for this and should be replaced. But first, I wish to have a more general way of parametrising a curve. It is often useful to use a parameter other than the length element.

Let a curve be parametrised in 3d space using cartesian coordinates as
\begin{equation}
\vec{\mathcal{\gamma}}^T=(\gamma^x(\lambda),\gamma^y(\lambda),\gamma^z(\lambda))~,
\end{equation}
where $\lambda$ denotes any affine parameter that varies continuously and monotonously along the curve. Then the length element of the said curve is
\begin{equation}
ds=|\vec{\mathcal{\gamma}}(\lambda)|d\lambda~.
\end{equation}
Hence the total length of the curve is
\begin{equation}
S=\oint_\mathcal{\gamma}ds=\oint_\mathcal{\gamma}|\vec{\mathcal{\gamma}}(\lambda)|d\lambda~.
\end{equation}
The expression for the curvature then changes to
\begin{equation}
k(\lambda)=\frac{1}{|\vec{\mathcal{\gamma}}(\lambda)|}\frac{d\phi}{d\lambda}~,
\end{equation}
so that it does not alter the form of the formula for the total curvature:
\begin{equation}
\oint_\mathcal{\gamma} k(s)ds=\int_\mathcal{\gamma}\frac{d\phi}{ds}ds=\int_\mathcal{\gamma}\frac{d\phi}{d\lambda}d\lambda~,
\end{equation}

I will only be bothered with curves in 2d so that $\vec{\mathcal{\gamma}}(\lambda)^T=(x(\lambda),y(\lambda))$. Let's define the angle $\phi$ from
\begin{equation}
\frac{x'(\lambda)}{\sqrt{x'^2+y'^2}}=\cos\phi
\end{equation}
\begin{equation}
\frac{y'(\lambda)}{\sqrt{x'^2+y'^2}}=\sin\phi~.
\end{equation}
Then,
\begin{equation}
\frac{d}{d\lambda}\frac{y'(\lambda)}{\sqrt{x'^2+y'^2}}=\cos\phi\frac{d\phi}{d\lambda}=k(\lambda)|\vec{\mathcal{\gamma}}(\lambda)|\cos\phi=k(\lambda)x'(\lambda)~,
\end{equation}
so that
\begin{equation}
k(\lambda)=\frac{y'' x'-y'x''}{(x'^2+y'^2)^{3/2}}~.
\end{equation}
This is the more practical expression for the curvature that we were looking for.
Time to look at a few curves:

Circle
------
The parameter for the curve is taken as the polar angle:  $\vec{\mathcal{\gamma}}(\theta)^T=(r\cos\theta,r\sin\theta)$ so that the curvature is a constant and simply the inverse of the radius of curvature:
\begin{equation}
k(\theta)=\frac{1}{r}~,
\end{equation}
and its integral gives
\begin{equation}
\int_0^{2\pi}\frac{1}{r}~r~d\theta=2\pi
\end{equation}

Ellipse
------
Let's parametrise the ellipsoid as:  $\vec{\mathcal{\gamma}}(\theta)^T=(a\cos\theta,b\sin\theta)$, then:
\begin{equation}
k(\theta)=\frac{ab}{(b^2\cos^2\theta+a^2\sin^2\theta)^{3/2}}~,
\end{equation}
The integral is most easily computed numerically

![alt]({{ site.url }}{{ site.baseurl }}/images/integral.png){: .align-center}

Nyquist curve
------

![alt]({{ site.url }}{{ site.baseurl }}/images/nyquist-1.png){: .align-center}

This example is less trivial. The curve winds twice on itself and is parametrised as $\vec{\mathcal{\gamma}}(t)^T=(\text{Re}[\frac{1}{(-\frac{1}{2}+e^{it})^2}],-\text{Im}[\frac{1}{(-\frac{1}{2}+e^{it})^2}])$ and its curvature is
\begin{equation}
k(t)=-\frac{1}{16} (5-4 \cos (t))^2 (2 \cos (t)-7) \sqrt{-\frac{1}{(4 \cos
   (t)-5)^3}}~.
\end{equation}
The total curvature is obtained by integrating between $0$ and $2\pi$ and its value is:
\begin{equation}
\int_0^{2\pi}k(t)dt=4\pi~,
\end{equation}
as expected for a curve with a winding number $n=2$.

Now that I am more convinced, I can understand the reason for the bulge in the rubber band of the first picture.

As the inner rubber band is forced within the surface enclosed by the other one, its curvature must be bigger on a large portion of the curve (more positive). However, as the total curvature must remain equal to $2\pi$, there has to be a region of the curve with negative curvature to compensate. Hence the bulge.

Incidentally, there *is* a way of getting one rubber band inside another without the bulge, you just need to increase the winding number.

![alt]({{ site.url }}{{ site.baseurl }}/images/rubbers2.jpg){: .align-center}
