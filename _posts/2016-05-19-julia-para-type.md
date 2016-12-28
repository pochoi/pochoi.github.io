---
layout: post
title: Confusing Julia!	 Outer constructor with parametric type
tags: codes
---

I just come across a confusing part when defining a constructor with parametric type.
Lets do a simple example (in Julia v0.4)

```julia
type Hello{T}
	x::T
end
```

I want an outer constructor which makes `x` to be a zero of the type `T`. At the first thought, I do the following:

```julia
Hello{T}() = Hello{T}(zero(T))
```

If the above definition is correct, I expect that:

```julia
julia> a = Hello{Float64}()
Hello{Float64}(0.0)

julia> a.x
0.0

julia> b = Hello{Int64}()
Hello{Int64}(0)

julia> b.x
0
```

However, the above definition will just give you the error:

```
julia> Hello{T}() = Hello{T}(zero(T))
WARNING: static parameter T does not occur in signature for call at none:1.
The method will not be callable.
Hello{T}
```

OMG! What happens?!?! Then I find out this [issue](https://github.com/JuliaLang/julia/issues/11310).

The problem is that Julia treats `Hello{T}() = Hello{T}(zero(T))` as

```julia
call{T}(::Type{Hello}) = Hello{T}(zero(T))
```
Notice it is `Hello` instead of `Hello{T}`. The missing `T` causes the error.

The current solution (in Julia v0.4) is to overload `call` explicitly:

```julia
call{T}(::Type{Hello{T}}) = Hello{T}(zero(T))
```

Hope this problem will be "resolved" in future release.