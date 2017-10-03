---
title: Thinking before calculating
date: 2017-10-03
excerpt: "The best units for a given problem"
header:
  overlay_image: /images/math.jpg
  overlay_filter: 0.5
use_math: true
---

When dealing with equations in physics, checking your units is an excellent way of looking for errors. For example, suppose you were to treat the problem of an object being drop from the top of a cliff. If the object is assumed to have initial zero velocity, you would end up with:

\begin{equation}
z=h-g\frac{t^2}{2}~,
\end{equation}

where $z$ stands for the height of the object measured from the ground, $h$ that of the cliff, $g$, the gravitational acceleration and $t$ the time elapsed since the drop. A quick check of dimensions will tell you that all three terms have units of length, as they should. Your equation is therefore consistent from a dimensional point of view. This does not necessarily mean that it is correct but if you had found that the units were inconsistent, then you would have been absolutely sure that it was not.

The constant $g$ has a particular status among the symbols of the above expression. It can be thought of as a *conversion factor* transforming time scales squared to length scales. Knowing the dimensions of this factor is essential to using the trick described above.

Sometimes, however, having to drag the symbols of conversion factors around is the dominant source of errors.
