##Lecture1
#### Problem Sorting 

##### Insertion Sort

  > for j <- 2 to n
  > ```python
  > do key <- A[j]
  > 	i <- j-1
  > while i > 0 and A[i] > key:
  > 	do A[i+1] <- A[i]
  > 		i = i - 1
  > A[i+1] <- key
  > ```
###### T(n) = Theta n^2

##### Runtime depend:

1. input
2. 规模
3. 上界
4. 最坏情况分析T(n)
5. 平均情况
6. theta 

##### Merge Sort

> 我自己写的伪代码：
> ```python
> MergeSort(A, 1, n)
> 	if n is 1:
> 		done.
> 	l1 <- MergeSort(A, 1, n/2)
> 	l2 <- MergeSort(A, n/2+1, n)
> 	Merge(l1, l2, l)
> ```
>
>
> ```python
> Merge(l1, l2, l)
>     pl1 <- 1, pl2 <- 1, pl <- 1
>     while pl1 < len(l1) and pl2 < len(l2)
>         if l1[pl1] < l2[pl2]
>             l[pl] <- l1[pl1]
>             pl <- pl + 1, pl1 <- pl1 + 1
>         else
>             l[pl] <= l2[pl2]
>             pl <- pl + 1, pl2 <- pl2 + 1
>     while pl1 < len(l1)
>         l[pl] <- l1[pl1]
>         pl <- pl + 1, pl1 <- pl1 + 1
>     while pl2 < len(l2)
>         l[pl] <- l2[pl2]
>         pl <- pl + 1, pl2 <- pl2 + 1
> ```
>
> 下面是老师写的伪代码，简洁清晰，值得我去学习，
> ```python
> MergeSort(A[1, ..., n])
> 	if n = 1, done
> 	Recusively sort A[1, ..., n/2] and A[n/2+1, ..., n]
> 	Merge 2 sorted lists
> ```
######T(n) = Theta n * log(n)