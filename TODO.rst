This page contains a list of things that could be done to improve this project.

FFT
###

The FFT implementation is fairly good, yet several things could be improved
* A 6-point transform module could be added to improve performance further
* There is still room for improvememnt in some transform modules
* The Inverse FFT implementation should not make multiple pass over the data, this mean that the conjugate should be done directly inside the transform modules based on a function parameter

Matrix Multiplication
#####################

1. An efficient implementation for floats and complex numbers would greatly benefit the library.
1. An AVX-optimized matrix algorith for double would be of great value
1. Improving the standard multiplication algorithm for complex numbers would be a great improvement as well.

Misc
####

1. Finding ways to reduce the compile-time overhead of the library expressions
