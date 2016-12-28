---
layout: post
title: First note
tags: codes
---

It is my personal website for research infos or notes.

Here should be equations and codes. Lets do some tests:

$$
\frac{\partial f}{\partial \bar{z}} = \mu \frac{\partial f}{\partial z}
$$

$$
\begin{aligned}
\begin{pmatrix}
I & O \\
O & I
\end{pmatrix}
+
\begin{pmatrix}
V & O \\
O & U
\end{pmatrix}
\begin{pmatrix}
D & O \\
O & D
\end{pmatrix}
\begin{pmatrix}
O & U^T \\
V^T & O
\end{pmatrix}
& = 
\begin{pmatrix}
I & O \\
O & I
\end{pmatrix}
+
\begin{pmatrix}
V & O \\
O & U
\end{pmatrix}
\begin{pmatrix}
O & DU^T \\
DV^T & O
\end{pmatrix}
\\
& = 
\begin{pmatrix}
I & O \\
O & I
\end{pmatrix}
+
\begin{pmatrix}
O & VDU^T \\
UDV^T & O
\end{pmatrix}
\\
& = 
\begin{pmatrix}
I & VDU^T \\
UDV^T & I
\end{pmatrix}
\end{aligned}
$$

```julia
type Point{T}
  x::T
  y::T
end
```

```R
plus <- function(x) {
    x + 1
}
```

## What I learnt from the above tests

* The markdown engin `kramdown` has a better $\LaTeX$ support than `redcarpet`.
* `kramdown` does not work with the syntax highlighter `pygments` which supports most programming languauges, for example, **Julia**.
* `rouge` is the choice next to `pygments`. According to the `rouge` development repository on GitHub, `rouge` was updated to support **Julia** on **Nov 17, 2015**. However, the latest release of `rouge` today (May 16, 2016), version 1.10.1, includes updates only up to **Sep 10, 2015**. So, there is no **Julia** syntax highlight if the `rouge` on my computer is just the release version 1.10.1. 
* So, to get the **Julia** syntax highlight works, I have to install the latest development verson of `rouge` from its GitHub repository.

