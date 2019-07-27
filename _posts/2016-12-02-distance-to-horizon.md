---
title: What is the distance to the horizon ?
date: 2016-12-02
excerpt: "Two mathematicians on the shore of the Pacific ocean"
use_math: true
classes: wide
---

What is the distance that a boat has to sail before it starts disappearing behind the horizon ?

Obviously this depends on the altitude of the observer. It is easy enough to get an approximate answer using Pythagorean geometry but we had a look at this with a pal of mine while on holiday by the ocean and for some reason, it didn't occur to us to use that simple trick then and we went straight for the more complete answer. Here is our take on it. The only approximation we make is that the Earth is perfectly round.

The situation looks like the picture below.

![alt]({{ site.url }}{{ site.baseurl }}/images/horizon.png){: .align-center}

The distance that we are looking for is the red piece of arc labeled $$l$$. We will be sorted if we can find  the $$\theta$$ coordinate of the point where our line of sight is tangent to the Earth. Working with the radius of the Earth as the unit of length, the equation for our line of sight can be guessed from the picture above.

$$
y = 1 + h -x\tan{\theta}~.
$$

In polar coordinates, $$(x,y)=(\sin{\theta},\cos{\theta})$$, so finding $$\theta$$ is just a matter of solving

$$
\cos{\theta} = \frac{1}{1+h}~.
$$

I am $180~$cm tall (6ft), putting this inside the above equation gives a distane of $4.8~$km (about 3mi) to the horizon.

It is interesting to know how this results scales with the height of the observer. Expanding the $$\arccos$$ function in series gives

$$
\theta\sim \sqrt{2}\sqrt{h}+\mathcal{O}[h]^{3/2}~.
$$

Which, incidentally, is the result computed using Pythagorean geometry.
