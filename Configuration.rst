ETL can be configured with several macros: 

 * ETL_VECTORIZE: Enable vectorized implementations of some algorithms (convolution and the custom matrix multiplication algorithms). 
 * ETL_BLAS_MODE: Enable the use of a BLAS library (through cblas). A BLAS library must be installed.
 * ETL_MKL_MODE: Allow the use of Intel MKL-specific functions to tune some algorithms (currently online inplace matrix transposition)
 * ETL_NO_TEMPORARY: Prevent expressions from creating temporaries. This is likely to slow down computations.
 * ETL_ELEMENT_WISE_MULTIPLICATION: When this option is activated, a * b always results in element wise multiplication
