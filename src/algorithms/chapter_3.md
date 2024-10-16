# Dynamic Programming

## Standard Setup for a Dynamic Programming Problem

A dynamic programming problem will have the solutions to subproblem overlap
i.e. if a problem can be solved by backtracking, but we have repeated work
there's something you can cache, this caching is what leads to a dynamic
programming solution.

A famous example is the fibonacci numbers, the fibonacci numbers is defined recursively

```c++
int fib(int n) {
    if (n < = 1)
        return n;
    return fib(n - 1) + fib(n - 2);
}
```

notice how this produces a binary tree where we're constantly re computing the
subtrees after computing it the first time, i.e. say we want to find `fib(5)`
when solving `fib(5)` must compute `fib(4)` as well as `fib(3)` and `fib(4)`
must also compute `fib(3)` why are we recomputing `fib(3)` so we cache the
solution to `fib(3)` because it's repeated.

## 0/1 Knapsack

Sometimes we need to track more pieces of information we call a bit of
information we need to track state, or dimension.