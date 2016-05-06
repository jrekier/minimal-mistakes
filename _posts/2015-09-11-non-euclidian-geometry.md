---
title: Non-Euclidian Geometry
header:
  image: nightsky.jpg
use_math: true
---

When I was thaught geometry at school, we used to draw shapes on paper such as squares and triangles. Sometimes, we even considered solids in 3D.

The mathematical description of these is based on a set of base rules (axioms) identified by [Euclid](https://en.wikipedia.org/wiki/Euclid) around 300BC.

Over the past millennia, the study of geometry has been extended a lot and the word is no longer limited to the study of shapes and solids in 2 or 3 dimensions.

One important step toward this generalisation was made by carefully inspecting the axioms of Euclid and investigating what happens when some of them are disregarded.

I want to give an example of what happens when one ditches Euclid's 'unbeloved' 5th axiom.

This axiom can be stated as : *If one takes one line and a point not on the line, there is but one line parallel to the first one that goes through the point.*

The 5th axiom is very important to describe the familiar geometry of the plane and 3 dimensional space. However, it is not suited to more general surfaces. Take, for example, the upper surface of a **two-sheet hyperboloid** drawn in green on the picture below. The **geodesics**, the equivalent of the *straight lines* on this surface are the intersections of the surface and planes passing through the origin of coordinates. Three of these lines are drawn in black, blue and red on the surface.

![alt]({{ site.url }}{{ site.baseurl }}/images/euclid1.png)

Now, even though the blue and red lines intersect in one point, neither of these intersect the black line and thus both can be considered as parallel to it. One can be tempted to argue that what is true for the hyperboloid of the figure which is limited in space but might not be in the whole infinite hyperboloid surface. It turns out that this can be checked very simply by considering a representation of the hyperbolic space due to **Poincaré**. This representation brings every points of the hyperboloid surface within a disk of unit radius and is shown on the figure below.

![alt]({{ site.url }}{{ site.baseurl }}/images/euclid2.png)

As can be seen from the picture, the red and blue lines reach the boundary of the Poincaré disk corresponding to spatial infinity.

The algebraic expression for the Poincaré projection is very simple in terms of polar coordinates. The 3D parametric representation of points on the hyperboloid is

$$
\begin{cases}
x = r\cos\theta \\
y = r\sin\theta \\
z = \sqrt{1+r^2}
\end{cases}~.  
$$

The projection reads
$$
(r,\theta)\rightarrow (\frac{r}{\sqrt{1+r^2}+1},\theta)~.
$$

Geometrically, this corresponds to the intersection of the line intersecting the horizontal plane and joining a point on the hyperboloid with the point of coordinates $$(0,0,-1)$$. This is an example of a **stereographic projection**.

Non-euclidian geometry is a very useful topic of mathematics as it has many applications notably in physics. One of the most important being General Relativity in which space-time is a non-euclidian 4D space, the curvature of which being gravitation.
