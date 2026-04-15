

#### 1.5.2.5. Fixed-Point Performance Guide


Fixed-point emulation allows users to make performance and precision trade-offs for further acceleration.  For dynamic mantissa control, users are able to configure the automatic dynamic precision framework to use fewer or more bits than the accuracy of native FP64 requires with cublasSetFixedPointEmulationMantissaBitOffset().  Fixed mantissa control can be similarly tuned by increasing or decreasing the number of mantissa bits with cublasSetFixedPointEmulationMaxMantissaBitCount().


Due to the large fixed-point workspace requirements, asynchronous allocation is done with cudaMallocAsync().  In cases where not enough GEMMs are called to amortize the cost of memory allocation, or very frequent CUDA stream synchronization occurs, you can improve performance by:


- Reducing the number of CUDA stream synchronizations
- Managing your own memory and providing workspace with cublasSetWorkspace()
- Allowing the default memory pool to retain memory between synchronizations


