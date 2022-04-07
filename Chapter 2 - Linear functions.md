# **Chapter 2 - Linear functions**

## **2.1 Linear functions and affine functions**

### **Superposition property**
$$
f(\alpha x + \beta y) = \alpha f(x) + \beta f(y)
$$

### **Linearity**
A function that satisfies the superposition property if called *linear*.

### **The inner product function**
The inner product function where $a$ is some $n$-vector
$$
f(x) = a^Tx = a_1x_1 + \dots + a_nx_n
$$
is linear, since it satisfies the superposition property:
$$
\begin{aligned}
f(\alpha x + \beta y) & = a^T(\alpha x + \beta y) \\
& = a^T(\alpha x) + a^T(\beta y) \\
& = \alpha(a^Tx) + \beta(a^Ty) \\
& = \alpha f(x) + \beta f(y)
\end{aligned}
$$

### **Inner product representation of a linear function**
The converse is also true: If a function is linear, then it can be expressed as the inner product of its argument with some fixed vector. In other words, a linear function $f$ can be represented by $f(x) = a^Tx$ for some $n$-vector $a$. We call $a^Tx$ the *inner product representation* of $f$. 

If $f$ is linear, then by multi-term superposition we have 
$$
\begin{aligned}
f(x) & = f(x_1e_1 + \dots + x_ne_n) \\
& = x_1f(e_1) + \dots + x_nf(e_n) \\
& = a^Tx
\end{aligned}
$$
with $a=(f(e_1), f(e_2), \dots, f(e_n))$.

### **Implications**
The formula $f(x) = x_1f(e_1) + x_2f(e_2) + \dots + x_nf(e_n)$ has several interesting implications. Suppose, for example, that the linear function $f$ is given as a subroutine (or a physical system) that computes (or results in the output) $f(x)$ when we give the argument (or input) $x$. Once we have found $f(e_1), \dots, f(e_n)$ by $n$ calls to the subroutine (or $n$ experiments), we can predict (or simulate) what $f(x)$ will be, for *any* vector x. 

The representation of a linear function $f$ as $f(x) = a^Tx$ is unique, which means that there is only one vector $a$ for which $f(x) = a^Tx$ holds. 

### **Affine functions, variation of superposition property, representation, and implication**
An affine function is a linear function plus a constant:
$$
f(x) = a^Tx+b
$$
Any scalar-valued affine function satisfies the following variation on the superposition property:
$$
f(\alpha x + \beta y) = \alpha f(x) + \beta f(y)
$$
for all $n$-vectors $x$, $y$, and all scalars $\alpha$, $\beta$ that satisfy $\alpha + \beta = 1$.

The converse is also true: Any scalar-valued function that satisfies the restricted superposition property is affine. The representation is:
$$
f(x) = f(0) + x_1(f(e_1)-f(0)) + \dots + x_n(f(e_n)-f(0)).
$$
where the vector $a$ and constant $b$ in the representation $f(x) = a^Tx+b$ are: $a_i=f(e_i)-f(0)$, and $b=f(0)$.

This shows that for an affine function, once we know the $n+1$ numbers $f(0)$, $f(e_1)$, \dots, $f(e_n)$, we can predict (or reconstruct or evaluate) $f(x)$ for any $n$-vector $x$.

## **2.2 Taylor approximation**
TODO

## **2.3 Regression model**
$$
\hat{y} = x^T\beta+v
$$
The entries of $x$ are *regressors*, and $\hat{y}$ is the *prediction*. 

### **Simplified regression model notation**
Vector stacking can be used to lump the weights and offset in the regression model into a single parameter vector. We create a new regressor vector $\tilde{x} = (1,x)$ and a parameter vector $\tilde{\beta}=(v,\beta)$, so the regression model has the simpler inner product form:
$$
\hat{y} = x^T\beta + v = 
\begin{bmatrix}
1 \\
x
\end{bmatrix}
\begin{bmatrix}
v \\
\beta
\end{bmatrix}
=\tilde{x}^T\tilde{\beta}.
$$
Often we omit the tildes, and simply write $\hat{y}=x^T\beta$, assuming that the first feature in x in the constant 1. 
