<img src="https://r2cdn.perplexity.ai/pplx-full-logo-primary-dark%402x.png" class="logo" width="120"/>

# NPTEL Programming, Data Structures and Algorithms using Python

Algorithm: how to systematically perform a task

write down as a sequence of steps

- recipe or program

our focus
-------------

Algorithms that manipulate information

- compute numerical functions
-- f(x,y) = x^y
- Reorganize data
-- arrange in asecending order
- Optimization -- find the shortest route
- And more ...
--  solve Sudoku

Greatest common divisor

- gcd(m,n)
-- largest k such that k divides m and k divides n
-- gcd(8,12) = 4
-- gcd(18,25) = 1
- 1 divides every number
- At least one common divisor in the number

Computing gcd(m,n)

- List out factors of m
- List out factors of n
- Report the largest no that appears on both lists
- is this a valid algorithm
- finite presentation of the recipe.
- terminates after a finite no of steps.
- Factors of m must be between 1 and m
- test each no in this range
- if it divides m without a remainder , and it to list of factors
- ex: gcd(14,63)
factors 14 = { 1, 2, 7, 14}
factors 63 = {1, 3, 7, 21, 63}

constrct list of common factors

- for each of 14 , check if it a factor of 63
factors (14 ^ 63)= {1,7}
return largest factor in this list : 7
--
An Alg for gcd(m,n)
- use fm, fn for list of factors of m,n respectively
- for each i 1 to m, add i to fm if i divides m
- for each j form 1 to n, add j to fn if j divides n
- use cf for list common factors
- for each f in fm, add f to cf if f also appears in fn
- return largest (rightmost) vlaue in cf
------------------------
def gcd(m,n):
fm = []
for i in range(1,m+1):
if (m%i) == 0:
fm.append(i)
fn = []
for j in range(1, n+1):
if (n%j) == 0:
fn.append(j)
cf = []
for f in fm:
if f in fn:
cf.append(f)
return cf[-1]
-----------------------------

Some points to note

- use names to remember interdiate values
- m, n, fm, fn, cf, i, j, f
- Values can be sigle items or collections
- m, n, i, j, f, are single numbers
- fm, n, cf are lists of numbers
- Assign values to names
- Explicitly, fn = [], and implicitly, for f in cf:
- Update them, fn.append(i)
- Program is a sequence of steps
- some steps are repeated
- do the same thing for each item in a list
- some steps are executed conditionally
- do something if a value meets some reqirement

Here are concise study notes based only on your provided content for the topic "NPTEL Programming, Data Structures and Algorithms using Python":

## What is an Algorithm?

- **Algorithm**: A systematic way to perform a task.
    - Written as a sequence of steps, like a recipe or program.


### Our Focus

Algorithms that manipulate information, such as:

- **Computing numerical functions:**
Example: \$ f(x, y) = x^y \$ (exponentiation)
- **Reorganizing data:**
Example: Arrange numbers in ascending order.
- **Optimization:**
Example: Find the shortest route.
- **Other tasks:**
Example: Solve Sudoku.


## Greatest Common Divisor (gcd)

- **Definition:** gcd(m, n) is the largest k such that k divides both m and n.
    - Examples: gcd(8, 12) = 4; gcd(18, 25) = 1
- Note:
    - 1 divides every number, so there is always at least one common divisor.


## Computing gcd(m, n): Factorization Method

1. **List out factors** of m (between 1 and m).
    - Test each number from 1 to m: if m % i == 0, add i to factors of m.
2. **List out factors** of n (between 1 and n).
    - Similarly, test all numbers from 1 to n.
3. **Compare the two lists** and find the largest number in both.

**Example: gcd(14, 63)**

- Factors of 14: {1, 2, 7, 14}
- Factors of 63: {1, 3, 7, 21, 63}
- Common factors: {1, 7}
- **gcd(14, 63) = 7** (largest common factor)


## Algorithm: List-based GCD

1. Use `fm`, `fn` for factors of m, n.
2. For i from 1 to m:
    - If m % i == 0, add i to `fm`
3. For j from 1 to n:
    - If n % j == 0, add j to `fn`
4. Build `cf` for common factors:
    - For every f in `fm`, if f in `fn`, add to `cf`
5. Return the largest value from `cf`

**Python Implementation:**

```python
def gcd(m, n):
    fm = []
    for i in range(1, m + 1):
        if m % i == 0:
            fm.append(i)
    fn = []
    for j in range(1, n + 1):
        if n % j == 0:
            fn.append(j)
    cf = []
    for f in fm:
        if f in fn:
            cf.append(f)
    return cf[-1]
```


## Points to Remember

- **Meaningful names**: Use variables like m, n, fm, fn, cf, i, j, f to hold values.
- **Values types**:
    - Single item variables: m, n, i, j, f.
    - Collections: fm, fn, cf (lists).
- **Assignments**:
    - Explicit: `fn = []` (empty list).
    - Implicit: `for f in cf:` (loop variable).
- **Update values**:
    - `fn.append(i)` adds a value to a list.
- **Program Control**:
    - Steps are executed in sequence.
    - Repetition (loops): Do something for each item in a list.
    - Conditional execution: Do something only if a requirement is met.

These notes summarize the key ideas and steps in approaching algorithms, with a focus on the GCD example, based entirely on your content.

