.. role:: cpp(code)
   :language: C++

All ETL data structures are typed and can only contains one type of elements. While it can theoratically holds any type, it especially made for number types.

ETL is especially optimized for:

* :cpp:`float`
* :cpp:`double`

It is currently being optimized for:

* :cpp:`std::complex<float>`
* :cpp:`std::complex<double>`

It supports :cpp:`int` and :cpp:`long`.

If you find a standard type for which ETL data structures do not work as intended, please open an issue.
