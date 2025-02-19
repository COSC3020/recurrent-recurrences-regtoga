# Recurrent Recurrences

Give big $\Theta$ bounds for the following recurrence relations.

1.
$$ T(n) =
    \begin{cases}
        1 & n \leq 1\\
        T\left(\frac{n}{13}\right) + 5 & n > 1
    \end{cases}
$$

2.
$$ T(n) =
    \begin{cases}
        1 & n \leq 1\\
        13 T\left(\frac{n}{13}\right) + 5 & n > 1
    \end{cases}
$$

3.
$$ T(n) =
    \begin{cases}
        1 & n \leq 1\\
        13 T\left(\frac{n}{13}\right) + 2n & n > 1
    \end{cases}
$$

### 1.

$
T(n) = T\left(\frac{n}{13}\right) + 5
$

$
T(n) = T\left(\frac{n}{13^2}\right) + 5 \cdot 2
$

$
T(n) = T\left(\frac{n}{13^3}\right) + 5 \cdot 3
$

continuing this process:

$
T(n) = T\left(\frac{n}{13^i}\right) + 5i
$

setting $( i = \log_{13}(n) )$ we get:

$
T(n) = T(1) + 5 \log_{13}(n)
$

since $( T(1) )$ is a constant the complexity is:

$
\Theta(\log n)
$

$
T(n) \in O(\log n)
$

---

### 2.

$
T(n) = 13 T\left(\frac{n}{13}\right) + 5
$

$
T(n) = 13 \left( 13 T\left(\frac{n}{13^2}\right) + 5 \right) + 5
$

$
T(n) = 13^2 T\left(\frac{n}{13^2}\right) + 5 \cdot (1 + 13)
$

continuing this process:

$
T(n) = 13^i T\left(\frac{n}{13^i}\right) + 5 \sum_{k=0}^{i-1} 13^k
$

using the geometric series sum:

$
\sum_{k=0}^{i-1} 13^k = \frac{13^i - 1}{13 - 1}
$

setting $( i = \log_{13}(n) )$ we get:

$
T(n) = 13^{\log_{13}(n)} T(1) + \frac{5(13^{\log_{13}(n)} - 1)}{12}
$

since $( 13^{\log_{13}(n)} = n )$ this simplifies to:

$
T(n) = n T(1) + O(n)
$

$
\Theta(n \log n)
$

$
T(n) \in O(n \log n)
$

---

### 3.

$
T(n) = 13 T\left(\frac{n}{13}\right) + 2n
$

$
T(n) = 13 \left( 13 T\left(\frac{n}{13^2}\right) + 2 \frac{n}{13} \right) + 2n
$

$
T(n) = 13^2 T\left(\frac{n}{13^2}\right) + 2n \left(1 + \frac{1}{13} \right)
$

continuing this process:

$
T(n) = 13^i T\left(\frac{n}{13^i}\right) + 2n \sum_{k=0}^{i-1} \frac{1}{13^k}
$

using the geometric series sum

$
\sum_{k=0}^{i-1} \frac{1}{13^k} = \frac{1 - 13^{-i}}{1 - \frac{1}{13}}
$

setting $( i = \log_{13}(n) )$ we get:

$
T(n) = 13^{\log_{13}(n)} T(1) + 2n \frac{1 - 13^{-\log_{13}(n)}}{\frac{12}{13}}
$

approximating for large $( n )$:

$
T(n) = n T(1) + O(n \log n)
$

$
T(n) \in O(n \log n)
$

Answers in text:

1. O(log(n))
2. O(nlog(n))
3. O(nlog(n))

I certify that I have listed all sources used to complete this exercise, including the use of any Large Language Models. All of the work is my own, except where stated otherwise. I am aware that plagiarism carries severe penalties and that if plagiarism is suspected, charges may be filed against me without prior notice.