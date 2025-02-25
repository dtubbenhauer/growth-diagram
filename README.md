# Code and Erratum for *Growth problems in diagram categories*

I collected a bit of Mathematica code and additional details relevant for the paper *Growth problems in diagram categories*
<a href="https://arxiv.org/abs/2412.01283">https://arxiv.org/abs/2412.01283</a> on this page.

An Erratum for the paper *Growth problems in diagram categories* can be found at the bottom of the page.

# Contact

If you find any errors in the paper *Growth problems in diagram categories* **please email me**:

[dtubbenhauer@gmail.com](mailto:dtubbenhauer@gmail.com?subject=[GitHub]%web-reps)

Same goes for any errors related to this page.

# Asymptotics from generating functions

Relevant for the paper is Hayman's method, which on MathSciNet is summarzed by the quote (from Boas, R. P. on MathSciNet):

<div style="text-align: center"><img src="https://github.com/dtubbenhauer/growth-diagram/blob/main/stirling.png" width="800" height="800" style="border: 0px;" /></div>

For the exponential generating function $f(x)=\exp(\frac{k}{2}\exp(2x)+\exp(x)-\frac{k+2}{2})$ satisfies all requirements. One then calculates $g(x)=xf'(x)/f(x)$ 
and $h(x)=xg'(x)$ (which is easy) and performs some algebra on it. All of this can be computer verified with Mathematica code, as explained in <a href="https://arxiv.org/abs/2207.10568">https://arxiv.org/abs/2207.10568</a>.

Note that these are **exact** calculations, so one can put the results into a paper. Arguable, this is better than doing it by hand :relaxed:

# Asymptotics using Mathematica

To quote <a href="https://www.wolfram.com/language/12/asymptotics">https://www.wolfram.com/language/12/asymptotics</a>:

> Asymptotic methods represent a third mode of computing that complements exact symbolic and approximate numeric modes of computing for calculus and algebra. Asymptotic methods are what disciplines turn to when they run into hard problems and are used in a wide variety of areas, including number theory, analysis of algorithms, statistics, theoretical physics and numerical methods. Asymptotic computing allows hard problems to be solved and furthermore is typically more insightful even when other modes of computing succeed. With Version 12, asymptotic computing is fully automated and as easy to use as other high-level solvers.

The corresponding guide is here: <a href="https://reference.wolfram.com/language/guide/Asymptotics.html">https://reference.wolfram.com/language/guide/Asymptotics.html</a>

Note again that these are **exact** calculations, so one can put the results into a paper. Arguable, this is better than doing it by hand :relaxed:

# For the cobordism category

In this case one simply needs to setup the function:

```
(*Define the Lambert W function*)W[x_] := Log[x]

(*Define the value of z*)
z[n_, k_] := 
 W[2 n/k]/2 - 
  1/((4 (k/2) n^(1 - 1/2) (W[2 n/k] + 1) W[2 n/k]^(1/2 - 2)) + 
     2/W[2 n/k] + 1)

(*Define the asymptotic expression for a(n)*)
a[n_, k_] := ((n/z[n, k])^(n + 1/2) Exp[k/2] Exp[2 z[n, k] + 1] Exp[
     z[n, k] - n - (k + 2)/2])/
  Sqrt[2 (k/2) Exp[2 z[n, k]] (2 z[n, k] + 1) + 
    Exp[z[n, k]] (z[n, k] + 1)]
```
Here the Lambert W function is approximated by the logarithm, which is justified by $W(x)=\ln(x)-\ln\ln(x)+o(1)$. Then the rest is easy:

```
Asymptotic[(a[n, 1])^(1/n) // Simplify, n -> Infinity]
```

The code runs for general $k$, but takes a while to evaluate. For fixed $k$ this is very quick.

# Additional details for the calculation in Knop's category

To be done

# Erratum

Empty so far.
