---
title: What growth means
date: 2020-01-03
excerpt: ""
#header:
#  overlay_image: /images/math.jpg
#  overlay_filter: 0.5
use_math: true
---

### in short :



### in details :

A few months ago, I saw [this video](https://www.youtube.com/watch?v=-eljw9qoNAo) of George Monbiot angrily pleading his case against perpetual growth and the lies of so-called "*green capitalism*". At the begining of his demonstration, he explains how the search for a modest rate of 3% growth in our economy leads to a doubling of our production in 24 years. This intervention made me think of a quote by the late professor of physics [Albert Bartlett](https://en.wikipedia.org/wiki/Albert_Allen_Bartlett):

> The greatest shortcoming of the human race is our inability to understand the exponential function.
>
> — Albert Bartlett 

In this post, I will try to contribute to the solution of this problem by providing my own interpretation of the exponential function and its meaning. 

In mathematics, the exponential is the solution to the following problem: 

{: .text-center}

Find the expression of a function **proportional to its rate of growth** 

In mathematics, the rate of growth of a function $$y(t)$$ is equal to its first derivative, so that the above statement translates to:


$$
\begin{equation}
\frac{dy}{dt}=\lambda y(t)~,
\label{eq:dydt}
\end{equation}
$$


where $\lambda$ is some constant of proportionality. Students of mathematics learn to solve the above equation in their first year of University. The result is 


$$
\begin{equation}
y(t)=y(0)~e^{\lambda t}~,
\label{eq:exp}
\end{equation}
$$


where $y(0)$ represents the value of the function at $t=0$. The real number $e\approx2.718$ is a fundamental constant, on par with other numbers like $\pi$. 

The plot below shows the shape of Eq.$(\ref{eq:exp})$ for $y(0)=1$ and for different values of $\lambda$. You can see that this parameter sets the steepness of the curve, the larger the steeper. 

![exponential function](/images/posts_data/exponential/exp.png)

Now, perhaps the main source of confusion comes from the fact that $$\lambda$$ is what economists call the **growth rate** while for mathematician, this name is employed to denote $$\frac{dy}{dt}$$ itself. From Eq.$$(\ref{eq:dydt})$$, we see that $$\lambda$$ is equal to the ratio $$\frac{dy}{dt}/y(t)$$, so that $$\lambda$$ could be more appropriately called the *relative* growth rate. 

Using the above figure, we can understand a number of things. First of all, suppose that the x-axis represents time measured in years and that the y-axis represents the GDP of a country. By looking at the green curve, we can see that is checks out with George Monbiot's computation predicting a doubling of the economy every 24 years for a relative growth rate of 3%. In order to get the exact result, we can go back to Eq.$(\ref{eq:exp})$, pose $y(t_2)=2y(0)$ and solve for $t_2$. This gives:


$$
\begin{align}
e^{\lambda t_2}&=2\nonumber\\
t_2&=\frac{\text{ln}~2}{\lambda}
\end{align}
$$


which, for $\lambda=0.03$, gives $t_2\sim23.105$. The quantity $t_2$ is called the *half-time* constant from its usage in the study of the decay rate of radioactive materials where the exact same mathematics applies, except that the exponential is decreasing, corresponding to a negative value of $\lambda$.

The other thing to learn from the above figure concerns the limits to our intuition in relation to the idea of perpetual growth. 

Eq.($\ref{eq:dydt}$) expresses clearly the origin of the error. The thing is that, although the growth rate 