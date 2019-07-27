---
title: Simple model of a bouncing ball
date: 2017-11-06
excerpt: "the nature of infinity"
use_math: true
classes: wide
tags:
  - math
---

Everyone has heard the sound of a ball bouncing off the floor after being dropped from a certain height. This makes a distinctive *thud—thud—thud-thu-th-tt-tt-t-…* with the sound of every rebound coming closer to the next as time goes. This is due to the fact that the ball loses some of its energy as it goes. In this post, I'll give a very simplistic model for this and hopefully learn something along the way.

Let's assume that the ball loses a fraction $\alpha$ of its energy everytime it touches the ground. We neglect the dragging force of the wind when the ball is in the air. The ratio of the energy between rebound $n$ and $n-1$ is then

$$\frac{E_n}{E_{n-1}}=(1-\alpha)~.$$

How can we measure the damping $\alpha$ ?

After it has bounced, the ball reaches some maximum height at which it comes to rest and so all its energy is gravitational potential energy. The ratio of height between two rebounds can therefore be guessed to be

$$\frac{h_n}{h_{n-1}}=(1-\alpha)~.$$

Now, it might be inpractical to measure the height of the ball before and after a given rebound. It is much easier to measure time intervals. From elementary kinematic, we know that the ball will drop from height $h_n$ in a time

$$t=\sqrt{\frac{2 h_n}{g}}~,$$

with $g$ being the gravitational acceleration. The ball rmakes a return trip from the ground up to its maximum height and back to the ground after it has bounced. The total time spent in the air between the rebound $n$ and $n+1$ is therefore:

$$t_n=2\sqrt{\frac{2h_n}{g}}~.$$

The ratio of two such succesive time intervals is then

$$\frac{t_n}{t_{n-1}}=(1-\alpha)^{\frac{1}{2}}~.$$

It is interesting to see that, in this very idealised model, the ratio between any two succesive time interval is constant.

How long will it take for the ball stop bouncing and come to a rest on the floor ? And after how many rebounds ? The answer to the first question is fairly easy to give but the answer to the second one may come as a bit of a surprise.

 For the sake of simplicity, we further assume that the ball instantly transfer its energy to the ground as it bounces back. This is of course an idealisation. The total time spent in the air for an initial drop from height $h_0$ followed by $N$ rebounds is

$$T=t_0+\sum_{n=1}^Nt_n$$

with $t_0$ being the time for the initial drop and $t_n$ represents the time in the air after the $n^\text{th}$ rebound given above. We also know the ratio of time interval between successive rebounds so that we may write:

$$T=t_0+t_1\sum_{n=1}^N(1-\alpha)^{\frac{n-1}{2}}~,$$

$$T=\sqrt{\frac{2h_0}{g}}+2\sqrt{\frac{2h_0}{g}}\sum_{n=1}^N(1-\alpha)^{\frac{n}{2}}~.$$

The series can be summed (as a geometrical progression) to obtain

$$T=\sqrt{\frac{2h_0}{g}}+2\sqrt{\frac{2h_0}{g}}\frac{(1-\alpha)^{1/2}-(1-\alpha)^{(N+1)/2}}{1-(1-\alpha)^{1/2}}~.$$

What is interesting about this expression, is that it converges to a finite number for $N\rightarrow+\infty$. From this, it is not difficult to obtain that the ratio of the time intervals after and before the first rebound is:

$$r=2\frac{(1-\alpha)^{\frac{1}{2}}}{1-(1-\alpha)^{\frac{1}{2}}}~.$$

This expression is easy to invert to obtain the absoprtion coefficient

$$\alpha=1-\frac{r^2}{(2+r)^2}~.$$

But hang on. In deriving the above, we have made the assumption that the number of rebounds goes to infinity $N\rightarrow+\infty$ yet the total time $T$ is finite. Does the ball *actually* performs an infinite number of rebounds? And how is it possible for it to do so in a finite amount of time?

Well, first of all, one must not forget that we are dealing here only with a *very* simplified model. In reality, there are a number of complications arrising. For a start, the amount of energy dissipated at each rebound is likely to depend on the velocity of the ball as it hits the ground, and so on.

Nevertheless, there is no contradiction in an infinite number of rebounds happening in a finite time. The paradox exists only in apparence and is similar to the more familar **Zeno paradox**. What happens is that, after each rebound, the ball spends less and less time in the air and, in fact, goes to zero as the number of rebound increases. At the end of the day, the two limits balance each other and the time remains finite.

More about Zeno paradox in a next post.
