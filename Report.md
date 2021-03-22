---
puppeteer:
  landscape: false
  format: "A4"
  timeout: 500 # <= Special config, which means waitFor 3000 ms
  export_on_save:
    puppeteer: true # export PDF on save
    puppeteer: ["pdf"] # export PDF and PNG files on save
---
<center>

# Report

邱紹庭
r07945001@ntu.edu.tw

</center>


## Problem 1

### 1. (5pt)

- loop 執行次數大約為 $n$ 次, 為線性關係, 故複雜度為 $O(n)$

### 2. (5pt)

- 執行次數大約為 $log_{2}(n) - 1$ (例如 $8=2^3=2\times \underbrace{2\times 2}_{2次}$). 因此複雜度為 $O(log(n))$ 

### 3. (10pt)

Time complexity of recurive functions [^master]

$$
\begin{align}
  T(n) &= 4T(n-1) \\
  T(n) &= 4 (4 T(n-2)) \\
  T(n) &= 4^{n-c} 3T(c-1) \\
  T(n) &= 4^{n-c} 3^c  \\
  T(n) &= O(4^n)_{\#}
\end{align}
$$


### 4. (10pt)

Becsue $f(n)$ and $g(n)$ are positively define for $n$ as a positive integer:

$$ 0 \leq max(f(n) + g(n)) \leq  f(n) + g(n) \leq 2\cdot max(f(n) + g(n))$$

for any $n\geq 1$.

We can find a $c_1\geq2$, such that fullfill the inequality:

   $$f(n) + g(n) \leq c_1 max(f(n)+g(n))$$

And also a $c_2 \leq 1$, satisfies

$$c_2 max(f(n)+ g(n)) \leq f(n) + g(n)$$

for all $n\geq 1$. Therefore, the euqlity holds by applying the definition of $\Theta(n)$ [^ITA_theta]



### 5. (10pt)

Because $f(n) = O(i(n))$ and $g(n) = O(j(n))$, there exist two integers $n_1$, $n_2$ and two constants $c_1$, $c_2$ that satisfy the inequalities:

<center>

$f(n) \leq c_1 i(n_1)$ and $g(n) \leq c_2 j(n_2)$

</center>


Let $n_0 = max(n_1, n_2)$ and  $c_0 = c_1c_2$. Consider the equation $f(n)\cdot g(n)$:

$$f(n) \cdot g(n) \leq c_1 i(n) \cdot c_2 j(n) \leq c_0 i(n)j(n)$$ 

for all $n\geq n_0$. Thus $f(n)\cdot g(n) \leq O(i(n)\cdot j(n))_{\#}$ [^prop_o].

### 6. (10pt)

The statement is **false**. Here is a contradictory  example:

Let $f(n) = 2 \log_{2} n$ ; $g(n) = \log_{2} n$. This example satisfy the condition, $f(n) = O(g(n))$. However, when apply this example in the power of 2. We can find that $2^{f(n)} = 2^{ 2 \log_{2} n} = n^2$, and $2^{g(n)} = n$[^log]. Therefore, in this case, $2^{f(n)} \notin O(2^{g(n)})_{\#}$.

### 7. (10pt)






## Code

### H3
#### H4
##### H5
###### H6


```c  {.line-numbers}
int a;
```

## Citation


Something important 

## Equations

$$
\begin{align}
 \lim_{n\rightarrow\infty} \frac{f}{g} &= 0 \\
 &= 3
\end{align}
$$


[^master]: Time complexity of recursive functions [Master theorem]. https://yourbasic.org/algorithms/time-complexity-recursive-functions/
[^ITA_theta]: Cormen, T. H., Leiserson, C. E., Rivest, R. L., & Stein, C. (n.d.). Introduction to Algorithms, Third Edition. pp.44-47
[^prop_o]: Properties of Big-O. Data Structures and Algorithms with Object-Oriented Design Patterns in Java. [[Link](https://book.huihoo.com/data-structures-and-algorithms-with-object-oriented-design-patterns-in-java/html/page62.html)]
[^log]: $b^{\log_b p} = p$. see [log equalities](https://ducdoan.com/wp-content/uploads/2018/12/2.jpg).