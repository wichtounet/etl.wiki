ETL is based on the concept of Smart Expression Templates.

Most expressions are evaluated completely lazily. For instance:

.. code:: c++

   vec = vec_a * 1.0 + 2.0 * vec_b * vec_c + vec_d / 3.3;

Will be implemented as if it was a simple for loop:

.. code:: c++

   for(std::size_t i = 0; i < vec.size(); ++i){
       vec[i] = vec_a[i] * 1.0 + 2.0 * vec_b[i] * vec_c[i] + vec_d[i] / 3.3;
   }

However, some expressions cannot be efficiently implemented in this manner. For instance, even though you could implement matrix multiplication lazily, it would not be efficient since matrix multiplication needs blocking in order to be implemented efficiently. In such cases, the result is computed using an optimized kernel prior to its access. In this code:

.. code:: cpp

   mat = mat_a * 2.3 + mat_b * mat_c;

The matrix multiplication is executed first and then the loop is executed to fill :code:`mat`.

Moreover, another problem arises with complex operations:

.. code:: cpp

   mat = (mat_a * 2.3) * (mat_b + mat_c);

If you were to implemented this as a simple matrix multiplication, you would have to compute several times the multiplication on the left and several times the addition on the right. Moreover, since you have expressions on the left and on the right, you won't be able to use an optimized kernel which all work directly on memory. In such cases, ETL generates a temporary for both lhs and rhs and then performs the matrix multiplication.
