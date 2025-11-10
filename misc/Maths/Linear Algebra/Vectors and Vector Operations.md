## Vectors
**Dimensionality**: The number of elements in the vector.
**Orientation**: Whether the vector is in **column** or **row** orientation.

Dimensionality is often indicated using $\mathbb{R}^N$ where $\mathbb{R}$ represents real numbers ($\mathbb{C}$ for complex numbers) and $^N$ indicates the dimensionality.

For example, $\mathbb{R}^2$ is a vector with two elements.

$$
x=\begin{bmatrix}  
1 \\  
4 \\
5 \\
6
\end{bmatrix} y=\begin{bmatrix} 0.3 \\ -7 \end{bmatrix} z=\begin{bmatrix} 1 & 4 & 5 & 6 \end{bmatrix} 
$$
Where: ($\in$ means "is contained in the set of")
$x \in \mathbb{R}^4$ row vector
$y \in \mathbb{R}^2$ column vector
$z \in \mathbb{R}^4$ row vector

When referring to vectors, the correct terminology is: $\overrightarrow{v}$

Row vectors are written as $w^T$. The $^T$ indicates the transposition operation.

To represent vectors in Python, you can do it as follows:
```python
asList = [1,2,3]
asArray = np.array([1,2,3]) # 1D array
rowVec = np.array([ [1,2,3] ]) # row
colVec = np.array([ [1], [2], [3] ]) # column
```

The `asArray` variable is an undirected array, meaning it's simply a 1D list in NumPy.

## Operations with vectors
### Addition of two vectors
$$
\begin{bmatrix}  4 \\  5 \\ 6 \end{bmatrix} + \begin{bmatrix} 10 \\ 20 \\ 30 \end{bmatrix} = \begin{bmatrix} 14 \\ 25 \\ 36 \end{bmatrix} 
$$
### Subtraction of two vectors
$$
\begin{bmatrix}  4 \\  5 \\ 6 \end{bmatrix} - \begin{bmatrix} 10 \\ 20 \\ 30 \end{bmatrix} = \begin{bmatrix} -6 \\ -15 \\ -24 \end{bmatrix} 
$$
### Broadcasting (Python Only)
$$
\begin{bmatrix}  4 \\  5 \\ 6 \end{bmatrix} + \begin{bmatrix} 10 & 20 & 30 \end{bmatrix} = \begin{bmatrix} 14 & 15&16 \\ 24&25&26 \\ 34&35&36 \end{bmatrix} 
$$
### Vector-Scalar Multiplication
A scalar in linear algebra is a number on its own. It is usually denoted by Greek letters ($\alpha, \lambda$).
Vector-scalar multiplication is denoted, for example, $\beta u$.

It is used to multiply each vector element by the scalar:
$$
\lambda=4, w= \begin{bmatrix} 9 \\ 4 \\ 1 \end{bmatrix}, \lambda w=\begin{bmatrix} 36 \\ 16 \\ 4 \end{bmatrix}
$$
A vector of all zeros is called a "_vector of zeros_" denoted as $0y$, it is a special vector in linear algebra and is often called the "_trivial solution_".

### Transposition
$$
m^{T}_{i,j}=m_{j,i}
$$
Transposing twice returns the vector to its original orientation.
$$
v^{TT}=v
$$
### Vector magnitudes and Unit Vectors
The magnitude of a vector, also called its geometric length, is the distance from the tail to the head of a vector and is calculated using the standard Euclidean distance formula. (The square root of the sum of the squared elements of the vector.)
$$
|| v ||=\sqrt{\sum^n_{i=1}v^2_i}
$$
Some applications use squared magnitudes (written as $||v||^2$), in which case the square root term disappears from the right-hand side.

In mathematics, the dimensionality of a vector is the number of elements in that vector.

Whereas in Python, the function:
```python 
len() # DIMENSIONALITY
```
is shorthand for `length` and returns the dimensionality of an array. 

The function:
```python
np.norm() # MAGNITUDE
```
It returns the geometric length (magnitude).

A unit vector is defined as $||v||=1$.

To create a unit vector:
$$
\hat v=\frac{1}{||v||}v
$$
Where $\hat v$ indicates a unit vector.

> There is a vector that does not have an associated unit vector, and that vector is 0.

### Dot product or inner product
It is a unique number that provides information about the relationship between two vectors.

$$
a^Tb
$$
To calculate the dot product, we multiply the corresponding elements of the two vectors and then sum all the individual products.

In summary:
1. Multiply by the elements
2. Sum them
$$
\delta = \sum^{n}_{i=1}a_ib_i
$$
It is only valid between two vectors of the same dimension.

Example:
$$
\begin{bmatrix} 1 & 2 & 3 & 4 \end{bmatrix} - \begin{bmatrix} 5 & 6 & 7 & 8 \end{bmatrix} = 1 * 5 + 2*6+3*7 + 4*8 = 5+12+21+32 = 70
$$

In Python, to implement dot multiplication, we use the function $np.dot()$:
```python
v = np.array([1,2,3,4])
w = np.array([5,6,7,8])
np.dot(v,w)
```

> **Note on NP.DOT()**
> > It doesn't actually implement the vector dot product; it implements matrix multiplication, which is a collection of dot products.

This product can be interpreted as a measure of **similarity** or **correspondence** between two vectors. Imagine you collect data on the weight and height of 20 people and store it in two vectors. To determine if these variables are related (taller people tend to weigh more), you might expect the dot product between these two vectors to be large. To normalize it, we use the **[[Pearson correlation coefficient]]**.

#### The dot product is distributive.
The distributive property in mathematics is that:
$$
a^T(b+c) = a^Tb+a^Tc
$$
The dot product of a sum of vectors is equal to the sum of the dot products of the vectors.
In Python:
```python
a = np.array([ 0,1,2 ])
b = np.array([ 3,5,8 ])
c = np.array([ 13,21,34 ])

# distributivo
res1 = np.dot( a, b+c )
res2 = np.dot( a,b ) + np.dot( a,c )
```

### Dot Product Geometry
The product of the magnitudes of the two vectors, scaled by the cosine of the angle between them.
$$
\alpha = cos(\theta_{v,w})\,||v|| \, ||w||
$$
> **ORTHOGONAL VECTORS HAVE A DOT PRODUCT OF 0**
> >Two vectors are orthogonal; Two vectors have a dot product of 0; Two meet at a 90° angle.

### Other vector multiplications:
##### Hadamard multiplication
Each corresponding element of the two vectors is multiplied.
The product is a vector of the same dimension as the two vectors being multiplied.
For example:
$$
\begin{bmatrix} 5 \\ 4 \\ 8 \\ 2 \end{bmatrix} \odot \begin{bmatrix} 1 \\ 0 \\ 0.5 \\ -1\end{bmatrix} = \begin{bmatrix} 5 \\ 0 \\ 4 \\ -2\end{bmatrix}
$$
Another example, we have these two matrices:
$$
A=\begin{bmatrix} 1&2 \\​3 & 4 \end{bmatrix},\, \,B=\begin{bmatrix} 5&6 \\7 &8 \end{bmatrix}
$$
Applying Hadamard's multiplication, we get:
$$
A \odot B = \begin{bmatrix} 1*5 & 2*6 \\ 3*7 & 4*8 \end{bmatrix} = \begin{bmatrix} 5 & 12 \\ 21 & 32 \end{bmatrix}
$$
##### Exterior product (Wedge product)
This is used to create a matrix from a column vector and a row vector.

Example:
$$
\begin{bmatrix} a \\ b \\ c \end{bmatrix} \begin{bmatrix} d & e\end{bmatrix}=\begin{bmatrix} ad & ae \\ bd & be \\ cd & ce \end{bmatrix}
$$
The exterior product is quite different from the dot product because it produces a matrix instead of a scalar, and the two vectors in an exterior product can have **different dimensionalities**, whereas the two vectors in a dot product must have the same dimensionality.

It is denoted as $vw^T$ (remember that we assume the vectors are column-oriented; therefore, the exterior product involves multiplying a column by a row).

The notation for the product is $v^Tw$ and the exterior product is $vw^T$.

### Orthogonal Vector Decomposition

> Decomposing a vector or matrix means dividing that matrix into multiple simpler parts. 

Decompositions are used to reveal information that is "hidden" in a matrix or for data compression.

For example, we can decompose the number 42.01 into two parts: 42 and 0.01. 
Perhaps that 0.01 is noise that should be ignored, or perhaps the goal is to compress the data (the integer 42 requires less memory than the floating-point number 42.01).

Decomposition, therefore, **involves representing a mathematical object as the sum of simpler objects ($42 = 42 + 0.01$)**.

We can also decompose the number 42 into the product of the prime numbers 2, 3, and 7. This decomposition is called **prime factorization**.

The orthogonal decomposition of vectors leads directly to the **Gram-Schmidt** procedure and QR decomposition, which is frequently used when solving inverse problems in statistics.

To determine if one vector is orthogonal to another, we must find that they are perpendicular, which means that their dot product is zero.
$$
a^T(b-\beta a) =0
$$
To solve $\beta$ we can apply the distributive property of dot products. [1]
$$\begin{align*}
a^Tb-\beta a^Ta=0 \\
\beta a^Ta = a^Tb \\
\beta = \frac{a^Tb}{a^Ta}
\end{align*}
$$
This is orthogonal projection.

**But how does this relate to the orthogonal decomposition of vectors?**
The target vector will be $t$ and the reference vector will be $r$. The perpendicular component will be $t_{\perp_{r}}$ and the parallel component, denoted as $t_{\parallel_{r}}$.

A vector parallel to $r$ is any scaled version of $r$ parallel to $r$. Therefore, we find $t_{\parallel_{r}}$ by applying the orthogonal projection formula:
$$
t_{\parallel_{r}} = r \frac{t^Tr}{r^Tr}
$$
Here, unlike in equation [1], we want to calculate the scaled vector $\beta r$.

To find the perpendicular component, it's simpler. Since we already know that the two vector components must add up to the original target vector, we find it like this:
$$
\begin{align*}
t=t_{\perp _{r}}+t_{\parallel _{r}} \\
t_{\perp _{r}}=t-t_{\parallel _{r}}
\end{align*}
$$
In other words, we subtract the parallel component from the original vector, and the remainder is our perpendicular component.

