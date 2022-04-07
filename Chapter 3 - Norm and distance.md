# **Chapter 3 - Norm and distance**

## **3.1 Norm**
Euclidean norm:
$$
||x|| = \sqrt{x_1^2+x_2^2+\dots+x_n^2}
$$
or 
$$
||x|| = \sqrt{x^Tx}
$$

The Euclidean norm can be considered a generalization of extension of the absolute value or magnitude that applies to vectors. 

### **Root-mean-square value**
$$
\bold{rms}(x) = \sqrt{\frac{x_1^2+\dots+x_n^2}{n}} = \frac{||x||}{\sqrt{n}}
$$
RMS values are useful when comparing norms of vectors with different dimensions: the RMS value of a vector tells us what a 'typical' value of $|x_i|$ is. 

The argument of the square-root in the middle expression is called the *mean square* value of x, denoted **ms**$(x)$.

### **Norm of a sum**
$$
||x+y|| = \sqrt{||x||^2+2x^Ty+||y||^2}
$$
or
$$
||x+y||^2 = ||x||^2+2x^Ty+||y||^2
$$

### **Norm of block vectors**
For $d=(a,b,c)$:
$$
||d||^2 = ||a||^2+||b||^2+||c||^2
$$
or
$$
||(a,b,c)|| = ||(||a||,||b||,||c||)||
$$

### **Chebyshev inequality**
TODO

## **3.2 Distance**
### **Euclidean distance**
**dist**$(a,b) = ||a-b||$ 

### **Triangle inequality**
$$
||a-c|| \leq ||a-b|| + ||b-c||
$$

### **Units for heterogeneous vector entries**
The entries in the vectors all have equal status in determining the distance between them. For example, if $x_2$ and $y_2$ differ by one, the contribution to the distance between them is the same as the contribution when $x_3$ and $y_3$ differ by one. This makes sense when the entries of the vectors $x$ and $y$ represent the same type of quantity using the same units. However, when the entries of a vector represent different types of quantities, the units must be carefully chosen. If we want the different entries in vectors to have approximately equal status in determining distance, their numerical values should be approximately of the same magnitude.

For example, consider the $2$-vectors, $x$, $y$, and $z$ are the feature vectors for three houses, where the first entry of each vector gives the house area and the second entry gives the number of bedrooms. 

An ideal unit of house area is thousands of square feet. This way, consider three houses with feature vectors
$$
x = (1.6,2), \quad y = (1.5,2), \quad z = (1.6,4).
$$
The first two are close since $||x-y||$=0.1 is small, which matches our intuition that the first two houses are similar since they both have two bedrooms and are close in area. The third house would be considered far from the first two houses.

However, if we choose the unit of house area to be square feet, we'd end up with
$$
x = (1600,2), \quad y = (1500,2), \quad z = (1600,4).
$$
The distance between the first and third houses is now 2, which is very small, while the distance between the first and second houses is much larger. However, it is strange to consider a two-bedroom house and a four-bedroom house to be closer than two houses with the same number of bedrooms but different in only 100 square-feet in area. 

## **3.3 Standard deviation**
### **De-meaned vector**
$$
\tilde{x} = x - \bold{avg}(x)\bold{1}
$$
such that $\bold{avg}(\tilde{x})=0$.
The de-meaned vector is useful for understanding how the entries of a vector deviate from their mean value.

### **Standard deviation**
The *standard deviation* is the RMS value os the de-meaned vector $x - \bold{avg}(x)\bold{1}$
$$
\bold{std}(x) = \sqrt{\frac{(x_1-\bold{avg}(x))^2 + \dots + (x_n-\bold{avg}(x))^2}{n}}.
$$
It can be written using the inner product and norm as
$$
\bold{std}(x) = \frac{||x-\frac{1^Tx}{n}\bold{1}||}{\sqrt{n}}
$$
The standard deviation of a vector x tells us the typical amount by which it entries deviate from their average value.

Using Greek representation,
$$
\mu = \frac{\bold{1}^Tx}{n}, \quad \sigma = \frac{||x-\mu\bold{1}||}{\sqrt(n)}
$$

### **Average, RMS, and standard deviation**
$$
\bold{rms}(x)^2 = \bold{avg}(x)^2 + \bold{std}(x)^2.
$$

### **Properties of standard deviation**
- $\bold{std}(x+a\bold{1}) = \bold{std}(x)$
- $\bold{std}(ax) = |a| \bold{std}(x)$

### **Standardization**
$$
z = \frac{1}{\bold{std}(x)}(x-\bold{avg}(x)\bold{1})
$$

## **3.4 Angle**
### **Angle between vectors**
$$
\theta = \arccos{\frac{a^Tb}{||a||\cdot||b||}}
$$
and
$$
a^Tb=||a||||b||\cos{\theta}
$$

### **Correlation coefficient**
$$
\rho = \frac{\tilde{a}^T\tilde{b}}{||\tilde{a}||||\tilde{b}||}
$$
The correlation coefficient ranges between $-1$ and $+1$. 

### **Standard deviation of sum**
$$
\bold{std}(a+b) = \sqrt{\bold{std}(a)^2+2\rho\ \bold{std}(a) + \bold{std}(b)^2}
$$
If $\rho = 1$,
$$
\bold{std}(a+b)=\bold{std}(a)+\bold{std}(b)
$$
As $\rho$ decreases, the standard deviation of the sum decreases. When $\rho=0$, $i.e., a \text{ and }b$ are uncorrelated,
$$
\bold{std}(a+b)=\sqrt{\bold{std}(a)^2+\bold{std}(b)^2}
$$
If $\rho=-1$,
$$
\bold{std}(a+b)=|\bold{std}(a)-\bold{std}(b)|
$$

### **Hedging investments**
Suppose vectors $a$ and $b$ are time series of returns for two assets with the same return $\mu$ and risk $\sigma$ and correlation coefficient $\rho$. Hedging the two investments give $c=(a+b)/2$. Then
$$
\bold{avg}(c) = \bold{avg}((a+b)/2) = (\bold{avg}(a) + \bold{avg}(b)/2) = \mu
$$
$$
\bold{std}(c) = \sqrt{2\sigma ^2 + 2\rho \sigma ^2} / 2 = \sigma \sqrt{(1+\rho)/2}
$$
When the returns are uncorrelated, the risk is a factor of $1/\sqrt{2} = 0.707$ smaller. When the returns are strongly negatively correlated, the risk is much smaller. **Hedging reduces risk**.
