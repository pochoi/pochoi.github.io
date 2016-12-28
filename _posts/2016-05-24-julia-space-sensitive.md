---
layout: post
title: Julia is space sensitive (in some sense)
tags: codes
---

```julia
julia> a = zeros(3)
3-element Array{Float64,1}:
 0.0
 0.0
 0.0

julia> a[2+1]
0.0

julia> a[2 + 1]
0.0

julia> a[2+ 1]
0.0

julia> a[2 +1]
ERROR: MethodError: `typed_hcat` has no method matching typed_hcat(::Array{Float64,1}, ::Int64, ::Int64)
Closest candidates are:
  typed_hcat(::Type{T}, ::Number...)
  typed_hcat(::Type{T}, ::Any...)

julia> a[(2 +1)]
0.0
```
