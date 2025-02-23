# Code and Erratum for *Growth problems in diagram categories*

I collected a bit of Mathematica code relevant for the paper *Growth problems in diagram categories*
<a href="https://arxiv.org/abs/2412.01283">https://arxiv.org/abs/2412.01283</a> on this page.

An Erratum for the paper *Growth problems in diagram categories* can be found at the bottom of the page.

# Contact

If you find any errors in the paper *Growth problems in diagram categories* **please email me**:

[dtubbenhauer@gmail.com](mailto:dtubbenhauer@gmail.com?subject=[GitHub]%web-reps)

Same goes for any errors related to this page.

# Asymptotics using Mathematica

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

# Erratum

Empty so far.
