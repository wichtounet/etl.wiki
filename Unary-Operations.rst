.. role:: cpp(code)
   :language: C++

Several unary operators are available. Each operation is performed
on every element of the vector or the matrix.

Available operators:

* log
* abs
* sign
* max/min
* noise: Add standard normal noise to each element
* logistic_noise: Add normal noise of mean zero and variance sigmoid(x) to each
  element
* exp
* softplus
* bernoulli

Operations can easily be combined:

.. code:: cpp

    etl::dyn_vector<double> a({1.0,2.0,3.0});
    etl::dyn_vector<double> c((log(a) + exp(a) >> sign(a)) / (1.0 + abs(a)));

Several transformations are also available:

* hflip: Flip the vector or the matrix horizontally
* vflip: Flip the vector or the matrix vertically
* fflip: Flip the vector or the matrix horizontally and verticaly. It is the
  equivalent of hflip(vflip(x))
* reshape: Interpet a vector as a matrix

Sub matrices
############

There are two ways to get a submatrix. For instance, if
:cpp:`matrix` is a `[3, 4, 5]` matrix:

* :cpp:`matrix(2)` returns the third sub matrix of size `[4, 5]`
* :cpp:`etl::sub(matrix, 2)` returns the third sub matrix of size
  `[4, 5]`

Both ways are doing exactly the same thing.

For 2D matrix, there are two more functions useful:

* :cpp:`etl::row(matrix, 2)` returns the third row of the matrix
* :cpp:`etl::col(matrix, 2)` returns the third column of the matrix

Sub matrices are implemented very efficiently, there are not copying
anything as long as they are not assigned to another data
structures. They are merely a sub view inside the matrix. Moreover,
they give direct memory access to the ETL operators, making for fast
operations. However, getting a column view of a row-major matrix
will not be efficient.

Transposition
#############

Transpose a matrix can be done in several ways:

* :cpp:`matrix.transpose_in_place()` directly transpose the matrix
* :cpp:`matrix.transpose()` returns an expression representing the
  transposition of the matrix
* :cpp:`transpose(matrix)` returns an expression representing the
  transposition of the matrix

sigmoid
#######

ETL has several implementations of sigmoid:

* :cpp:`sigmoid()` is the normal implementation with full precision
* :cpp:`fast_sigmoid()` is a good approximated version, faster than
  the standard version.
* :cpp:`hard_sigmoid()` is a bad approximation version, much faster
  than the other version.
