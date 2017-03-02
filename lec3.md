#  Lec3

## ——Divide and Conquer(分治法)

### 分治法思想:

1. Divide the problem into one or more subproblems
2. Comquer each subproblem recursively
3. Combine solutions

### 算法实例

#### Merge Sort(归并排序)

T(n) = 2T(n/2) + O(n) = O(nlg(n))

...

#### Binary Search(二分查找)

T(n) = T(n/2) + O(1) = O(lg(n))

...

#### Powering a number(幂运算)

T(n) = T(n/2) + O(1)

> 需要考虑上下界情况：
>
> x^n  = x^(n/2) * x^(n/2), if n is even
>
> else = x^((n-1)/2) * x^((n-1)/2) * x, if n is odd

...

#### Fibonacci numbers求斐波那契数列第N项) 

Fibonacci(n) = 0, if n = 0

​                       = 1, if n = 1

​                       = Fibonacci(n-1) + Fibonacci(n-2), if n >= 2

##### Solution1:

Naive recursive alg(递归处理):

Time = $\Omega \left ( \varphi ^{n} \right )$(指数级), $\varphi = \frac{1+\sqrt{5}}{2}$(黄金比例)

##### Solution2:

Bottom-up alg(自下而上方法):

计算$F_{1}, F_{2},...F_{n-2},F_{n-1},->F_{n}$

自下而上，利用缓存，可以消除重复计算

Time = O(n)

##### Solution3:

Naive recursive squaring(平方递归)

用到一个数学特性：

> $F_{n}= \frac{\varphi ^{n}}{\sqrt{5}} $最接近的整数

因此理论上，Time可以为O(log(n))

但实际上不可行，因为1.计算机存储浮点数会产生误差，得不到正确的值2.计算机处理浮点数的乘法用的时间大于O(1)?

##### Solution4:

Real recursive squaring(真·平方递归)

用到一个数学特性：

> $$
> \begin{vmatrix}
> F_{n} & F_{n-1}\\ 
> F_{n-1} & F_{n-2} 
> \end{vmatrix}= \begin{vmatrix}
> 1 & 1\\ 
> 1 & 0
> \end{vmatrix}^{n}
> $$
>

可以用归纳法证明。

Time = O(log(n))

#### Matrix multiplication(矩阵相乘)

**问题定义**：A * B = C， A,B,C都为n\*n的矩阵

##### Solution1:

Standard alg:

T(n) = O(n^3)

##### Solution2:

矩阵分块

> 把n\*n的矩阵分成4个n/2\*n/2的子矩阵
>
> A分为abcd，B分为efgh，C分为rstu
>
> 则，分别计算rstu即可：
>
> > r = ae + bg
> >
> > s = af + bh
> >
> > t = ce + dg
> >
> > u = cf + dh
>
> 因此，n阶矩阵相乘转换为8个n/2阶矩阵相乘和4个n/2阶矩阵相加

T(n) = 8T(n/2) + O(n^2) = O(n^3)

可以看出搞了这么半天结果跟Solution1复杂度一样，弃之。

##### Solution3:

真·矩阵分块

> Solution2虽然没有实际作用，但给我们提供了一个思路。在此思路上做优化，减少子矩阵做乘法的次数。
>
> 算法：
>
> 依然先分块
>
> 计算:
>
> > P1 = a(f-h)
> >
> > P2 = (a+b)h
> >
> > P3 = (c+d)e
> >
> > P4 = d(g-e)
> >
> > P5 = (a+d)(e+h)
> >
> > P6 = (b-d)(g+h)
> >
> > P7 = (a-c) (e+f)
>
> 则：
>
> > r = P5 + P4 - P2 + P6
> >
> > s = P1 + P2
> >
> > t = P3 + P4
> >
> > u = P5+ P1 - P3 - P7

相比与Solution2，改进之后乘法减少为7次，

T(n) = 7T(n/2) + O(n^2) = $n^{lg^{7}}\approx n^{2.81}$ 

#### Complete binary tree on VLSI(完全二叉树在超大规模集成电路上的布局最小化)

eh...图不好画。。算了