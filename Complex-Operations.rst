.. role:: cpp(code)
   :language: C++

Matrix Multiplication
#####################

Multiplication between matrices (or vector-matrix or matrix-vector)
can be done simply by using the * operator:

.. code:: c++

    etl::fast_matrix<T, 2, 3> a = {1,2,3,4,5,6};
    etl::fast_matrix<T, 3, 2> b = {7,8,9,10,11,12};
    etl::fast_matrix<T, 2, 2> c = a * b;

If BLAS is configured, a BLAS implementation will be used for the
multiplication. Otherwise a custom blocked implementatio will be
used. ETL will always use the fastest implementation available.

An implementation of Strassen algorithm is also available:

.. code:: c++

    etl::fast_matrix<T, 2, 2> c = etl::strassen_mmul(a, b);

But it is nowhere as optimized as a BLAS operation.

Convolution
###########

Implementation of valid, same and full convolutions are available:

* conv_1d_valid, conv_2d_valid : Valid convolution of a vector or a matrix
* conv_1d_same, conv_2d_same : Same convolution of a vector or a matrix
* conv_1d_full, conv_2d_full : Full convolution of a vector or a matrix

  * fft_conv_1d_full, fft_conv_2d_full : Full convolution by using FFT
  * fast_conv_1d_full, fast_conv_2d_full : Full convolution by using FFT if available, normal implementation otherwise

ETL contains vectorized (SSE and AVX) implementations of each
convolution, that are used if ETL_VECTORIZE_IMPL has been defined.

Fast Fourrier Transform
#######################

If MKL library support is enabled, Fast Fourrier Transform
operations are available:

* fft_1d(vector) : Returns the FFT of the given vector
* ifft_1d(vector) : Returns Inverse FFT of the given vector
* fft_2d(matrix) : Returns the FFT of the given 2D matrix
* ifft_2d(matrix) : Returns Inverse FFT of the given 2D matrix

