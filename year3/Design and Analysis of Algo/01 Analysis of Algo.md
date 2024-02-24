### Analysis
Problem solving capability of the algorithm in terms of the time and size required 

### Worst case
Maximum number of steps taken on any instance of size a. 

### Notations
| Symbol     | Name      | Meaning      |
| ---------- | --------- | ------------ |
| $$O$$      | Big O     | Worst Case   |
| $$\Omega$$ | Big Omega | Average Case |
| $$\theta$$ | Big Theta | Best Case    | 

> A sequence of operations provided to input of size 'a' averaged over time

## Growth of functions
| S.no | O(n)                      | Type        | Usage                 |
| ---- | ------------------------- | ----------- | --------------------- |
| 1    | 1                         | Constant    |                       |
| 2    | $$ \log\left( N \right)$$ | Logistic    | Bin Search            |
| 3    | $$ \sqrt{N} $$            |             | Find Division         |
| 4    | $$ N $$                   | Linear      | Linear Search         |
| 5    | $$ N\log{N} $$            |             |                       |
| 6    | $$ N^2 $$                 | Quadratic   | Matrix addition       |
| 7    | $$ N^3 $$                 | Cubic       | Matrix Multiplication |
| 8    | $$ 2N $$                  | Exponential | Sum of subsets        |
| 9    | $$ N! $$                  | Exponential | Permutations           | 
>[!info] 
> A recurrence is an equation or inequality that describe a function terms of its value on smaller inputs.

Algorithm A and B spend exactly $T_a(n) = 5.log_{10}n$ and $T_n(n) = 25.n$ microseconds repectively, for a problem of size n. Which algorithm is better in the sense of Big-Oh? For which problem size does it outperforms the other? 

Answer:
	$T_b(n) \le T_a(n)$
	$25n \le 5nlog_{10}n$
	$5 \le log_{10}n$