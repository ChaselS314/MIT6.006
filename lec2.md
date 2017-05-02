# Lec2

## 计算算法复杂度

### 递归树法

...

### Master Method 主方法

> 对于满足
> $$ 
> T(n) = aT(n/b) + f(n), where,a \geqslant  1, b > 1, f(n) > 0, when, n > n_{0}
> $$
>
> 形式的递归算法(f(n)的约束条件的意思是，当n足够大是保证f(n)为正值)
>
> 比较f(n)和$n^{log_{b^a}}$:
>
> Case1: $f(n) > n^{log_{b^a}}$
>
> > 对于某常数$\varepsilon > 0$，有$f(n) = O(n^{{log_{b}}^{a-\varepsilon }})$，则：
> >
> > $T(n) = O( n^{log_{b^a}})$
>
> Case2: $f(n) = n^{log_{b^a}}$
>
> > 若$f(n) = O(n^{{log_{b}}^{a}})$，则：
> >
> > $T(n) = O( n^{log_{b^a}}\cdot lg^{n})$
>
> Case3: $f(n) < n^{log_{b^a}}$
>
> > 对于某常数$\varepsilon > 0$，有$f(n) = O(n^{{log_{b}}^{a+\varepsilon }})$，则：
> >
> > $T(n) = O( f(n))$
