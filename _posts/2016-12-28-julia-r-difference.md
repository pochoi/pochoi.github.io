---
layout: post
title: A little difference between Julia and R
tags: codes
---

## Julia

```julia
julia> a = [1,2,3,4,5]
5-element Array{Int64,1}:
 1
 2
 3
 4
 5

julia> a[1:2][1] = 1219
1219

julia> a
5-element Array{Int64,1}:
 1
 2
 3
 4
 5
```

## R

```r
> a = c(1,2,3,4,5)
> a[1:2][1] = 1219
> a
[1] 1219    2    3    4    5
```

## Why

In Julia, the expression `a[1:2]` creates an array independent from `a`. Therefore `a[1:2][1]` is not the same reference to `a[1]`. On the other hand, we got what we "expect" in R.

Can we have something like `a[1:2][1]` in Julia? Yes, but in a slightly different way. There is a type `SubArray` for this purpose.

```julia
julia> sub(a, 1:2)[1] = 1219
1219

julia> a
5-element Array{Int64,1}:
 1219
    2
    3
    4
    5
```

`sub(a, 1:2)` creates a object of type `SubArray`. The index assignment syntax `[] = ` (i.e. `setindex!`) for `SubArray` , will pull out the corresponding reference of the original array `a`.

[SubArray in Julia manual v5](http://docs.julialang.org/en/release-0.5/devdocs/subarrays/)
