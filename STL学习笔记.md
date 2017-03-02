# STL学习笔记

## Part I

### Vector

> Vector is the only container that is backward-compatible to native C code – this means that vector actually is the array, but with some additional features.

#### Vector.size()

> size() return unsigned integral type.

#### Vector.empty()

> ```c++
> bool is_nonempty_notgood = (v.size() >= 0); // Try to avoid this,This is because not all the containers can report their size in O(1), although vector could.
> bool is_nonempty_ok = !v.empty(); 
> ```

#### Vector.resize()

> Resizes the container so that it contains *n* elements.
>
> If *n* is smaller than the current container [size](http://www.cplusplus.com/vector::size), the content is reduced to its first *n* elements, removing those beyond (and destroying them).
>
> If *n* is greater than the current container [size](http://www.cplusplus.com/vector::size), the content is expanded by inserting at the end as many elements as needed to reach a size of *n*. If *val* is specified, the new elements are initialized as copies of *val*, otherwise, they are value-initialized.
>

Notice:

> ```c++
>  vector<int> v(20); 
>  for(int i = 0; i < 20; i++) { 
>       v[i] = i+1; 
>  } 
>  v.resize(25); 
>  for(int i = 20; i < 25; i++) { 
>       v.push_back(i*2); // Writes to elements with indices [25..30), not [20..25) ! 
>  } 
> ```

#### Vector.clear()

> This function makes vector to contain 0 elements. It does not make elements zeroes -- watch out -- it completely erases the container.

#### Vector.push_back()

> push data on the end of vector.

#### Vector.pop_back()

#### Vector.insert()

#### Vector.erase()

> The insert/erase technique is common, but **not identical** for all STL containers.

Notice:

> You should remember one more very important thing: When vector is passed as a parameter to some function, a copy of vector is actually created. It may take a lot of time and memory to create new vectors when they are not really needed. Actually, it’s hard to find a task where the copying of vector is REALLY needed when passing it as a parameter. So, you should never write:
>
> > ```c++
> >  void some_function(vector<int> v) { // Never do it unless you’re sure what you do! 
> >       // ... 
> >  } 
> > ```
>
> Instead, use the following construction:
>
> > ```c++
> > void some_function(const vector<int>& v) { // OK 
> >       // ... 
> >  } 
> > ```
>
> If you are going to change the contents of vector in the function, just omit the ‘const’ modifier.

### Pair

STL std::pair is just a pair of elements. The simplest form would be the following:

> ```c++
>  template<typename T1, typename T2> struct pair { 
>       T1 first; 
>       T2 second; 
>  }; 
> ```

### Iterator

Iterator is just like an object with syntax very much like a pointer. The following operations are defined for iterators:

- get value of an iterator, int x = *it;
- increment and decrement iterators it1++, it2–;
- compare iterators by ‘!=’ and by ‘<’
- add an immediate to iterator it += 20; <=> shift 20 elements forward
- get the distance between iterators, int n = it2-it1;

The type of iterator can be constructed by a type of container by appending “::iterator”, “::const_iterator”, “::reverse_iterator” or “::const_reverse_iterator” to it. 

### Algorithms in STL

#### reverse()

> ```c++
> template <class BidirectionalIterator>
>   void reverse (BidirectionalIterator first, BidirectionalIterator last);
> ```

Many STL algorithms are declared in the same way: they get a pair of iterators – the beginning and end of a range – and return an iterator.

#### find()

> ```c++
> template <class InputIterator, class T>
>    InputIterator find (InputIterator first, InputIterator last, const T& val);
> ```

#### max_element() / min_element()

> ```c++
> default (1)	
> template <class ForwardIterator>
>   ForwardIterator max_element (ForwardIterator first, ForwardIterator last);
> custom (2)	
> template <class ForwardIterator, class Compare>
>   ForwardIterator max_element (ForwardIterator first, ForwardIterator last,
>                                Compare comp);
> ```

#### sort()

> ```c++
> default (1)	
> template <class RandomAccessIterator>
>   void sort (RandomAccessIterator first, RandomAccessIterator last);
> custom (2)	
> template <class RandomAccessIterator, class Compare>
>   void sort (RandomAccessIterator first, RandomAccessIterator last, Compare comp);
> ```

#### max()

#### min()

#### swap()

#### next_permutation()

> Don’t forget to ensure that the elements in a container are sorted before your first call to next_permutation(…). Their initial state should form the very first permutation; otherwise, some permutations will not be checked.

#### prev_permutation()

### String

#### string.substr()

> ```c++
> string substr (size_t pos = 0, size_t len = npos) const;
> ```

### Set

#### complex:

> Set can add, remove and check the presence of particular element in O(log N)
>
> A count of the elements in the set, N, is returned in O(1). 

Since set is not a linear container, it’s impossible to take the element in set by index. Therefore, the only way to traverse the elements of set is to use iterators.

#### Set.find() vs find()

>There is a global algorithm ‘find()’, which takes two iterators, element, and works for O(N). It is possible to use it for searching for element in set, but why use an O(N) algorithm while there exists an O(log N) one?

### Map

> **Remember that set and map have the member functions find() and count(), which works in O(log N), while std::find() and std::count() take O(N).**

