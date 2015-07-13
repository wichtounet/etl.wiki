.. role:: cpp(code)
   :language: C++

All binary and unary operations are applied lazily, only when they
are assigned to a concrete vector or matrix class.

In this code:

.. code:: c++

   etl::dyn_vector<double> a({1.0,2.0,3.0});
   auto expr = a >> a + (a / 2.0);
   std::cout << expr[1] << std::endl;

the expression will only be evaluated at the second position of the
vector, all the other parts of the expression will not be evaluated.

To force evaluation and assignment to a data structure, you can use
the :cpp:`etl::s(x)` function:

.. code:: c++

   etl::dyn_vector<double> a({1.0,2.0,3.0});
   auto value = etl::s(a >> a + (a / 2.0));
   std::cout << value[1] << std::endl;

In this case, the complete expression will be evaluated when
assigned into :cpp:`value`.

Exceptions
##########

Some expressions can not be completely done lazily. This is the case
for matrix multiplication, convolution and fast fourrier transform.
In those cases, the complete operation is done once for assignment.
If you want to use only some values without assignment, you'll have
to force the internal evaluation:

.. code:: c++

   etl::dyn_matrix<double> a(3, 3, 2.0);
   auto expr = a * a;
   etl::force(expr);
   std::cout << expr[1] << std::endl;
