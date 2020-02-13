# 1.1 Vector operations

## Norm 

The __norm__ or __magnitude__ of a vector is defined as:

\begin{equation*}
\left\|\vec{v}\right\| = \sqrt{\sum_n{v_n^2}}
\end{equation*}

This corresponds to the __length__ of the vector. 

## Unit vectors

A __unit vector__ is a vector of length one.

Any vector can be rescaled to have __unit length__ by dividing by its __norm__. In other words, a vector may be factorised into a product of its norm and a unit vector. 

\begin{equation*}
\hat{v} = \frac{\vec{v}}{\left\|\vec{v}\right\|} \qquad \qquad
\vec{v} = {\left\|\vec{v}\right\|}\:\hat{v}
\end{equation*}

## Dot product

The __inner product__, or __dot product,__ of two vectors is the sum of the pairwise product of their components:

\begin{equation*}
\begin{bmatrix}
a \\
b \\
c \\
\end{bmatrix} 
\bullet
\begin{bmatrix}
x \\
y \\
z \\
\end{bmatrix} = 
\begin{bmatrix}
ax \\
+ \\
by \\
+ \\
cz \\
\end{bmatrix} 
\end{equation*}

<br>

\begin{equation*}
\vec{v} \cdot \vec{w} \equiv \sum_{n}v_n w_n
\end{equation*}

Geometrically, this equates to:

\begin{equation*}
\vec{v} \cdot \vec{w} \equiv {\left\|\vec{v}\right\|} \; {\left\|\vec{w}\right\|} \cos{(\phi_{vw})}
\end{equation*}

Where $\phi_{vw}$ is the __angle__ between the two vectors.

This means the dot product is 0 when $\left\|\vec{v}\right\|$, $\left\|\vec{w}\right\|$ or $\cos{\phi}$ is 0. 

If we let $b$ equal the length of $\vec{w}$ projected onto $\vec{v}$, the cosine of the angle of the vectors can be defined as $\frac{b}{\left\|\vec{w}\right\|}$. This gives us:

\begin{equation*}
\vec{v} \cdot \vec{w} \equiv 
\frac{b}{\left\|\vec{w}\right\|}{\left\|\vec{v}\right\|} \; {\left\|\vec{w}\right\|}
\end{equation*}


<center>
<img src='img/dot_product.png'width="400">
</center>

In other words, the dot product of $\vec{v}$ with $\vec{w}$ can be visualised as the __component of $\vec{w}$ projected onto $\vec{v}$__, scaled by the length of $\vec{v}$. If $\vec{w}$ is the __unit vector__ $\hat{u}$, the it is simply the __projection__ of $\vec{v}$ onto the line in the direction of $\hat{u}$. 


<center>
<img src='img/dot_product_unit.png'width="400">
</center>


As a summary, the dot product of:
- two __perpendicular__ vectors = 0
- two __parallel__ vectors = the product of their norms
- a __vector with itself__ = the square of its norm

## Vector spaces

A __vector space__ is a collection of vectors closed under linear combination. All vector spaces include the __zero vector__. 

A __subspace__ is a vector space lying within another vector space - as in, a 2D plane in a 3D space.

A set of vectors __spans__ a vector space if one can write any vector in that space as a linear combination of the set. A set can be redundant - for example, if two of the vectors are scaled copies of each other. 

A set of vectors $\{ \vec{v}_1, \vec{v}_2, ..., \vec{v}_n\}$ is __linearly independent__ if and only if the only solution to the equation:

\begin{equation*}
\sum_{n} \alpha_n \vec{v}_n = 0
\end{equation*}

is $\alpha_n = 0$ for all $n$.

<center>
<img src='img/vector_spaces.png'width="350">
</center>

## Basis vectors

The __basis__ of a vector space is its __linearly independent spanning set__. This means the minimum set of vectors required to span it. 

In general, the vector space $R^N$ requires a basis of size $N$.

The __basis vectors__ define a set of coordinate axes for the space. They _need not be perpendicular_. 

The __standard basis__ is the set of __unit vectors__ that lie along the axes of the space:

\begin{equation*}
\hat{e}_1 = 
\begin{bmatrix}
1 \\
0 \\
0 \\
\vdots \\
0 \\
\end{bmatrix} , \;
\hat{e}_2 = 
\begin{bmatrix}
0 \\
1 \\
0 \\
\vdots \\
0 \\
\end{bmatrix} , \; \cdots \;
\hat{e}_N = 
\begin{bmatrix}
0 \\
0 \\
0 \\
\vdots \\
1 \\
\end{bmatrix}
\end{equation*}

<center>
<img src='img/basis_vector.png'width="400">
</center>

## Vectors as operators

It can be useful to interpret vectors as __operators__ applied to an input. For example, the dot product of a vector $\vec{v}$ with the vector:

\begin{equation*}
\vec{w} =  
\begin{bmatrix}
\frac{1}{N} \\
\frac{1}{N} \\
... \\
\frac{1}{N} \\
\end{bmatrix} 
\end{equation*}

gives the __average__ of the components of $\vec{v}$ . 


Likewise, the dot product with the vector:

\begin{equation*}
\vec{w} =  
\begin{bmatrix}
0 \\
-1 \\
1 \\
0 \\
\end{bmatrix} 
\end{equation*}

computes the __local difference__ between two components of $\vec{v}$ . 


\begin{equation*}
\end{equation*}


<br>

# 1.2  Linear Systems & Matrices 

## Linear systems

A __linear system__ $S$ transforms vectors in one vector space into those of another vector space, obeying the __principle of superposition__: 


\begin{equation*}
S \{ a \vec{v} + b \vec{w} \} = aS\{ \vec{v} \} + bS\{ \vec{w} \}
\end{equation*}

This means the __system response__ to any linear combination of vectors is equal to the linear combination of the responses to each of the vectors alone. 

In other words:
- multiplying by the scaling factor
- adding together
- then applying the linear transformation S

is equivalent to:
- applying the linear transformation S
- adding together
- then multiplying by the scaling factor

We can write any vector as a sum of its __standard basis vectors__ multiplied by a respective __weight__:

\begin{equation*}
\vec{v} = v_1 \hat{e}_1 + v_2 \hat{e}_2 + \cdots + v_n \hat{e}_N
\end{equation*}

Using the definition of linear systems, we can write:

\begin{equation*}
\begin{aligned}
S \{ \hat{v} \} & {}={} S \{ v_1 \hat{e}_1 + v_2 \hat{e}_2 + \cdots + v_n \hat{e}_N \} \\
& = v_1 S \{ \hat{e}_1 \} + v_2 S \{ \hat{e}_2 \} + \cdots + v_n S \{ \hat{e}_N \}
\end{aligned}
\end{equation*}

This means the __response of a linear system__ is a __weighted sum__ of the responses to each of the __standard basis vectors__. We can call these responses __response vectors__. The system is __fully characterised__ by this set of response vectors.

<center>
<img src='img/linear_system.png'width="450">
</center>

We can put the column vectors $S \{ \hat{e}_1 \}, S \{ \hat{e}_2 \} ... etc $ corresponding to the __responses__ to each basis vector into a __matrix__. This matrix is a complete representation of the linear system. 

\begin{equation*}
S = 
\begin{bmatrix}
\vdots & \vdots & & \vdots \\
\vdots & \vdots & & \vdots \\
S \{ \hat{e}_1 \} & S \{ \hat{e}_2 \} & \cdots &  S \{ \hat{e}_n \} \\
\vdots & \vdots & & \vdots \\
\vdots & \vdots & & \vdots \\
\end{bmatrix}
\end{equation*}

The __system response__ is a __weighted sum__ of the __columns__ of the matrix.

If we call the elements of the matrix $S_{rc}$, with $r$ indicating the __rows__ and $c$ the __columns__, the response $\vec{w}$ of the system to an input vector $\vec{v}$ has components:

\begin{equation*}
w_r = \sum_{c} S_{rc} v_c
\end{equation*}

In other words, each component of the output vector is a __dot product__ of the corresponding __row__ of the matrix with the input vector. 

\begin{equation*}
\vec{w} = S\cdot\vec{v}
\end{equation*}


\begin{equation*}
\begin{bmatrix}
w_1 \\
w_2 \\
w_3 \\
\vdots \\
w_n \\
\end{bmatrix} = 
\begin{bmatrix}
\vdots & \vdots & & \vdots \\
\vdots & \vdots & & \vdots \\
S \{ \hat{e}_1 \} & S \{ \hat{e}_2 \} & \cdots &  S \{ \hat{e}_n \} \\
\vdots & \vdots & & \vdots \\
\vdots & \vdots & & \vdots \\
\end{bmatrix}
\bullet
\begin{bmatrix}
v_1 \\
v_2 \\
v_3 \\
\vdots \\
v_n \\
\end{bmatrix}
\end{equation*}

For this to work, the __number of columns__ in the matrix $S$ must equal the __number of rows__ in the input vector $\vec{v}$. 

## Matrix transpose

The __transpose__ of a matrix is the same matrix but with the __rows and columns swapped__. 

\begin{equation*}
(S_{nm})^T = S_{mn}
\end{equation*}

A __symmetric matrix__ is a square matrix that is equal to its transpose. 

## Diagonal matrices 

A __diagonal matrix__ is one for which the only non-zero components can be along the diagonal.

\begin{equation*}
D = \left( \begin{array}{ccccc}
d_{11} &  &  &  &  \\
 & d_{22} &  &  &  \\
 &  & d_{33} & &  \\
 &  &  & \ddots &  \\
 &  &  &  & d_{nn} \\
\end{array} \right)
\end{equation*}

In general, the operation performed by diagonal matrices is to __stretch or compress__ vector spaces. The $n$th axis of the space is stretched or compressed by the amount in the $n$th diagonal element, $S_{nn}$. 


The diagonal matrix for which the diagonal components are all 1s is called the __identity matrix,__ $I$. As such, the identity matrix leaves the vector space untransformed. For example:


\begin{equation*}
I_4 = \begin{bmatrix}
1 & 0 & 0 & 0 \\
0 & 1 & 0 & 0 \\
0 & 0 & 1 & 0 \\
0 & 0 & 0 & 1 \\
\end{bmatrix}
\end{equation*}


### Inverse of diagonal matrices

The inverse of a __square diagonal matrix__ is a matrix in which each diagonal component is the scalar inverse of the original stretch factor: $\begin{equation*}
D_{nn}\;^{-1} = \frac{1}{D_{nn}}
\end{equation*}$.


\begin{equation*}
D^{-1} = \left( \begin{array}{ccccc}
\frac{1}{d_{11}} &  &  &  &  \\
 & \frac{1}{d_{22}} &  &  &  \\
 &  & \frac{1}{d_{33}} & &  \\
 &  &  & \ddots &  \\
 &  &  &  & \frac{1}{d_{nn}} \\
\end{array} \right)
\end{equation*}

Applying the diagonal matrix $D$ and its inverse $D^{-1}$ in succession restore the original vector, so the matrix product of the two is the identity matrix. 

\begin{equation*}
D^{-1}D = I
\end{equation*}

However, if an element of the diagonal is __zero__, it __cannot be inverted__. This is because, in multiplying a component of a vector space with 0, the associated axis is __annihilated__ during the transformation. 

### Nullspace and rank 

The set of axes "annihilated" by the matrix form the __nullspace__ of the matrix. In contrast, the set of axes the matrix can "reach" is the __column space__ of the matrix. Any matrix with __nonzero nullspace__ cannot be inverted.

The __rank__ of a matrix is the dimensionality of the column space. 

A matrix is __full rank__ if its rank is equal to at least the smaller of its two dimensions.

## Orthogonal matrices

An __orthogonal matrix__ is a __square matrix__ for which:

- every column is a _unit vector_
- every pair of columns is _orthogonal_


The __transpose__ of the orthogonal matrix $O$ multiplied by itself gives the identity matrix:

\begin{equation*}
O^{T}O = I
\end{equation*}

The operation performed by orthogonal matrices is a __generalised rotation__ vector spaces. It maps the original standard basis onto a new set of $N$ orthogonal axes. It does not stretch, compress or change the angle between two vectors in vector space.

To give a few examples:

$\begin{bmatrix}
1 & 0 \\
0 & -1
\end{bmatrix}$  Performs a __reflection__ across the x-axis.

<br>

$\begin{bmatrix}
0 & 0 & 0 & 1 \\
0 & 0 & 1 & 0 \\
1 & 0 & 0 & 0 \\
0 & 1 & 0 & 0
\end{bmatrix}$  Performs a __permutation__ of the coordinate axes.

<br> 

$\begin{bmatrix}
cos \theta & -sin \theta \\
sin \theta & cos \theta
\end{bmatrix}$  Performs a __rotation__ by $\theta$.

<br>

### Inverse of orthogonal matrices

The inverse of an orthogonal matrix is simply its __transpose__. Since $O$ corresponds to a generalised rotation of the space, $O^{T}$ corresponds to the same rotation in the opposite direction.

\begin{equation*}
O^{T} = O^{-1}
\end{equation*}

<br>

# 1.3  Singular Value Decomposition

Any matrix $M$ can be decomposed into a product of three matrices:

\begin{equation}
\underbrace{M}_{W \times D} = \underbrace{U}_{W \times W} \times \underbrace{\Sigma}_{W\times D} \times \underbrace{V^{T}}_{D \times D}
\end{equation}

such that $U$ and $V$ are __orthogonal matrices__ and $\Sigma$ is a __diagonal matrix__ with positive entries.

The diagonal elements of $\Sigma$ are called the __singular values__. 

This decomposition separates the action of $M$ into three components:

- $V^{T}$ -  __rotation__ of vector space into new coordinate system
- $\Sigma$ - __scaling__ of axes of vector space
- $U$ - __rotation__ of vector space into output coordinate system 


<center>
<img src='img/SVD_1.png'width="400">
</center>

The __nullspace__ of $M$ corresponds to the columns of $V$ which align with __zero singular values__. 

The __column space__ (also known as _range space_) of $M$ corresponds to the columns of $U$ which align with __non-zero singular values__.

The matrix is __invertible__ if and only if the _number of non-zero singular values_ equals the _number of columns of M._


\begin{equation*}
M = U \Sigma V^T = 
\begin{matrix}
\underbrace{\left[\begin{matrix} & \\ & \\ & \\ \vec u_1 & \dots & \vec u_r \\ & \\ & \\ & \\ \end{matrix}\right.}& 
    \underbrace{\left.\begin{matrix} & \\ & \\ & \\ \vec u_{r+1} & \dots &  \vec u_m \\ & \\ & \\ & \\ \end{matrix}\right]}\\
Col M & Nul M
    \end{matrix}
    \begin{bmatrix}
      \sigma_1 & & & & & \\
      & \sigma_2  & & &  & \\
      & & \ddots & & & \\
      & & & \sigma_r  & &  \\
      & & & & 0 & &  \\
      & & & & & \ddots & \\
      & & & & & & 0 
  \end{bmatrix}
  \begin{bmatrix}
    \vec v_1^T \\ \dots \\ \vec v_r^T \\ & \\
    \vec v_{r+1}^T \\ \dots \\ \vec v_n^T
  \end{bmatrix}
  \begin{matrix}
    \left.\vphantom{\begin{bmatrix}
       \vec v_1^T \\ \vec v_2^T \\ \dots \\ \vec v_r^T 
       \end{bmatrix}}\right\} Row M \\ 
    \left.\vphantom{\begin{bmatrix}
      \vect v_{r+1}^T \\ \dots \\ \vect v_n^T 
    \end{bmatrix}}\right\} Nul M
\end{matrix}
\end{equation*}


The __singular values__ in $\sigma_1, \sigma_2... etc$ are ordered according to size. The first singular value is the 'most significant'. This means we can choose a 'cut-off' and approximate the original matrix $M$ just using the first $n$ singular values.

\begin{equation*}
M = \sigma_1 \vec u_1 \vec v^{T}_1
+ \sigma_2 \vec u_2 \vec v^{T}_2 + \dots + \sigma_n \vec u_n \vec v^{T}_n
\end{equation*}


The SVD is __guaranteed to exist__ for any matrix. It is also __unique,__ outside of variations such as permuting or negating the components. 

The transformation of $M$ on a vector $\vec{x}$ can be seen as a weighted sum of the outer products of $U$ and $V^{T}$:

\begin{equation*}
M \vec{x} = \sum_{n} \sigma_n (\vec u_n \vec v^{T}_n) \vec{x}
\end{equation*}
