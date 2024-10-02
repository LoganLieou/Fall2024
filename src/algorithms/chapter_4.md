# String Fundamentals

This is my notes off the notes taken in
[cp-algorithms](https://cp-algorithms.com/string/string-hashing.html) extracting
only the parts I find useful for my understanding then I will work some example
problems

## Hashing

Typically will use a rolling polynomial hash defined roughly as 
$\sum_i^{n-1} s_i \cdot{} p^i$ mod $m$ where $p$ and $m$ are some chosen values
which effect how likely we are to have a *collision*

#### Implementation

```c++
ll hash(const string &s) {
    ll p = 31, m = 1e9+9, pp = 1, h = 0;
    for (char c : s) {
        h = (h + (c - 'a' + 1) * pp) % m;
        pp = (pp * p) % m;
    }
    return h;
}
```

we can additionally use a prefix hash in order to quickly compute in $O(1)$ the
substring hash of `s` i.e. `prefix_hash[j] - prefix_hash[i-1]` gives us the hash
of substring of `s[i:j] `

#### Improving Collision Probability

To improve the probability that we will not have a collision just choose a
different `m` and `p` for a different hash and run the string through both
hashes such that when comparing some string we have to have 
`h1(s) == h2(t) && h2(s) == h2(t)`

## Rabin Karp

In essence we're trying to see if `t` is in `s` the way we do this is by
computing the prefix hash of s and the hash of t then matching t with prefix of
length t in s and checking if the hash is equal until we either find or don't
`t` in `s`

## Knuth Morris Pratt

TODO

## Z-Function

Say we have a string `s` we want to match for index `i` in `s` the longest
prefix match for the suffix starting from `s`

#### Trivial Implementation
```c++
vector<int> z(n, 0);
for (int i = 1; i < n; ++i) {
    while (i + z[i] < n && s[z[i]] == s[z[i] + i])
        ++z[i];
}
```

#### Improved Implementation

We can improve the previous implementation which essentially just does as the
algorithm says by reusing our work, i.e. not starting from zero we want to check
if we are inside of a prefix we've already matched so we keep track of the left
and right side of this window, and if `i < r` then we're inside of the
precipitation thus we should use the result from this to help start our
computation at `z[i]` (do note on average this will improve our algorithm to
$O(n)$ instead of $O(n^2)$ although this proof is not very intuitive)

```c++
vector<int> z(n, 0);
int l = 0, r = 0;
for (int i = 1; i < n; ++i) {
    if (i < r)
        z[i] = min(r - i, z[i - l]); // I don't really understand this
    while (z[i] + i < n && s[z[i]] == s[z[i] + i])
        ++z[i];
    if (z[i] + i > r) {
        r = z[i] + i;
        l = i;
    }
}
```

#### Using the Z-Function to Find Pattern

In order to find occurrences of `p` in `s` we can formulate a string `t` where
`t` concatenates `p` and `s` with a character which is not in `p` or `s` then we
run the z-function on this string if there's a match a value `z[i]` will we
equal to the length of `p` on the right hand side of the string.

#### String Compression TODO: Explain the Algorithm

Want to find the smallest string `p` such that repeating `p` can produce `s` for
example if you have a string `aaa` the smallest such string is `a` of length 1.

## Suffix Array