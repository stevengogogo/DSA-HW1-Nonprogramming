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



## Code

### H3
#### H4
##### H5
###### H6


```c  {.line-numbers}
int a;
```

## Citation


Something important [^1][^3].

## Equations

$$
\begin{align}
 \lim_{n\rightarrow\infty} \frac{f}{g} &= 0 \\
 &= 3
\end{align}
$$


[^master]: Time complexity of recursive functions [Master theorem]. https://yourbasic.org/algorithms/time-complexity-recursive-functions/

[^1]: Citation 1
[^3]: Auto indexing
