ETL can be configured with several macros:

* ETL_VECTORIZE_IMPL: Enable vectorized implementations of some algorithms (convolution and the custom matrix multiplication algorithms).
* ETL_VECTORIZE_EXPR: Allow ETL to vectorize all expressions when possible (for instance r = a + b / c)
* ETL_VECTORIZE_FULL: Shortcut for ETL_VECTORIZE_IMPL and ETL_VECTORIZE_EXPR
* ETL_BLAS_MODE: Allow the use of a BLAS library (through cblas). A BLAS library must be installed.
* ETL_MKL_MODE: Allow the use of Intel MKL-specific functions to tune some algorithms (currently online inplace matrix transposition and FFT support)
* ETL_NO_TEMPORARY: Prevent expressions from creating temporaries. This is likely to slow down computations.
* ETL_ELEMENT_WISE_MULTIPLICATION: When this option is activated, a * b always results in element wise multiplication
* ETL_STRICT_DIV: Prevent ETL from using multiplication to perform division
* ETL_UNROLL_VECT: Tell ETL to unroll vectorized loops
* ETL_UNROLL_NON_VECT: Tell ETL to unroll normal loops
