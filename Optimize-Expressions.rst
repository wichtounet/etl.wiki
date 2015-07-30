ETL is able to optimize some expressions if it can be resolved more efficienty. For instance, this expression:

.. code:: c++

    C = (A * 1.0) * (B + 0.0);

is exactly the same as:

.. code:: c++

    C = A * B;

but the second version saves multiplications, additions and two matrix copy.

In ETL, you can use the function opt to ensure that an expression will be optimized prior to assignment:

.. code:: c++

    C = opt((A * 1.0) * (B + 0.0));

In this case, it will be execute directly as a matrix multiplication of A and B.

While the gain can be very noticeable, it has a great impact on compilation time. If you use opt on complex expressions, compilation of the expression can be more than one order of magnitude slower. This is why optimization is not enabled by default in ETL.
