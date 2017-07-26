---
title: What happens when you accelerate to reach the speed of light ?
date: 2015-06-27
excerpt: "No black hole involved, sadly."
header:
  overlay_image: /images/math.jpg
  overlay_filter: 0.5
use_math: true
---

The ultimate speed limit of the Universe is the speed of light which nothing can overtop. What would happen then to an object on which a constant force is exerted in one direction?

Newton's second law predicts that its velocity should grow following

$$
 F = m\frac{dv}{dt}~,
$$

where $F$ is the force, $m$ is the mass of the object at rest and $\frac{dv}{dt}$ is the instantaneous rate of change in the velocity of the object (its first time derivative). Following Newton, this would mean that the velocity of the object should grow linearly.

But Newton's theory is incomplete and so is the above equation.

Newton's equation can be put in the form

$$
 F = \frac{dp}{dt}~,
$$

where $$p$$ is the momentum of the object. Setting $p=mv$ a is valid for objects moving slowly relative to the speed of light gives back our original expression of Newton's law. But $p=mv$ is invalid when one takes into account the effects of *Special Relativity*. The true expression for the momentum of a point-like object is in fact

$$
 p = \frac{mv}{\sqrt{1-\frac{v^2}{c^2}}}~.
$$

When this is put in Newton's equation, this gives an ordinary differential equation for the evolution of the velocity:

$$
 \frac{dv}{dt} = \frac{F}{m}\left(1-\frac{v^2}{c^2}\right)^{3/2}~.
$$

By imposing that the object is initially at rest, the solution of the above is

$$
 v(t)=\frac{c F t}{\sqrt{c^2m^2+F^2t^2}}~.
$$

Here is a plot of the solution along with the Newtonian solution with $F=m=c=1$.

![alt]({{ site.url }}{{ site.baseurl }}/images/speed_limit_fig_1.svg)

The velocity of the object never reaches that of light.
