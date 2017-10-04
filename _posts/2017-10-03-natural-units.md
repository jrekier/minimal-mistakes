---
title: Thinking before calculating
date: 2017-10-03
excerpt: "The best units for a given problem"
header:
  overlay_image: /images/math.jpg
  overlay_filter: 0.5
use_math: true
---

When dealing with equations in physics, checking your units is an excellent way of looking for errors. For example, suppose you were to treat the problem of an object being drop from the top of a cliff. If you assume that the object has initial zero velocity, you end up with:

\begin{equation}
z=h-g\frac{t^2}{2}~,
\end{equation}

where $z$ stands for the height of the object measured from the ground, $h$ that of the cliff, $g$, the gravitational acceleration and $t$ the time elapsed since the drop. A quick check of dimensions will tell you that all three terms have units of length, as they should. Your equation is therefore consistent from a dimensional point of view. This does not necessarily mean that it is correct but if you had found that the units were inconsistent, then you would have been absolutely sure that it is not.

The constant $g$ has a particular status among the symbols of the above expression. It can be thought of as a *conversion factor* transforming time scales squared to length scales. Knowing the dimensions of this factor is essential in using the trick described above.

Sometimes, however, having to drag conversion factors around is the dominant source of errors. There is, however, a neat trick to get rid of such factors. I will illustrate this for the problem of finding the energy levels of a quantum particle trapped in a 1-dimensional box.

The problem consists in solving the Schrödinger equation
\begin{equation}
-\frac{\hbar^2}{2\mu}\frac{d^2\psi}{dx^2}=E\psi~,
\end{equation}
subjected to boundary conditions $\psi(x=0)=\psi(x=l)=0$, with $l$ being the length of the box, $\mu$, the mass of the particle and $E$, its energy.

We start by identifying the fundamental independent dimensions of the problem. Very often, these consists only in *mass* (M), *length* (L) and *time* (T). Occasionally one might want to add a scale of electric charge or temperature. The *dimensional analysis* version of the above equation gives you
\begin{equation}
\frac{[\hbar^2]}{M L^2}=[E]~.
\end{equation}
where a symbol inclosed within square brackets denotes its dimensions regardless of its numerical value. In order to identify the dimensions of E in terms of our fundamental dimensions of mass, length and time, it is best to use a mnemonic equation. The obvious candidate here is $E=mc^2$ which tells us that $[E]=M L^2T^{-2}$, from which we can obtain
\begin{equation}
[\hbar]=L^2MT^{-1}~.
\label{eq:hbar}
\end{equation}

Next, we identify the natural physical scales of the problem which we will call $L_S$,$M_S$ and $M_S$. Having found these, we will then use them to measure all our masses $m$, lengths $d$ and times $t$ so that
\begin{align}
m&\rightarrow m~M_S\nonumber\\\\\\
d&\rightarrow d~L_S\nonumber\\\\\\
t&\rightarrow t~T_S~,\nonumber
\end{align}
with the symbols $m$, $t$ and $d$ on the right now being dimensionless.
Going back to our problem, it is straightforward enough to identify $M_S=\mu$ and $L_S=l$. From, Eq.\ref{eq:hbar}, we then see that the only natural time scale to choose is
\begin{equation}
T_S=\frac{l^2 \mu^2}{\hbar}~.
\end{equation}

Now comes the clever bit. Once these scales have been defined, we **set the numerical value of each to $1$**. This amounts to a simple choice of units. For example, setting $M_S=\mu=1$ means that all masses will now be measured as multiples of $\mu$. This might seem innocent enough but it should, however, be easy enough to work out that, in this set of units, the original equation now turns into its simplified *dimensionless form*:
\begin{equation}
-\frac{1}{2}\frac{d^2\psi}{dx^2}=E\psi~,
\label{eq:shrodingerdimless}
\end{equation}
with $E$ now being measured in units of $E_s=M_S L_S^2 T_S^{-2}=1$. It seems, perhaps, astonishing that we are still able to say anything about our problem when so many things have already been set to one. It is worth noting, though, that even though our new equation is now considerably more readable than the original, we have lost the possibility to check the steps of any ensuing computation using dimensional analysis. This, however, is arguably a price worth paying.

Now let's get through the resolution. The general solution of the homogeneous form of Eq.\ref{eq:shrodingerdimless} is
\begin{equation}
\psi(x)=A e^{ikx}+B e^{-ikx}~.
\end{equation}
Imposing $\psi(x=0)=0$, gives $A+B=0$, which yields $\psi(x)=A \sin(kx)$ and $\psi(x=1)=0$ (remember that now $l=1$), imposes that
\begin{align}
k=n\pi&&n\in\mathbb{N}~.
\end{align}
Inserting back into the original equation gives the values of the energy levels in a very elegant form
\begin{equation}
E=\frac{n^2\pi^2}{2}~.
\end{equation}
Of course, one might want the numerical values of these energies in a set of units that is more convenient to compare with experiment. To get this, we simply need to multiply our result by the energy scale $E_S$, but now leaving its precise numerical value left to be set by any other choice of units. One has $E_S=\frac{\hbar^2}{l^2\mu}$ so that one finally gets
\begin{equation}
E=\frac{n^2\pi^2}{2}\frac{\hbar^2}{\mu^2 l}~.
\end{equation}
The nice thing about this trick is that it allows you to immediately guess the dependency of the solution on the parameters of your system (here $l$ and $\mu$) without having to carry around their symbols throughout. In fact, without even solving the problem, I could have already told you that the energy levels would be multiples of $\frac{\hbar^2}{\mu^2 l}$ just by doing a bit of dimensional analysis. This might seem like a minor bonus in the present context but is in fact a huge deal in longer and more cluttered computations.
