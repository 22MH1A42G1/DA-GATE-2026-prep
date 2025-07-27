
# Can we do better ?

- we scanfrom 1 to m to compute fm and again from 1 to n to compute fn
- why not a single scan from 1 to max(m,n)?
- for each i in 1 max(m,n), add i to fm if i divids m and add i to fn if i divides n.

Even better ?

why compute two lists and then compare common factors cf? do it in one one shot.

- for each i in 1 to max(m,n), if i divides n, then add i to cf

Actually , any common factor must br less thn min(m,n)

- for each i in 1 min(m,n), if i divides m and i also divides n, then add i to cf

------
```
def gcd(m,n):
    cf = []
    for i in range(1,min(m,n)+1):
        if (m%i) ==0 and (n%i)==0:
            cf.append(i)
    return cf[-1]
```
---------

Do we need lists at all ?

we only need the largest common factor

- 1 will always be a common factor
- each time we find a larger common factor common factor, discard the previous one
- remember the largest common factor seen so far and return it
- mrcf - most recent common factor
----
```
def gcd(m,n):
    mrcf = 0
    for i in range(1, min(m,n)+1):
        if (m%i)==0 and (n%i)==0:
            mrcf = i
    return mrcf
```
-----

Scan backwards?

- to finds the largest common facor , start at the end and work backwards
- let i run from min(m,n) to 1
- first common factor that we find will be gcd!

-----
```
def gcd(m,n):
    i = min(m,n)
    while i>0:
        if (m%i)==0 and (n%i)==0:
            return i
        else:
            i = i-1
```
----
A new kind of repetition

while condition:
step 1
step 2
.. .
step k

Don't know in advance how many times we will repeat the steps
Should be careful to ensure the loop terminates - eventually the condition should become false!

Summary

with a little thought, we have dramatically simplified our naive algorithm

Though the newer versions are simpler, they still take time proportional to the values m and n

A much more efficient approach is possible

Absolutely! Your progression demonstrates excellent algorithmic refinement. Let’s summarize and structure these improvements for your Markdown notes, following your previous format.

# Optimizing the GCD Algorithm

In the previous naive algorithm, we used lists to first store and then compare all factors, which is both space and time inefficient. Below, we detail several **improvements** leading to a dramatically simpler and more efficient approach.

## Can We Do Better?

- The naive approach scans from `1` to `m` to compute factors of `m` (`fm`), and separately from `1` to `n` for `fn`.
- **Improvement idea:** One scan from `1` to `max(m, n)`; for each `i`, add to `fm` or `fn` if `i` divides `m` or `n` respectively.


## Even Better?

- Why compute two lists (`fm`, `fn`) and then a list of common factors (`cf`)?
Directly, for each `i` in `1` to `max(m, n)`, if `i` divides both `m` and `n`, add `i` to `cf`.
- **Insight:** Any common factor must be less than or equal to `min(m, n)`.
So, loop through `1` to `min(m, n)`.


### Example Code

```python
def gcd(m, n):
    cf = []
    for i in range(1, min(m, n)+1):
        if (m % i) == 0 and (n % i) == 0:
            cf.append(i)
    return cf[-1]
```


## Do We Need Lists at All?

- Actually, we only want the **largest common factor**.
- Keep updating a single variable (say, `mrcf` for "most recent common factor") as we find new common factors.


### Improved Code

```python
def gcd(m, n):
    for i in range(1, min(m, n)+1):
        if (m % i) == 0 and (n % i) == 0:
            mrcf = i
    return mrcf
```


## Scan Backwards

- To find the **largest common factor faster**, start at `min(m, n)` and scan backward.
- First factor found that divides both is the GCD!
- Immediate exit from the loop upon finding the answer.


### Efficient Code

```python
def gcd(m, n):
    i = min(m, n)
    while i > 0:
        if (m % i) == 0 and (n % i) == 0:
            return i
        else:
            i = i - 1
```


## A New Kind of Repetition: The While Loop

- The `while` pattern repeats steps as long as some condition holds.
- Used when we don't know in advance exactly how many times to repeat.
- **Caution:** Ensure the loop will eventually terminate!


## Summary of Improvements

- Through step-by-step reasoning, the naive algorithm is **dramatically simplified**.
- Each version reduces unnecessary computation and memory usage.
- The final backward scan is a significant time optimization, especially for large numbers.
- **Note:** Even these versions take time proportional to `min(m, n)`. Faster algorithms are possible... for example, [Euclid's algorithm](https://en.wikipedia.org/wiki/Euclidean_algorithm).

> “With a little thought, we have dramatically improved our naive algorithm, but even simpler, faster methods exist.”

Let me know if you’d like to add the next step with Euclid’s algorithm or further markdown refinements!

