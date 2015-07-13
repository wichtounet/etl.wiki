.. role:: cpp(code)
   :language: C++

Classic element-wise operations can be done on vector and matrix as if it was
done on scalars. Matrices and vectors can also be added, subtracted, divided, ...
by scalars. These operations can be done on any ETL data structures.

.. code:: cpp

    etl::dyn_vector<double> a({1.0,2.0,3.0});
    etl::dyn_vector<double> b({3.0,2.0,1.0});

    etl::dyn_vector<double> c(1.4 * (a + b) / b + b + a / 1.2);

All the operations are only executed once the expression is evaluated to
construct the dyn_vector.
