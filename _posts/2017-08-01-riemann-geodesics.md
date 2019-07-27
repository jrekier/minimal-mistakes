---
title: Trajectories in the Schwarzschild space-time
date: 2017-08-01
excerpt: "Using the Riemann package"
header:
  overlay_image: /images/nightsky.jpg
  overlay_filter: 0.5
use_math: true
classes: wide
---

Using the [Riemann package to do Riemannian geometry]({{ site.baseurl }}{% post_url 2017-07-16-extrinsic-curvature %}), one can easily perform computations in General Realtivity. In this post, I am going to show how one could compute motions in the Schwarzschild metric.

The complete computation can be retrieved in a dedicated notebook [Schwarzschild geodesic.md](https://github.com/jrekier/Riemann).

Before tackling the space-time problem, let's warm up by considering the simpler two-dimensional space with line-element:

# Space

\begin{equation}
ds^2=\frac{dr^2}{(1-\frac{r_s}{r})}+r^2d\phi^2~,
\end{equation}
where $$\{r,\phi\}$$ are the usual polar coordinates. The parameter $r_s$ stands for the Schwarzschild radius. In a complete space-time computation, this is proportional to the mass at the centre of coordinates.

The geodesic of this space are curves satisfying the equations

\begin{equation}
\frac{d^2x^\alpha}{d\lambda^2}+\Gamma^\alpha_{\beta\gamma}\frac{dx^\beta}{d\lambda}\frac{dx^\gamma}{d\lambda}=0~.
\end{equation}
where $$\{x^\mu\}_{\mu=1,..,d}$$ stands for the set of coordinates of space considered to be functions of a single affine parameter $\lambda$ thus describing one-dimensional curves. The $\Gamma$s are the Christoffel symbols. We are using Einstein's convention where indices repeated in a product implies summation on the said indices.

I have included a function to compute these equations inside the notebook. The steps are

<figure class="half">
    <a href="{{ site.url }}{{ site.baseurl }}/images/posts_data/riemann-geodesic/cell1.png"><img src="{{ site.url }}{{ site.baseurl }}/images/posts_data/riemann-geodesic/cell1.png"></a>
</figure>

to produce:
\begin{equation}
\begin{array}{c}
 r''(\lambda )+\frac{r_s r'(\lambda )^2}{2 r_s r(\lambda
   )-2 r(\lambda )^2}+\phi'(\lambda )^2 (r_s-r(\lambda ))=0 \\\\\\
 \phi''(\lambda )+\frac{2 \phi'(\lambda ) r'(\lambda )}{r(\lambda)}=0 \\
\end{array}
\end{equation}

The analytical resolution of these equation needs not concern us at the moment. For purposes of illustration, we can be content with a numerical resolution. We set up some initial conditions and do

![cell2]({{ site.url }}{{ site.baseurl }}/images/posts_data/riemann-geodesic/cell2.png)

and plot the result as a parametric curve. Anticipating on the computation in space-time, we can plot our result curve on the Flamm's paraboloid representing the following embedding in 3d space:
\begin{equation}
\\{x = r \cos (\phi ),~y = r \sin (\phi ),~z = 2 \sqrt{r-1}\\}
\end{equation}
The function `Embedding3D` in the preamble to the notebook has been written to serve that visualisation purpose:

![flamm1]({{ site.url }}{{ site.baseurl }}/images/posts_data/riemann-geodesic/flamm1.png){: .align-center}

The blue line in the figure is the geodesic of the 2-dimensional given the initial conditions provided. Gravity is not taken into account.

# Space-time

In order to take gravity into account, one must consider the complete spacetime metric given by the line element:
\begin{equation}
ds^2=-\left(1-\frac{r_s}{r}\right)dt^2+\frac{dr^2}{(1-\frac{r_s}{r})}+r^2d\theta^2+r^2\sin(\theta)^2d\phi^2~,
\end{equation}
where $$\{t,r,\theta,\phi\}$$ are the combination of time and usual spherical coordinates.

In this case, the geodesic equations are (using the same function from the package as before):

\begin{align}
 t''(\lambda )-\frac{r_s r'(\lambda ) t'(\lambda )}{r_s r(\lambda )-r(\lambda )^2}=0& \\\\\\
 r''(\lambda )+\frac{r_s r'(\lambda )^2}{2 r_s r(\lambda)-2 r(\lambda )^2}+\theta'(\lambda )^2(r_s-r(\lambda ))+&\\\\\\
 \sin^2(\theta (\lambda )) \phi'(\lambda )^2 (r_s-r(\lambda))+\frac{r_s(r(\lambda )-r_s) t'(\lambda )^2}{2r(\lambda )^3}=0& \\\\\\
 \sin (\theta (\lambda )) \cos (\theta (\lambda )) \phi'(\lambda)^2-\theta''(\lambda )-\frac{2\theta'(\lambda ) r'(\lambda)}{r(\lambda )}=0& \\\\\\
 2 \theta'(\lambda ) \cot (\theta (\lambda )) \phi'(\lambda )+\phi''(\lambda )+\frac{2\phi'(\lambda ) r'(\lambda )}{r(\lambda )}=0&~.
\end{align}

We can solve these numerically as we did for the purely spatial case. There is however an extra subtlety here as one must not fail to consider the extra constraint induced by the *principle of equivalence*. We will first address the case where the particle has mass and then move on to the case of a massless particle.

## massive particle

The equivalence principle states that, at any point of space-time, the laws of motion must be reducible to those of special relativity by an adequate choice of local coordinates. This corresponds to the choice of a free-falling frame of reference. In the case of a massive particle, this amounts to demand that
\begin{equation}
ds^2=-d\lambda^2~,\label{eq:ds2mass}
\end{equation}
locally, where $$\lambda$$ is here interpreted as the proper-time of the particle. In practice, it means that, if one sets the initial value of all the coordinates functions $$x^\mu(\lambda)$$ and their derivatives except for $t'(\lambda)$, this latter quantity must be determined using Eq.~\ref{eq:ds2mass} . All this is done in the notebook. Once everything has been set up properly, we can finally see some cool physics happen. Below is a plot of a trajectory in the equatorial plane. This corresponds to initial conditions where the particle starts at $r=10$ and with a very small azimuthal velocity $\phi'=\frac{1}{50}$ so it begins to orbit the centre of coordinates. The Schwarzschild's radius here is set to $r_s=1$.

![trajectory]({{ site.url }}{{ site.baseurl }}/images/posts_data/riemann-geodesic/trajectory2d.png)

The orbit is not closed. It would be interesting to compare this with the result of Newtonian dynamics which I might just do in a future post. The figure below shows the same trajectory embedded on the surface of Flamm's paraboloid.

![trajectory]({{ site.url }}{{ site.baseurl }}/images/posts_data/riemann-geodesic/flamm2.png)

## massless particle

The discussion on the choice of initial value presented above in the case of a massive particle needs to be modified in order to be applied here.
Firstly, one must realise that the idead of proper-time is ill-defined for a massless particle and one must decide on another affine parameter to use. Perhaps the most natural choice is simply to use the length of the curve $\lambda=\ell$. Differentiation both sides with respect to $\lambda$ and taking the square leads to
\begin{equation}
\left(\frac{d\ell}{d\lambda}\right)^2=1~,
\label{eq:constr1}
\end{equation}
which sets a contraint on the spatial part of the metric.
One should also notice that the condition that the particle being massless, it must always travel at the speed of light which entails the constraint
\begin{equation}
ds^2=0~.
\label{eq:constr2}
\end{equation}
The above two constraints have to be satisfied simultaneously at all points of the trajectory and in particular by the initial conditions.

The figure below shows one such trajectory in the equatorial plane for a particle starting at $r=5$ with a small initial coordinate velocity towards the centre $r'=-0.5$ which constraints the azimuthal velocity to $\phi'=\frac{\sqrt{1-r'^2}}{r}$. The Schwarzschild's radius is set to $r_s=\frac{5}{3}$.

![trajectory]({{ site.url }}{{ site.baseurl }}/images/posts_data/riemann-geodesic/trajectory2d2.png)

The above clearly demonstrates the effect of space-time curvature on the trajectories of a massless particle. It is perhaps the most stringent departure of general relativity from Newtonian physics that light rays are bent by gravitational fields.

In order to render that fact even more vividly, we can compare our results to that obtained by performing the same computation but setting the Schwarzschild's radius to $r_s=0$ thus effectively describing Minkowski's space-time. You will find both curves on the picture below embedded into Flamm's paraboloid.

![trajectory]({{ site.url }}{{ site.baseurl }}/images/posts_data/riemann-geodesic/flamm3.png)

The blue curves is the solution for $r_s=\frac{5}{3}$, the yellow one is the one for $r_s=0$ thus corresponding to the solution of Newtonian physics in which light rays travels in space unaffected by gravitational fields.

# wrapping things up

In this post, I tried to show how one could use `Riemann` to perform practical computations of General relativity. The above examples treated only geodesic equations but I hope to be able to present you other usages in the future.
