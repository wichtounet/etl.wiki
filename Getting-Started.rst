.. role:: cpp(code)
   :language: C++

The library is header-only and does not need to be built it at all,
you just have to include its header files.

Most of the headers are not meant to be included directly inside a problem. Here are the header that are made to be included:

* etl.hpp: Contains all the features of the library
* etl_light.hpp: Contains the basic features of the library (no matrix multiplication, no convolution, no FFT)

You should always include one of these headers in your program.
