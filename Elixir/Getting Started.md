# Elixir 

## Pattern Matching
The <code>=</code> operator is used as assignment and pattern matching
ex
```elixir
iex> x = 1
1
iex> x
1
iex> 1 = x
1
iex> 2 = x
Match Error
```
It appears that if the variable does not have a value it is assigned if it has a value and is on the *right side* then it pattern matches

A more interesting example is using tuples
```elixir
iex> {a, b, c} = {:hello, "world", 42}
iex> a
:hello
iex> b
"world"
```

Can also do interesting pattern matching with lists
```elixir
iex> [h|t] = [1,2,3,4,5,6,7,8,9]
iex> h
1
iex> t
[2,3,4,5,6,7,8,9]
```

<code>[head | tail]</code> format can also be used to prepend values to a list
```elixir
iex> list = [1,2,3]
[1,2,3]
iex> [0 | list]
[0,1,2,3]
```

## The Pin Operator
<code>^</code> is th pin operator
use this when you want to pattern match against an existing variable rather than rebinding the variable

In other words use <code>^</code> when you want to pattern match the left hand value to the right hand value. It seems that normally pattern matching occurs when a variable is on the right hand side, <code>^</code> lets you have it on the left hand side.
```elixir
iex> x = 1
1
iex> 1 = x
1
#Should be the same as
iex> x = 1
1
iex> ^x = 1
1 #Is not assigned here
iex> ^x = 2
** (Match Error)
```
It can also be applied to a value in a tuple, list and possibly other types as well
```elixir
iex> x = 5
5
iex> [^x, y] = [5, 1]
[5, 1]
#X is pattern matched and y is assigned
```
### Unbound variable
<code>_</code> is a special variable that cannot be read from. Use this if you have a *pattern* that return multiple values (like a list) and you only want the first value or want the everything but the first value
```elixir
iex> [h|_] = [1, 2, 3]
[1, 2, 3]
iex> h
1
iex> _
** (CompileError) iex1: unbound variable _
#This should be reversable as well
iex> [_|t] = [1,2,3]
[1,2,3]
iex> t
[2,3]
```

### Functions
Functions __cannot be called on the left side of a match__

# Program Flow - Logic
In my current studies there is only 4 control flow structures __case__, __cond__, __if__ and __unless__, __do/end__ block</code> 

## case
Can compare a value against many patterns until a match is found
```elixir
iex> case {1, 2, 3} do
...> {4,5,6} ->
...>    "This clause won't match"
...> {1, x, 3} ->
...>    "This clause will match and bind x to 2 in the scope of this clause"
...> _->
...>    "This clause would match and value"
...>end
"this clause will match and bind x to 2 in the scope of this clause"
```
To pattern match an existing variable the <code>^</code> operator must be used
```
iex> x = 1
1
iex> case 10 do
...> ^x -> "Won't match"
...> _ -> "Default (All values match)"
...>end
```
case clauses also can include extra conditions known as __guards__
```elixir
case {1,2,3} do
    {1,x,3} when x > 0 -> "Will match"
    _ -> "Would match, if guard condition is not satisfied"
```
More documentation on [Guards](https://elixir-lang.org/docs/master/elixir/guards.html)

## cond
[TODO](https://elixir-lang.org/getting-started/case-cond-and-if.html#if-and-unless)
## if and unless
[TODO](https://elixir-lang.org/getting-started/case-cond-and-if.html#doend-blocks)



<<<<<<< HEAD
Adding something here
=======








Added this 
>>>>>>> master