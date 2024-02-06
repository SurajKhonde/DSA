---
description: opening new horizon
cover: >-
  https://images.unsplash.com/photo-1595225476474-87563907a212?crop=entropy&cs=srgb&fm=jpg&ixid=M3wxOTcwMjR8MHwxfHNlYXJjaHw1fHxEU0F8ZW58MHx8fHwxNzA3MTg5MDI0fDA&ixlib=rb-4.0.3&q=85
coverY: 0
---

# DSA

>
>
> Analysis of Algorithms (Background)
>
> ***
>
> #### What is meant by Algorithm Analysis?
>
> Algorithm analysis is an important part of computational complexity theory, which provides theoretical estimation for the required resources of an algorithm to solve a specific computational problem. Analysis of algorithms is the determination of the amount of time and space resources required to execute it.
>
> #### Why Analysis of Algorithms is important?
>
> * To predict the behavior of an algorithm without implementing it on a specific computer.
> * It is much more convenient to have simple measures for the efficiency of an algorithm than to implement the algorithm and test the efficiency every time a certain parameter in the underlying computer system changes.
> * It is impossible to predict the exact behavior of an algorithm. There are too many influencing factors.
> * The analysis is thus only an approximation; it is not perfect.
> * More importantly, by analyzing different algorithms, we can compare them to determine the best one for our purpose.
>
> #### Types of Algorithm Analysis:
>
> 1. Best case
> 2. Worst case
> 3. Average case
>
> [Link text](http://www.example.com)
>
> Asymptotic Analysis
>
> ***
>
> _In Asymptotic Analysis, we **evaluate the performance of an algorithm in terms of input size** (we don’t measure the actual running time). We calculate, how the time (or space) taken by an algorithm increases with the input size._&#x20;
>
> ### Why performance analysis?&#x20;
>
> There are many important things that should be taken care of, like user-friendliness, modularity, security, maintainability, etc. Why worry about performance?  The answer to this is simple, we can have all the above things only if we have performance. So performance is like currency through which we can buy all the above things. Another reason for studying performance is – speed is fun! To summarize, performance == scale. Imagine a text editor that can load 1000 pages, but can spell check 1 page per minute OR an image editor that takes 1 hour to rotate your image 90 degrees left OR … you get it. If a software feature can not cope with the scale of tasks users need to perform – it is as good as dead.&#x20;
>
> ### Given two algorithms for a task, how do we find out which one is better?&#x20;
>
> One naive way of doing this is – to implement both the algorithms and run the two programs on your computer for different inputs and see which one takes less time. There are many problems with this approach for the analysis of algorithms.&#x20;
>
> * It might be possible that for some inputs, the first algorithm performs better than the second. And for some inputs second performs better.&#x20;
> * It might also be possible that for some inputs, the first algorithm performs better on one machine, and the second works better on another machine for some other inputs.
>
> [_Asymptotic Analysis_](http://en.wikipedia.org/wiki/Asymptotic\_analysis) _is the big idea that handles the above issues in analyzing algorithms. In Asymptotic Analysis, we **evaluate the performance of an algorithm in terms of input size** (we don’t measure the actual running time). We calculate, how the time (or space) taken by an algorithm increases with the input size._&#x20;
>
> **For example**, let us consider the search problem (searching a given item) in a sorted array.&#x20;
>
> The solution to above search problem includes:&#x20;
>
> * **Linear Search** (order of growth is linear)&#x20;
> * **Binary Search** (order of growth is logarithmic).&#x20;
>
> To understand how Asymptotic Analysis solves the problems mentioned above in analyzing algorithms,&#x20;
>
> * let us say:&#x20;
>   * we run the Linear Search on a fast computer A and&#x20;
>   * Binary Search on a slow computer B and&#x20;
>   * pick the constant values for the two computers so that it tells us exactly how long it takes for the given machine to perform the search in seconds.&#x20;
> * Let’s say the constant for A is 0.2 and the constant for B is 1000 which means that A is 5000 times more powerful than B.&#x20;
> * For small values of input array size n, the fast computer may take less time.&#x20;
> * **But, after a certain value of input array size, the Binary Search will definitely start taking less time compared to the Linear Search even though the Binary Search is being run on a slow machine**.&#x20;

| Input Size | Running time on A | Running time on B |
| ---------- | ----------------- | ----------------- |
| 10         | 2 sec             | \~ 1 h            |
| 100        | 20 sec            | \~ 1.8 h          |
| 10^6       | \~ 55.5 h         | \~ 5.5 h          |
| 10^9       | \~ 6.3 years      | \~ 8.3 h          |

> * The reason is the order of growth of Binary Search with respect to input size is logarithmic while the order of growth of Linear Search is linear.&#x20;
> * **So the machine-dependent constants can always be ignored after a certain value of input size.**&#x20;
>
> Running times for this example:&#x20;
>
> * Linear Search running time in seconds on A: 0.2 \* n&#x20;
> * Binary Search running time in seconds on B: 1000\*log(n)&#x20;
>
> ### Does Asymptotic Analysis always work?&#x20;
>
> Asymptotic Analysis is not perfect, but that’s the best way available for analyzing algorithms. For example, say there are two sorting algorithms that take 1000nLogn and 2nLogn time respectively on a machine. Both of these algorithms are asymptotically the same (order of growth is nLogn). So, With Asymptotic Analysis, we can’t judge which one is better as we ignore constants in Asymptotic Analysis.&#x20;
>
> Also, in Asymptotic analysis, we always talk about input sizes larger than a constant value. It might be possible that those large inputs are never given to your software and an asymptotically slower algorithm always performs better for your particular situation. So, you may end up choosing an algorithm that is Asymptotically slower but faster for your software.
>
> Please write comments if you find anything incorrect, or if you want to share more information about the topic discussed above
>
> ***
>
> Horizontal rule for section breaks
>
> ***
>
> ```
> ```

Asymptotic Notation

***

We have discussed [Asymptotic Analysis](https://www.cdn.geeksforgeeks.org/analysis-of-algorithms-set-1-asymptotic-analysis/), and[ Worst, Average](https://www.cdn.geeksforgeeks.org/analysis-of-algorithms-set-2-asymptotic-analysis/),[ and Best Cases of Algorithms](https://www.cdn.geeksforgeeks.org/analysis-of-algorithms-set-2-asymptotic-analysis/). The main idea of asymptotic analysis is to have a measure of the efficiency of algorithms that don't depend on machine-specific constants and don't require algorithms to be implemented and time taken by programs to be compared. Asymptotic notations are mathematical tools to represent the time complexity of algorithms for asymptotic analysis. The following 3 asymptotic notations are mostly used to represent the time complexity of algorithms. \
\
\
![thetanotation](https://media.geeksforgeeks.org/wp-content/uploads/AlgoAnalysis-1.png)

&#x20;

**1) Θ Notation:** The theta notation bounds a function from above and below, so it defines exact asymptotic behavior. \
A simple way to get the Theta notation of an expression is to drop low-order terms and ignore leading constants. For example, consider the following expression. \
3n3 + 6n2 + 6000 = Θ(n3)&#x20;

Dropping lower order terms is always fine because there will always be a number(n) after which Θ(n3) has higher values than Θ(n2) irrespective of the constants involved.&#x20;

For a given function g(n), we denote Θ(g(n)) is following set of functions.&#x20;

```
Θ(g(n)) = {f(n): there exist positive constants c1, c2 and n0 such 
                 that 0 <= c1*g(n) <= f(n) <= c2*g(n) for all n >= n0}
```

&#x20;

The above definition means, if f(n) is theta of g(n), then the value f(n) is always between c1\*g(n) and c2\*g(n) for large values of n (n >= n0). The definition of theta also requires that f(n) must be non-negative for values of n greater than n0. \
\
\
![BigO](https://media.geeksforgeeks.org/wp-content/uploads/AlgoAnalysis-2.png)\
&#x20;

**2) Big O Notation:** The Big O notation defines an upper bound of an algorithm, it bounds a function only from above. For example, consider the case of Insertion Sort. It takes linear time in the best case and quadratic time in the worst case. We can safely say that the time complexity of Insertion sort is O(n^2). Note that O(n^2) also covers linear time.&#x20;

If we use Θ notation to represent time complexity of Insertion sort, we have to use two statements for best and worst cases: \
1\. The worst-case time complexity of Insertion Sort is Θ(n^2). \
2\. The best case time complexity of Insertion Sort is Θ(n).&#x20;

The Big O notation is useful when we only have an upper bound on the time complexity of an algorithm. Many times we easily find an upper bound by simply looking at the algorithm. &#x20;

```
O(g(n)) = { f(n): there exist positive constants c and 
                  n0 such that 0 <= f(n) <= c*g(n) for 
                  all n >= n0}
```

\
\
![BigOmega](https://media.geeksforgeeks.org/wp-content/uploads/AlgoAnalysis-3.png)\
&#x20;

**3) Ω Notation:** Just as Big O notation provides an asymptotic upper bound on a function, Ω notation provides an asymptotic lower bound. \
Ω Notation can be useful when we have a lower bound on the time complexity of an algorithm. As discussed in the previous post, the [best case performance of an algorithm is generally not useful](https://www.cdn.geeksforgeeks.org/analysis-of-algorithms-set-2-asymptotic-analysis/), the Omega notation is the least used notation among all three.&#x20;

For a given function g(n), we denote by Ω(g(n)) the set of functions. &#x20;

```
Ω (g(n)) = {f(n): there exist positive constants c and
                  n0 such that 0 <= c*g(n) <= f(n) for
                  all n >= n0}.
```

Let us consider the same Insertion sort example here. The time complexity of Insertion Sort can be written as Ω(n), but it is not very useful information about insertion sort, as we are generally interested in worst-case and sometimes in the average case. \
\
**Properties of Asymptotic Notations :** \
As we have gone through the definition of these three notations let's now discuss some important properties of those notations.&#x20;

**1. General Properties :** \
&#x20;    If f(n) is O(g(n)) then a\*f(n) is also O(g(n)) ; where a is a constant.&#x20;

&#x20;    Example: f(n) = 2n²+5 is O(n²) \
&#x20;    then 7\*f(n) = 7(2n²+5) = 14n²+35 is also O(n²) .\
\
&#x20;    Similarly, this property satisfies both Θ and Ω notation.&#x20;

\
&#x20;    We can say \
&#x20;    If f(n) is Θ(g(n)) then a\*f(n) is also Θ(g(n)) ; where a is a constant. \
&#x20;    If f(n) is Ω (g(n)) then a\*f(n) is also Ω (g(n)) ; where a is a constant.

&#x20;

**2. Transitive Properties :**&#x20;

&#x20;    If f(n) is O(g(n)) and g(n) is O(h(n)) then f(n) = O(h(n))

&#x20;   Example: if f(n) = n, g(n) = n² and h(n)=n³\
&#x20;   n is O(n²) and n² is O(n³)\
&#x20;   then n is O(n³)

&#x20;  Similarly, this property satisfies both Θ and Ω notation.

&#x20;  We can say\
&#x20;  If f(n) is Θ(g(n)) and g(n) is Θ(h(n)) then f(n) = Θ(h(n)) .\
&#x20;  If f(n) is Ω (g(n)) and g(n) is Ω (h(n)) then f(n) = Ω (h(n))

&#x20;

**3. Reflexive Properties** :&#x20;

&#x20;     Reflexive properties are always easy to understand after transitive.

&#x20;     If f(n) is given then f(n) is O(f(n)). Since _MAXIMUM VALUE OF f(n) will be f(n) ITSELF !_

&#x20;     Hence x = f(n) and y = O(f(n) tie themselves in reflexive relation always.

&#x20;    _Example:_ f(n) = n² ; O(n²) i.e O(f(n))

&#x20;     Similarly, this property satisfies both Θ and Ω notation.

&#x20;     _We can say that:_

&#x20;     If f(n) is given then f(n) is Θ(f(n)).

&#x20;     If f(n) is given then f(n) is Ω (f(n)).

&#x20;

**4. Symmetric Properties :**&#x20;

&#x20;     If f(n) is Θ(g(n)) then g(n) is Θ(f(n)) .&#x20;

&#x20;     Example: f(n) = n² and g(n) = n² \
&#x20;     then f(n) = Θ(n²) and g(n) = Θ(n²)&#x20;

&#x20;     **This property only satisfies for Θ notation.**

&#x20;

**5. Transpose Symmetric Properties :**&#x20;

&#x20;     If f(n) is O(g(n)) then g(n) is Ω (f(n)).&#x20;

&#x20;     _Example:_ f(n) = n , g(n) = n² \
&#x20;     then n is O(n²) and n² is Ω (n) \
\
&#x20;     **This property only satisfies O and Ω notations**.

&#x20;

**6. Some More Properties :**&#x20;

&#x20;    1.) If f(n) = O(g(n)) and f(n) = Ω(g(n)) then f(n) = Θ(g(n))

&#x20;    2.) If f(n) = O(g(n)) and d(n)=O(e(n)) \
&#x20;         then f(n) + d(n) = O( max( g(n), e(n) )) \
&#x20;         _Example:_ f(n) = n i.e O(n) \
&#x20;                        d(n) = n² i.e O(n²) \
&#x20;                        then f(n) + d(n) = n + n² i.e O(n²)

&#x20;     3.) If f(n)=O(g(n)) and d(n)=O(e(n)) \
&#x20;          then f(n) \* d(n) = O( g(n) \* e(n) ) \
&#x20;          _Example:_ f(n) = n i.e O(n) \
&#x20;          d(n) = n² i.e O(n²) \
&#x20;                     then f(n) \* d(n) = n \* n² = n³ i.e O(n³)

**\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_**\
\
**Exercise:** \
**Ques:** Consider the following functions from positives integers to real numbers

* 10, √n, n, log2n, 100/n.

Arrange them in increasing order of asymptotic complexity.

1. &#x20;log2n, 100/n, 10, √n, n
2. 100/n, 10, log2n, √n, n
3. 10, 100/n ,√n, log2n, n
4. 100/n, log2n, 10 ,√n, n

**Answer: 2**\
\
&#x20;**Important Links :**

* There are two more notations called [**little o and little omega**](https://www.geeksforgeeks.org/analysis-of-algorithems-little-o-and-little-omega-notations/). Little o provides a strict upper bound (equality condition is removed from Big O) and little omega provides strict lower bound (equality condition removed from big omega)
* [Analysis of Algorithms | Set 4 (Analysis of Loops)](https://www.geeksforgeeks.org/analysis-of-algorithms-set-4-analysis-of-loops/)
* [Recent Articles on analysis of algorith](https://www.geeksforgeeks.org/category/algorithm/analysis/)\


Analysis of Recursion

***

Many algorithms are recursive. When we analyze them, we get a recurrence relation for time complexity. We get running time on an input of size n as a function of n and the running time on inputs of smaller sizes. For example in Merge Sort, to sort a given array, we divide it into two halves and recursively repeat the process for the two halves. Finally, we merge the results. Time complexity of Merge Sort can be written as T(n) = 2T(n/2) + cn. There are many other algorithms like Binary Search, Tower of Hanoi, etc. \
\
There are mainly three ways of solving recurrences:

### Substitution Method:&#x20;

We make a guess for the solution and then we use mathematical induction to prove the guess is correct or incorrect.&#x20;

> For example consider the recurrence T(n) = 2T(n/2) + n
>
> We guess the solution as T(n) = O(nLogn). Now we use induction to prove our guess.
>
> We need to prove that T(n) <= cnLogn. We can assume that it is true for values smaller than n.
>
> T(n) = 2T(n/2) + n\
> &#x20;    <= 2c(n/2Log(n/2)) + n\
> &#x20;      \=  cnLogn - cnLog2 + n\
> &#x20;      \=  cnLogn - cn + n\
> &#x20;   <= cnLogn

### **Recurrence Tree Method:**

In this method, we draw a recurrence tree and calculate the time taken by every level of the tree. Finally, we sum the work done at all levels. To draw the recurrence tree, we start from the given recurrence and keep drawing till we find a pattern among levels. The pattern is typically arithmetic or geometric series. \
&#x20;

> For example, consider the recurrence relation&#x20;
>
> T(n) = T(n/4) + T(n/2) + cn2
>
> &#x20;           cn2\
> &#x20;           /      \\\
> &#x20; T(n/4)     T(n/2)
>
> If we further break down the expression T(n/4) and T(n/2), \
> we get the following recursion tree.
>
> &#x20;                   cn2\
> &#x20;             /             \      \
> &#x20;   c(n2)/16          c(n2)/4\
> &#x20;  /         \            /         \\\
> T(n/16)  T(n/8)  T(n/8)    T(n/4)&#x20;
>
> Breaking down further gives us following
>
> &#x20;                      cn2 \
> &#x20;               /                \     \
> &#x20;      c(n2)/16              c(n2)/4\
> &#x20;   /          \                 /          \\\
> c(n2)/256  c(n2)/64  c(n2)/64   c(n2)/16\
> &#x20;/    \            /    \      /    \        /    \ &#x20;
>
> To know the value of T(n), we need to calculate the sum of tree \
> nodes level by level. If we sum the above tree level by level,&#x20;
>
> we get the following series T(n)  = c(n^2 + 5(n^2)/16 + 25(n^2)/256) + ....\
> The above series is a geometrical progression with a ratio of 5/16.
>
> To get an upper bound, we can sum the infinite series. We get the sum as (n2)/(1 - 5/16) which is O(n2)

### **Master Method:**&#x20;

Master Method is a direct way to get the solution. The master method works only for the following type of recurrences or for recurrences that can be transformed into the following type. \
&#x20;

> T(n) = aT(n/b) + f(n) where a >= 1 and b > 1

\
There are the following three cases:&#x20;

* If f(n) = O(nc) where c < Logba then T(n) = Θ(nLogba)&#x20;
* If f(n) = Θ(nc) where c = Logba then T(n) = Θ(ncLog n)&#x20;
* If f(n) = Ω(nc) where c > Logba then T(n) = Θ(f(n))&#x20;

#### **How does this work?**&#x20;

The master method is mainly derived from the recurrence tree method. If we draw the recurrence tree of T(n) = aT(n/b) + f(n), we can see that the work done at the root is f(n), and work done at all leaves is Θ(nc) where c is Logba. And the height of the recurrence tree is Logbn \
&#x20;

![Master Theorem](https://media.geeksforgeeks.org/wp-content/uploads/AlgoAnalysis.png)

\
In the recurrence tree method, we calculate the total work done. If the work done at leaves is polynomially more, then leaves are the dominant part, and our result becomes the work done at leaves (Case 1). If work done at leaves and root is asymptotically the same, then our result becomes height multiplied by work done at any level (Case 2). If work done at the root is asymptotically more, then our result becomes work done at the root (Case 3). \
\
**Examples of some standard algorithms whose time complexity can be evaluated using the Master Method**&#x20;

* [Merge Sort](http://geeksquiz.com/merge-sort/): T(n) = 2T(n/2) + Θ(n). It falls in case 2 as c is 1 and Logba] is also 1. So the solution is Θ(n Logn)&#x20;
* [Binary Search](http://geeksquiz.com/binary-search/): T(n) = T(n/2) + Θ(1). It also falls in case 2 as c is 0 and Logba is also 0. So the solution is Θ(Logn)&#x20;

**Notes:**&#x20;

* It is not necessary that a recurrence of the form T(n) = aT(n/b) + f(n) can be solved using Master Theorem. The given three cases have some gaps between them. For example, the recurrence T(n) = 2T(n/2) + n/Logn cannot be solved using master method.&#x20;
* Case 2 can be extended for f(n) = Θ(ncLogkn) \
  If f(n) = Θ(ncLogkn) for some constant k >= 0 and c = Logba, then T(n) = Θ(ncLogk+1n)&#x20;

\
Recursion Tree Method for solving Recurrences

***

The [Recursion Tree Method](https://www.geeksforgeeks.org/analysis-algorithm-set-4-master-method-solving-recurrences/) is a way of solving[ recurrence relations](https://www.geeksforgeeks.org/different-types-recurrence-relations-solutions/). In this method, a recurrence relation is converted into recursive trees. Each node represents the cost incurred at various levels of recursion. To find the total cost, costs of all levels are summed up.

\


\


\


\


**Steps to solve recurrence relation using recursion tree method:**

\


\


1. Draw a recursive [tree](https://www.geeksforgeeks.org/tree-traversals-inorder-preorder-and-postorder/) for given recurrence relation
2. Calculate the cost at each level and count the total no of levels in the recursion tree.
3. Count the total number of nodes in the last level and calculate the cost of the last level
4. Sum up the cost of all the levels in the recursive tree

\


\


**Let us see how to solve these recurrence relations with the help of some examples:**

\


\


**Question 1:**

T(n) = 2T(n/2) + c

**Solution:**&#x20;

* **Step 1:** Draw a recursive tree&#x20;

<figure><img src="https://media.geeksforgeeks.org/wp-content/uploads/20210608083944/img-300x172.PNG" alt="Recursion Tree" width="300"><figcaption><p>Recursion Tree</p></figcaption></figure>

* **Step 2:** Calculate the work done or cost at each level and count total no of levels in recursion tree&#x20;

<figure><img src="https://media.geeksforgeeks.org/wp-content/uploads/20210608091942/img1-300x141.PNG" alt="Recursive Tree with each level cost" width="300"><figcaption><p>Recursive Tree with each level cost</p></figcaption></figure>

**Count the total number of levels -**&#x20;

Choose the longest path from root node to leaf node

> &#x20;n/20 -→ n/21 -→ n/22 -→ ......... -→ n/2k

Size of problem at last level = n/2k

&#x20;At last level size of problem becomes 1

> &#x20;n/2k = 1
>
> &#x20;2k = n
>
> &#x20;**k = log2(n)**  &#x20;

**Total no of levels  in recursive tree = k +1 = log2(n) + 1**

* **Step 3:** Count total number of nodes in the last level and calculate cost of last level

> &#x20;No. of nodes at level 0 = 20 = 1
>
> &#x20; No. of nodes at level 1 = 21 = 2
>
> &#x20;...............................................................
>
> &#x20;No. of nodes at level log2(n) = 2log2(n) = nlog2(2) = n
>
> &#x20;Cost of sub problems at level log2(n) (last level) = nxT(1) = nx1 = n &#x20;

* **Step 4:** Sum up the cost all the levels in recursive tree &#x20;

> &#x20;  T(n) = c + 2c + 4c + ---- + (no. of levels-1) times + last level cost
>
> &#x20;\= c + 2c + 4c + ---- + log2(n) times + Θ(n)
>
> &#x20;\= c(1 + 2 + 4 + ---- + log2(n) times) + Θ(n)
>
> &#x20;1 + 2 + 4 + ----- + log2(n) times --> 20 + 21 + 22 + ----- + log2(n) times --> Geometric Progression(G.P.)
>
> \= c(n) + Θ(n)

Thus, _**T(n) = Θ(n)**_

**Question 2: T(n) = T(n/10) + T(9n/10) + n**

**Solution:**&#x20;

* **Step 1:** Draw a recursive tree

&#x20;

<figure><img src="https://media.geeksforgeeks.org/wp-content/uploads/20210608101924/img-300x167.PNG" alt="Recursive Tree" width="300"><figcaption><p>Recursive Tree</p></figcaption></figure>

* **Step 2:** Calculate the work done or cost at each level and count total no of levels in recursion tree

<figure><img src="https://media.geeksforgeeks.org/wp-content/uploads/20210608103658/img1-300x129.PNG" alt="Recursion Tree with each level cost" width="300"><figcaption><p>Recursion Tree with each level cost</p></figcaption></figure>

&#x20;**Count the total number of levels -**

&#x20;Choose the longest path from root node to leaf node

> (9/10)0n --> (9/10)1n --> (9/10)2n --> ......... --> (9/10)kn
>
> &#x20;Size of problem at last level = (9/10)kn
>
> &#x20;At last level size of problem becomes 1
>
> (9/10)kn = 1
>
> (9/10)k = 1/n
>
> &#x20; **k = log10/9(n)**

&#x20;**Total no of levels in recursive tree = k +1 = log10/9(n) + 1**

* **Step 3:** Count total number of nodes in the last level and calculate cost of last level

> No. of nodes at level 0 = 20 = 1
>
> No. of nodes at level 1 = 21 = 2
>
> ...............................................................
>
> No. of nodes at level log10/9(n) = 2log10/9(n) = nlog10/9(2)
>
> Cost of sub problems at level log2(n) (last level) = nlog10/9(2) x T(1) = nlog10/9(2) x 1 = nlog10/9(2) &#x20;
>
> * **Step 4:** Sum up the cost all the levels in recursive tree &#x20;
>
> T(n) = n + n + n + ---- + (no. of levels - 1) times + last level cost
>
> &#x20;\= n + n + n + ---- + log10/9(n) times + Θ(nlog10/9(2))
>
> \= nlog10/9(n) + Θ(nlog10/9(2))

Thus, _**T(n) = Θ(n^log10/9(n))**_  \


Applications of Recursion

***

Recursion is a powerful concept in computer programming that allows us to solve problems in a cleaner and more elegant way. Recursion is often used when a task can be broken down into smaller, repetitive tasks. In this article, we'll discuss some common applications of recursion in JavaScript and provide code examples to help illustrate these concepts.

1. Factorial Calculation

One of the most common examples of recursion is calculating the factorial of a number. Factorial is the product of all positive integers up to and including a given number. For example, the factorial of 5 is 5 \* 4 \* 3 \* 2 \* 1 = 120.

Here's an example of a recursive function in JavaScript that calculates the factorial of a number:

```
javascriptCopy codefunction factorial(n) {
  if (n === 0) {
    return 1;
  } else {
    return n * factorial(n - 1);
  }
}
```

1. Traversing a Tree Structure

Another common application of recursion is traversing a tree structure. A tree is a hierarchical data structure that consists of nodes and edges. Each node in a tree has a parent node and zero or more child nodes. Recursion can be used to traverse a tree and perform operations on each node.

Here's an example of a recursive function in JavaScript that performs a pre-order traversal of a binary tree:

```
scssCopy codefunction preOrderTraversal(node) {
  if (!node) {
    return;
  }
  console.log(node.value);
  preOrderTraversal(node.left);
  preOrderTraversal(node.right);
}
```

1. Generating Permutations and Combinations

Recursion can also be used to generate all permutations and combinations of a given set of elements. For example, we can use recursion to generate all possible combinations of a given set of characters.

Here's an example of a recursive function in JavaScript that generates all permutations of a given string:

```
rustCopy codefunction permutations(str) {
  if (str.length === 1) {
    return [str];
  }
  const result = [];
  for (let i = 0; i < str.length; i++) {
    const firstChar = str[i];
    const otherChars = str.substring(0, i) + str.substring(i + 1);
    const otherPermutations = permutations(otherChars);
    for (const permutation of otherPermutations) {
      result.push(firstChar + permutation);
    }
  }
  return result;
}
```

In conclusion, recursion is a powerful concept that allows us to solve problems in a cleaner and more elegant way. Whether we're calculating a factorial, traversing a tree structure, or generating permutations and combinations, recursion can help us write more efficient and maintainable code.



***

&#x20;in JavaScript that calculates the factorial of a number:

```
javascriptCopy codefunction factorial(n) {
  if (n === 0) {
    return 1;
  } else {
    return n * factorial(n - 1);
  }
}
```

1. Traversing a Tree Structure

Another common application of recursion is traversing a tree structure. A tree is a hierarchical data structure that consists of nodes and edges. Each node in a tree has a parent node and zero or more child nodes. Recursion can be used to traverse a tree and perform operations on each node.

Here's an example of a recursive function in JavaScript that performs a pre-order traversal of a binary tree:

```
scssCopy codefunction preOrderTraversal(node) {
  if (!node) {
    return;
  }
  console.log(node.value);
  preOrderTraversal(node.left);
  preOrderTraversal(node.right);
}
```

1. Generating Permutations and Combinations

Recursion can also be used to generate all permutations and combinations of a given set of elements. For example, we can use recursion to generate all possible combinations of a given set of characters.

Here's an example of a recursive function in JavaScript that generates all permutations of a given string:

```
rustCopy codefunction permutations(str) {
  if (str.length === 1) {
    return [str];
  }
  const result = [];
  for (let i = 0; i < str.length; i++) {
    const firstChar = str[i];
    const otherChars = str.substring(0, i) + str.substring(i + 1);
    const otherPermutations = permutations(otherChars);
    for (const permutation of otherPermutations) {
      result.push(firstChar + permutation);
    }
  }
  return result;
}
```

In conclusion, recursion is a powerful concept that allows us to solve problems in a cleaner and more elegant way. Whether we're calculating a factorial, traversing a tree structure, or generating permutations and combinations, recursion can help us write more efficient and maintainable code.

\
