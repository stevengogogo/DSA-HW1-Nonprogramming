---
puppeteer:
  landscape: false
  format: "A4"
  timeout: 500 # <= Special config, which means waitFor 3000 ms
  export_on_save:
    puppeteer: true # export PDF on save
    puppeteer: ["pdf"] # export PDF and PNG files on save
---


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

### 7. (10pt) The harmonic series

Strategy: **Approximation by Integrals** [^ITA_1154]

Let $f(k) = \frac{1}{k}$, which is a **monotonically decreasing function**. We can find the bounds

$$\int_{m}^{n+1} f(x)dx \leq \sum_{k=m}^{n} \frac{1}{k} \leq \int_{m-1}^{n} f(x) dx$$

For a **lower bound**,

$$\sum_{k=1}^{n} \frac{1}{k} \geq \sum^{n+1}_{1} \frac{1}{x} dx = \ln(n+1)$$

For an **upper bound**,


$$ \begin{align*} 
\sum_{k=2}^{n} \frac{1}{k} + 1 & \leq \int_{1}^{n} \frac{1}{x} dx + 1\\
                   & = \ln(n) + 1
\end{align*}$$

In summary,

$$\ln(n+1) \leq \sum_{k=1}^{n} \frac{1}{k} \leq \ln(n)+1$$

We need to find constants $c_1$ and $c_2$ that can include bounds by multply with $\ln(n)$.

- Lower bound:  $\ln(n+1) > 1 \cdot ln(n)$
  - where $c_1 = 1$ for $n \geq 1$
- Upper bound: $\ln(n) + 1 = \ln(e\cdot n) < 2\cdot \ln(n)$
  - where $c_2 = 2$ for  $n > e$

Therefore,

$$0\leq \ln(n) \leq \sum_{k=1}^{n} \frac{1}{k} \leq 2\ln(n)$$

for all $n>e$. By $\Theta$ notatoin: $\sum^{n}_{k=1} \frac{1}{k} = \Theta(\ln n) = \Theta(\frac{\log n}{\log e}) = \Theta(\log n)_{\#}$



### 8. (10pts) $\log(n!) = \Theta(n\log n)$

The equation can be expanded

$$\log(n!) = \log(n) + \log(n-1) + \cdots + \log(1)$$

We can find the upper bound by setting all the terms as $\log(n)$, and get

$$\log(n!) \leq n\log(n)$$

On the other hand, $\log(n!)$ can be expanded 

$$\log(n!) = \log(n * (n-1) * (n-1) * \cdots * 1) $$

By removing half of elements,

$$\begin{align*}
  \log(n!) &\geq \log(n*(n-1)*\cdots*(\frac{n}{2})) \\
           &\geq \log((\frac{n}{2})^{\frac{n}{2}}) = \frac{n}{2} \log(\frac{n}{2})
\end{align*}$$

The relation between $n\log(n)$ and $\frac{n}{2} \log(\frac{n}{2})$ can be further explained

$$\frac{n}{2}\log(\frac{n}{2}) = \frac{n}{2}(\log(n) - 1)$$

We need to find a $c$ that fullfills the following inequality:

$$c\cdot n\log(n) \leq \frac{n}{2}\log(\frac{n}{2}) $$


For $n\geq 4$ [^log],

$$\begin{align*}
  \log n &\geq 2 \\
  \frac{1}{4} \log n   &\geq  \frac{1}{2} \\
  \frac{1}{4} \log n - \frac{1}{2} &\geq 0 \\
  \frac{1}{4} n \log n - \frac{1}{2} n &\geq 0 
\end{align*}$$ 

Add $\frac{1}{4}n\log n$ on both sides:

$$\frac{1}{2} n\log n - \frac{1}{2}n \geq \frac{1}{4} n\log n$$

Recall the lower bound

$$ \begin{align*}
  \log(n!) &\geq \frac{n}{2} \log(\frac{n}{2}) \\
           &\geq \frac{1}{4} n\log n
\end{align*}$$

for all $n\geq 4$.

In conclusion,


$$0\leq \frac{1}{4}n\log(n) \leq \log(n!) \leq n\log(n)$$

for all $n\geq 4$. The $\Theta(n!) = n\log(n)_{\#}$


## 9. (10pts)

令 $g(n) = n\log n$.
每一個 $f(n)$ 都會產生 $2$ 個 $f(n-1)$. 直到  $\lfloor \frac{n}{2} \rfloor = 1$ 總計會產生 $n^{\log_2 2}$ 個 $\Theta(1)$ operations 在 leaves. 在分支的過程中, 會產生 $\sum_{j=0}^{\log_2 n - 1} 2^j g(\frac{n}{2^j})$ 個 operation 在 roots[^master_tree]. 所以可以得到以下關係

$$f(n) = \underbrace{\Theta(n^{\log_2 2})}_{Leaves} + \underbrace{\sum_{j=0}^{\lfloor \log_2 n - 1 \rfloor} 2^j g(\frac{n}{2^j})}_{Roots}$$


已知 $g(n) = \Theta(n\log n)$, 接下來比較 $2 g(\frac{n}{2})$ 和 $g(n)$ 的 complexity:


$$\begin{align*}
  2 g(\frac{n}{2}) &= 2 \cdot \frac{n}{2} \cdot \log(\frac{n}{2}) \\
                   &= n \cdot \log(\frac{n}{2}) \\
                   &= n \cdot (\log(n) - 1) \\
                   &< \underbrace{n\cdot \log(n)}_{=g(n)}
\end{align*}$$ 

for all $n>2$, 可以找到 $c<1$ 滿足 $2 g(\frac{n}{2}) < c\cdot g(n)$ 

另外下界可以用,

$$\begin{align*}
  2g(\frac{n}{2}) = log(\frac{n^n}{2}) & \geq log(n^{n/2}) \\
                                       & = \frac{1}{2} n\cdot \log(n)
\end{align*}$$ 

for $n\geq 4$. Furthermore, $\lim_{n\rightarrow \infty} \frac{log(n^n/2)}{log(n^{n/2})} = 2$ [^xpx]. Therefore, $2g(\frac{n}{2}) = \Theta(g(n))$

因此可以得到 roots 的 complexity,

$$\begin{align*}
\underbrace{\sum_{j=0}^{\lfloor \log_2 n - 1 \rfloor} 2^j g(\frac{n}{2^j})}_{Roots} &\leq \sum_{j=0}^{\lfloor \log_2 n - 1 \rfloor} c^j g(n) + O(1) \\
&\leq  g(n) \sum^{\lfloor \log_2 n - 1 \rfloor}_{j=0} c^j + O(1)\\
&= g(n) (\frac{1\cdot(1-c^{\lfloor \log_2 n - 1 \rfloor})}{1-c}) + O(1) \\
&= O(g(n))
\end{align*}$$

for $n>2$ and $c<1$. On the other hand, we can also find a lower bound by letting $c<\frac{1}{2}$ and $n>4$. Therefore

$$\underbrace{\sum_{j=0}^{\lfloor \log_2 n - 1 \rfloor} 2^j g(\frac{n}{2^j})}_{Roots} = \Theta(g(n))$$

Finally we get,

$$\begin{align*}
f(n) &= \Theta(n) + \Theta(n\log n) \\
     &= \Theta(n(\log(n))_{\#}
\end{align*}$$


10. (Bonus 10pts) 





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
[^ITA_theta]: Cormen, T. H., Leiserson, C. E., Rivest, R. L., & Stein, C. (n.d.). Introduction to Algorithms, Third Edition. **pp.44-47**
[^prop_o]: Properties of Big-O. Data Structures and Algorithms with Object-Oriented Design Patterns in Java. [[Link](https://book.huihoo.com/data-structures-and-algorithms-with-object-oriented-design-patterns-in-java/html/page62.html)]
[^log]: $b^{\log_b p} = p$. see [log equalities](https://ducdoan.com/wp-content/uploads/2018/12/2.jpg).
[^ITA_1154]:  Introduction to Algorithms, Third Edition. **pp.1154-1156**.
[^log]: How to prove $\log n! = \Theta(n\log n)$. [[tutorial](http://www.mcs.sdsmt.edu/ecorwin/cs372/handouts/theta_n_factorial.htm)]
[^master_tree]: Introduction to Algorithms, Third Edition. Chapter 4 Divide-and-Conquer. **pp.104**
[^xpx]: $\lim_{n\rightarrow \infty} \frac{log(n^n/2)}{log(n^{n/2})} = 2$. Becuase both nominator and denominator approach to infinity as $n \rightarrow \infty$. We can use [L'Hospital's Rule](https://en.wikipedia.org/wiki/L%27H%C3%B4pital%27s_rule). $\lim_{n\rightarrow \infty} \frac{log(n^n/2)}{log(n^{n/2})} = \lim_{n\rightarrow \infty} \frac{log(n^n/2)'}{log(n^{n/2})'}$. Later on, $\frac{d \log(n^n/2)}{dn} = \frac{1}{2}\log(n^n)'$[^lhos]; $\frac{d \log(\frac{n^n}{2})}{dn} = \log(n^n)'$ . Therefore, $\lim_{n\rightarrow \infty} \frac{log(n^n/2)}{log(n^{n/2})} = 2$
[^lhos]: $(x^x)' = x^x (\log(x) + 1)$. [[proof](https://jakubmarian.com/derivative-of-xx/)]