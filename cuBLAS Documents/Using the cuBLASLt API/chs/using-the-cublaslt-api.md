

# 3. Using the cuBLASLt API




## 3.1. General Description


The cuBLASLt library is a new lightweight library dedicated to GEneral Matrix-to-matrix Multiply (GEMM) operations with a new flexible API. This new library adds flexibility in matrix data layouts, input types, compute types, and also in choosing the algorithmic implementations and heuristics through parameter programmability.


Once a set of options for the intended GEMM operation are identified by the user, these options can be used repeatedly for different inputs. This is analogous to how cuFFT and FFTW first create a plan and reuse for same size and type FFTs with different input data.


> **Note**

Note
The cuBLASLt library does not guarantee the support of all possible sizes and configurations, however, since CUDA 12.2 update 2, the problem size limitations on m, n, and batch size have been largely resolved. The main focus of the library is to provide the most performant kernels, which might have some implied limitations. Some non-standard configurations may require a user to handle them manually, typically by decomposing the problem into smaller parts (see Problem Size Limitations).




### 3.1.1. Problem Size Limitations


There are inherent problem size limitations that are a result of limitations in CUDA grid dimensions.  For example, many kernels do not support batch sizes greater than 65535 due to a limitation on the *z* dimension of a grid.  There are similar restriction on the m and n values for a given problem.


In cases where a problem cannot be run by a single kernel, cuBLASLt will attempt to decompose the problem into multiple sub-problems and solve it by running the kernel on each sub-problem.


**There are some restrictions on cuBLASLt internal problem decomposition which are summarized below:**
: Amax computations are not supported.  This means that CUBLASLT_MATMUL_DESC_AMAX_D_POINTER and CUBLASLT_MATMUL_DESC_EPILOGUE_AUX_AMAX_POINTER must be left unset (see cublasLtMatmulDescAttributes_t)
All matrix layouts must have CUBLASLT_MATRIX_LAYOUT_ORDER set to CUBLASLT_ORDER_COL (see cublasLtOrder_t)
cuBLASLt will not partition along the n dimension when CUBLASLT_MATMUL_DESC_EPILOGUE is set to CUBLASLT_EPILOGUE_DRELU_BGRAD or CUBLASLT_EPILOGUE_DGELU_BGRAD (see cublasLtEpilogue_t)



To overcome these limitations, a user may want to partition the problem themself, launch kernels for each sub-problem, and compute any necessary reductions to combine the results.





### 3.1.2. Heuristics Cache


cuBLASLt uses heuristics to pick the most suitable matmul kernel for execution based on the problem sizes, GPU configuration, and other parameters. This requires performing some computations on the host CPU, which could take tens of microseconds. To overcome this overhead, it is recommended to query the heuristics once using [cublasLtMatmulAlgoGetHeuristic()](#cublasltmatmulalgogetheuristic) and then reuse the result for subsequent computations using [cublasLtMatmul()](#cublasltmatmul).


For the cases where querying heuristics once and then reusing them is not feasible, cuBLASLt implements a heuristics cache that maps matmul problems to kernels previously selected by heuristics. The heuristics cache uses an LRU-like eviction policy and is thread-safe.


The user can control the heuristics cache capacity with the `CUBLASLT_HEURISTICS_CACHE_CAPACITY` environment variable or with the [cublasLtHeuristicsCacheSetCapacity()](#cublasltheuristicscachesetcapacity) function which has higher precedence. The capacity is measured in number of entries and might be rounded up to the nearest multiple of some factor for performance reasons. Each entry takes about 360 bytes but is subject to change. The default capacity is 8192 entries.


> **Note**

Note
Setting capacity to zero disables the cache completely. This can be useful for workloads that do not have a steady state and for which cache operations may have higher overhead than regular heuristics computations.


> **Note**

Note
The cache is not ideal for performance reasons, so it is sometimes necessary to increase its capacity 1.5x-2.x over the anticipated number of unique matmul problems to achieve a nearly perfect hit rate.


See also: [cublasLtHeuristicsCacheGetCapacity()](#cublasltheuristicscachegetcapacity), [cublasLtHeuristicsCacheSetCapacity()](#cublasltheuristicscachesetcapacity).





### 3.1.3. cuBLASLt Logging


cuBLASLt logging mechanism can be enabled by setting the following environment variables before launching the target application:


- CUBLASLT_LOG_LEVEL=<level> where <level> is one of the following levels:



0 - Off - logging is disabled (default)
1 - Error - only errors will be logged
2 - Trace - API calls that launch CUDA kernels will log their parameters and important information
3 - Hints - hints that can potentially improve the application’s performance
4 - Info - provides general information about the library execution, may contain details about heuristic status
5 - API Trace - API calls will log their parameter and important information
- CUBLASLT_LOG_MASK=<mask>, where <mask> is a combination of the following flags:



0 - Off
1 - Error
2 - Trace
4 - Hints
8 - Info
16 - API Trace

For example, use CUBLASLT_LOG_MASK=5 to enable Error and Hints messages.
- CUBLASLT_LOG_FILE=<file_name>, where <file_name> is a path to a logging file.  The file name may contain %i, which will be replaced with the process ID. For example file_name_%i.log.


If `CUBLASLT_LOG_FILE` is not set, the log messages are printed to stdout.


Another option is to use the experimental cuBLASLt logging API. See:


[cublasLtLoggerSetCallback()](#cublasltloggersetcallback), [cublasLtLoggerSetFile()](#cublasltloggersetfile), [cublasLtLoggerOpenFile()](#cublasltloggeropenfile), [cublasLtLoggerSetLevel()](#cublasltloggersetlevel), [cublasLtLoggerSetMask()](#cublasltloggersetmask), [cublasLtLoggerForceDisable()](#cublasltloggerforcedisable)





### 3.1.4. Narrow Precision Data Types Usage


What we call here *narrow precision data types* were first introduced as 8-bit floating point data types (FP8) with Ada and Hopper GPUs (compute capability 8.9 and above), and were designed to further accelerate matrix multiplications. There are two types of FP8 available:


- CUDA_R_8F_E4M3 is designed to be accurate at a smaller dynamic range than half precision. The E4 and M3 indicate a 4-bit exponent and a 3-bit mantissa respectively. For more details, see __nv__fp8_e4m3.
- CUDA_R_8F_E5M2 is designed to be accurate at a similar dynamic range as half precision. The E5 and M2 indicate a 5-bit exponent and a 2-bit mantissa respectively. For more information see __nv__fp8_e5m2.


> **Note**

Note
Unless otherwise stated, FP8 refers to both CUDA_R_8F_E4M3 and CUDA_R_8F_E5M2.


With the Blackwell GPUs (compute capability 10.0 and above), cuBLAS adds support for 4-bit floating data type (FP4) `CUDA_R_4F_E2M1`. The E2 and M1 indicate a 2-bit exponent and a 1-bit mantissa respectively. For more details, see [__nv_fp4_e2m1](https://docs.nvidia.com/cuda/cuda-math-api/cuda_math_api/struct____nv__fp4__e2m1.html).


In order to maintain accuracy, data in narrow precisions needs to be scaled or dequantized before and potentially quantized after computations. cuBLAS provides several modes how the scaling factors are applied, defined in [cublasLtMatmulMatrixScale_t](#cublasltmatmulmatrixscale-t) and configured via the `CUBLASLT_MATMUL_DESC_{X}_SCALE_MODE` attributes (here `X` stands for `A`, `B`, `C`, `D`, `D_OUT`, or `EPILOGUE_AUX`; see [cublasLtMatmulDescAttributes_t](#cublasltmatmuldescattributes-t)). The scaling modes overview is given in the next table, and more details are available in the subsequent sections.


| Mode | Supported compute capabilities | Tensor values data type | Scaling factors data type | Scaling factor layout |
| --- | --- | --- | --- | --- |
| Tensorwide scaling | 8.9+ | CUDA_R_8F_E4M3 / CUDA_R_8F_E5M2 | CUDA_R_32F 1 | Scalar |
| Outer vector scaling | 9.0 | CUDA_R_8F_E4M3 / CUDA_R_8F_E5M2 | CUDA_R_32F | Vector |
| 128-element 1D block scaling | 9.0 | CUDA_R_8F_E4M3 / CUDA_R_8F_E5M2 | CUDA_R_32F | Tensor |
| 128x128-element 2D block scaling | 9.0 | CUDA_R_8F_E4M3 / CUDA_R_8F_E5M2 | CUDA_R_32F | Tensor |
| 32-element 1D block scaling | 10.0+ | CUDA_R_8F_E4M3 / CUDA_R_8F_E5M2 | CUDA_R_8F_UE8M0 2 | Tiled tensor 4 |
| 16-element 1D block scaling | 10.0+ | CUDA_R_4F_E2M1 | CUDA_R_8F_UE4M3 3 | Tiled tensor 4 |
| Experimental: Per-batch Tensorwide scaling | 10.0+ | CUDA_R_8F_E4M3 / CUDA_R_8F_E5M2 | CUDA_R_32F 1 | Array of pointers |


**NOTES:**


**1(1,2)**
: Scaling factors that have CUDA_R_32F data type can be negative and are applied as-is without taking their absolute value first.

**2**
: CUDA_R_8F_UE8M0 is an 8-bit unsigned exponent-only floating data type. For more information see __nv_fp8_e8m0.

**3**
: CUDA_R_8F_UE4M3 is an unsigned version of CUDA_R_E4M3.  The sign bit is ignored, so this enumerant is provided for convenience.

**4(1,2)**
: See 1D Block Scaling Factors Layout for more details.



> **Note**

Note
Scales are only applicable to narrow precisions matmuls. If any scale is set for a non-narrow precisions matmul, cuBLAS will return an error. Furthermore, scales are generally only supported for narrow precision tensors. If the corresponding scale is set for a non-narrow precisions tensor, cuBLAS will return an error. The one exception is that the C tensor is allowed to have a scale for non-narrow data types with tensorwide scaling mode.


> **Note**

Note
Only Tensorwide scaling is supported when cublasLtBatchMode_t of any matrix is set to CUBLASLT_BATCH_MODE_POINTER_ARRAY.




#### 3.1.4.1. Tensorwide Scaling For FP8 Data Types


Tensorwide scaling is enabled when `CUBLASLT_MATMUL_DESC_{X}_SCALE_MODE` attributes (here `X` stands for `A`, `B`, `C`, `D`, or `EPILOGUE_AUX`; see [cublasLtMatmulDescAttributes_t](#cublasltmatmuldescattributes-t)) for all FP8-precision tensors are set to `CUBLASLT_MATMUL_MATRIX_SCALE_SCALAR_32F` (this is the default value for FP8 tensors). In such case, the matmul operation in cuBLAS is defined in the following way (assuming, for exposition, that all tensors are using an FP8 precision):



$$D = scale_D \cdot (\alpha \cdot scale_A \cdot scale_B \cdot \text{op}(A) \text{op}(B) + \beta \cdot scale_C \cdot C).$$
Here \(A\), \(B\), and \(C\) are input tensors, and \(scale_A\), \(scale_B\), \(scale_C\), \(scale_D\), \(\alpha\), and \(\beta\) are input scalars. This differs from the other matrix multiplication routines because of this addition of scaling factors for each matrix. The \(scale_A\), \(scale_B\), and \(scale_C\) are used for de-quantization, and \(scale_D\) is used for quantization. Note that all the scaling factors are applied multiplicatively. This means that sometimes it is necessary to use a scaling factor or its reciprocal depending on the context in which it is applied. For more information on FP8, see [cublasLtMatmul()](#cublasltmatmul) and [cublasLtMatmulDescAttributes_t](#cublasltmatmuldescattributes-t).


For such matrix multiplications, epilogues and the absolute maximums of intermediate values are computed as follows:



$$\begin{split}Aux_{temp} & = \alpha \cdot scale_A \cdot scale_B \cdot \text{op}(A) \text{op}(B) + \beta \cdot scale_C \cdot C + bias, \\
D_{temp} & = \mathop{Epilogue}(Aux_{temp}), \\
amax_{D} & = \mathop{absmax}(D_{temp}), \\
amax_{Aux} & = \mathop{absmax}(Aux_{temp}), \\
D & = scale_D * D_{temp}, \\
Aux & = scale_{Aux} * Aux_{temp}. \\\end{split}$$
Here \(Aux\) is an auxiliary output of matmul consisting of the values that are passed to an epilogue function like GELU, \(scale_{Aux}\) is an optional scaling factor that can be applied to \(Aux\), and \(amax_{Aux}\) is the maximum absolute value in \(Aux\) before scaling. For more information, see attributes `CUBLASLT_MATMUL_DESC_AMAX_D_POINTER` and `CUBLASLT_MATMUL_DESC_EPILOGUE_AUX_AMAX_POINTER` in [cublasLtMatmulDescAttributes_t](#cublasltmatmuldescattributes-t).


> **Note**

Note
As indicated in equation above, bias is applied before calculating \(Aux_{temp}\).





#### 3.1.4.2. Experimental: Per-batch Tensorwide Scaling For FP8 Data Types


Per-batch Tensorwide scaling is enabled when `CUBLASLT_MATMUL_DESC_{X}_SCALE_MODE` attributes (here `X` stands for `A`, `B`, `C`, `D`, or `EPILOGUE_AUX`; see [cublasLtMatmulDescAttributes_t](#cublasltmatmuldescattributes-t)) for all FP8-precision tensors are set to `CUBLASLT_MATMUL_MATRIX_SCALE_PER_BATCH_SCALAR_32F`.


Per-batch Tensorwide scaling is a variant of tensorwide scaling except that each matrix in the batch has its own scaling factor.


When using per-batch Tensorwide scaling, the \(scale_A\), \(scale_B\), \(scale_C\), \(scale_D\), and \(scale_{Aux}\) must be device arrays of pointers of length `CUBLASLT_MATRIX_LAYOUT_BATCH_COUNT`.


> **Note**

Note
Per-batch Tensorwide scaling is only supported when cublasLtBatchMode_t of all matrices is set to CUBLASLT_BATCH_MODE_GROUPED.





#### 3.1.4.3. Outer Vector Scaling for FP8 Data Types


This scaling mode (also known as channelwise or rowwise scaling) is a refinement of the tensorwide scaling. Instead of multiplying a matrix by a single scalar, a scaling factor is associated with each row of \(A\) and each column of \(B\):



$$D_{ij} = \alpha \cdot scale_A^i \cdot scale_B^j \sum_{l=1}^k a_{il}\cdot b_{lj} + \beta \cdot scale_C \cdot C_{ij}.$$
Notably, \(scale_D\) is not supported because the only supported precisions for \(D\) are `CUDA_R_16F`, `CUDA_R_16BF`, and `CUDA_R_32F`.


To enable outer vector scaling, the `CUBLASLT_MATMUL_DESC_A_SCALE_MODE` and `CUBLASLT_MATMUL_DESC_B_SCALE_MODE` attributes, must be set to `CUBLASLT_MATMUL_MATRIX_SCALE_OUTER_VEC_32F`, while all the other scaling modes must not be modified.


When using this scaling mode, the \(scale_A\) and \(scale_B\) must be vectors of length \(M\) and \(N\) respectively.





#### 3.1.4.4. 16/32-Element 1D Block Scaling for FP8 and FP4 Data Types


1D block scaling aims to overcome limitations of having a single scalar to scale a whole tensor. It is described in more details in the [OCP MXFP](https://www.opencompute.org/documents/ocp-microscaling-formats-mx-v1-0-spec-final-pdf) specification, so we give just a brief overview here. Block scaling means that elements within the same 16- or 32-element block of adjacent values are assigned a shared scaling factor.


Currently, block scaling is supported for FP8-precision and FP4-precision tensors and mixing precisions is not supported. To enable block scaling, the `CUBLASLT_MATMUL_DESC_{X}_SCALE_MODE` attributes (here `X` stands for `A`, `B`, `C`, `DOUT`, or `EPILOGUE_AUX`; see [cublasLtMatmulDescAttributes_t](#cublasltmatmuldescattributes-t)) must be set to `CUBLASLT_MATMUL_MATRIX_SCALE_VEC32_UE8M0` for all FP8-precision tensors or to `CUBLASLT_MATMUL_MATRIX_SCALE_VEC16_UE4M3` for all FP4-precision tensors.


With block scaling, the matmul operation in cuBLAS is defined in the following way (assuming, for exposition, that all tensors are using a narrow precision). We loosely follow the OCP MXFP specification notation.


First, a scaled block (or an MX-compliant format vector in the OCP MXFP specification) is a tuple \(x = \left(S^x, \left[x^i\right]_{i=1}^k\right)\), where \(S^x\) is a shared scaling factor, and each \(x^i\) is stored using an FP8 or FP4 data type.


A dot product of two scaled blocks \(x = \left(S^x, \left[x^i\right]_{i=1}^{k}\right)\) and \(y = \left(S^y, \left[y^i\right]_{i=1}^{k}\right)\) is defined as follows:



$$Dot(x, y) = S^x S^y \cdot \sum_{i=1}^{k} x^i y^i.$$
For a sequence of \(n\) blocks \(X = \{x_j\}_{j=1}^n\) and \(Y = \{y_j\}_{j=1}^n\), the generalized dot product is defined as:



$$DotGeneral(X, Y) = \sum_{j=1}^n Dot(x_j, y_j).$$
The generalized dot product can be used to define the matrix multiplication by combining together one scaling factor per \(k\) elements of \(A\) and \(B\) in the \(K\) dimension (assuming, for simplicity, that \(K\) is divisible by \(k\) without a remainder):



$$\begin{split}L & = \frac{K}{k}, \\
A_i & = \left\{{scale_A}_{i,b}, \left[A_{i,(b-1)k+l}\right]_{l=1}^{k}\right\}_{b=1}^L, \\
B_j & = \left\{{scale_B}_{i,b}, \left[B_{(b-1)k+l,j}\right]_{l=1}^{k}\right\}_{b=1}^L, \\
(\left\{scale_A, A\right\} \times \left\{scale_B, B\right\})_{i,j} & = DotGeneral(A_i, B_j).\end{split}$$
Now, the full matmul can be written as:



$$\left\{scale_D^{out}, D\right\} = Quantize\left(scale_D^{in}\left(\alpha \cdot \left\{scale_A, \text{op}(A)\right\} \times \left\{scale_B, \text{op}(B)\right\} + \beta \cdot Dequantize(\left\{scale_C, C\right\})\right)\right).$$
The \(Quantize\) is explained in the [1D Block Quantization](#d-block-quantization) section, and \(Dequantize\) is defined as:



$$Dequantize\left(\left\{scale_C, C\right\})\right)_{i,j} = {scale_C}_{i/k,j} \cdot C_{i,j}.$$
> **Note**

Note
In addition to \(scale_D^{out}\) that is computed during quantization, there is also an input scalar tensor-wide scaling factor \(scale_D^{in}\) for \(D\) that is available only when scaling factors use the CUDA_R_8F_UE4M3 data type. It is used to ‘compress’ computed values prior to quantization.




3.1.4.4.1. 1D Block Quantization

Consider a single block of \(k\) elements of \(D\) in the \(M\) dimension: \(D^b_{fp32} = \left[d^i_{fp32}\right]_{i=1}^k\). Quantization of partial blocks is performed as if the missing values are zero. Let \(Amax(DType)\) be the maximal value representable in the destination precision.


The following computations steps are common to all combinations of output and scaling factors data types.


1. Compute the block absolute maximum value \(Amax(D^b_{fp32}) = max(\{|d_i|\}_{i=1}^k)\).
2. Compute the block scaling factor in single precision as \(S^b_{fp32} = \frac{Amax(D^b_{fp32})}{Amax(DType)}\).


**Computing scaling and conversion factors for FP8 with UE8M0 scales**


> **Note**

Note
RNE rounding is assumed unless noted otherwise.


Computations consist of the following steps:


1. Extract the block scaling factor exponent without bias adjustment as an integer \(E^b_{int}\) and mantissa as a fixed point number \(M^b_{fixp}\) from \(S^b_{fp32}\) (the actual implementation operates on bit representation directly).
2. Round the block exponent up keeping it within the range of values representable in UE8M0: \(E^b_{int} = \left\{\begin{array}{ll} E^b_{int} + 1, & \text{if } S^b_{fp32} \text{ is a normal number and }  E^b_{int} < 254 \text{ and } M^b_{fixp} > 0 \\ E^b_{int} + 1, & \text{if } S^b_{fp32} \text{is a denormal number and } M^b_{fixp} > 0.5, \\ E^b_{int}, & \text{otherwise.} \end{array}\right.\)
3. Compute the block scaling factor as \(S^b_{ue8m0} = 2^{E^b_{int}}\). Note that UE8M0 data type has exponent bias of 127.
4. Compute the block conversion factor \(R^b_{fp32} = \frac{1}{fp32(S^b_{ue8m0})}\).


> **Note**

Note
The algorithm above differs from the OCP MXFP suggested rounding scheme.


**Computing scaling and conversion factors for FP4 with UE4M3 scales**


Here we assume that the algorithm is provided with a precomputed input tensorwide scaling factor \(scale_D^{in}\) which in general case is computed as



$$scale_D^{in} = \frac{Amax(e2m1) \cdot Amax(e4m3)}{Amax(D_{temp})},$$
where \(Amax(D_{temp})\) is a global absolute maximum of matmul results before quantization. Since computing this value requires knowing the result of the whole computation, an approximate value from e.g. the previous iteration is used in practice.


Computations consist of the following steps:


1. Compute the narrow precision value of the block scaling factor \(S^b_{e4m3} = e4m3(S^b_{fp32})\).
2. Compute the block conversion factor \(R^b_{fp32} = \frac{1}{fp32(S^b_{e4m3})}\).


**Applying conversion factors**


For each \(i = 1 \ldots k\), compute \(d^i = DType(d^i_{fp32} \cdot R^b_{fp32})\). The resulting quantized block is \(\left(S^b, \left[d^i\right]_{i=1}^k\right)\), where \(S^b\) is \(S^b_{ue8m0}\) for FP8 with UE8M0 scaling factors, and \(S^b_{ue4m3}\) for FP4 with UE4M3 scaling factors.





3.1.4.4.2. 1D Block Scaling Factors Layout

Scaling factors are stored using a tiled layout. The following figure shows how each 128x4 tile is laid out in memory. The offset in memory is increasing from left to right, and then from top to bottom.





The following pseudocode can be used to translate from `inner` (K for A and B, and M for C or D) and `outer` (M for A, and N for B, C and D) indices to linear `offset` within a tile and back:



```c++

// Indices -> offset
offset = (outer % 32) * 16 + (outer / 32) * 4 + inner

// Offset -> Indices
outer = ((offset % 16) / 4) * 32 + (offset / 16)
inner = (offset % 4)


```


A single tile of scaling factors is applied to a 128x64 block when the scaling mode is `CUBLASLT_MATMUL_MATRIX_SCALE_VEC16_UE4M3` and to a 128x128 block when it is `CUBLASLT_MATMUL_MATRIX_SCALE_VEC32_UE8M0`.


Multiple blocks are arranged in the row-major manner. The next picture shows an example. The offset in memory is increasing from left to right, and then from top to bottom.





In general, for a scaling factors tensor with `sf_inner_dim` scaling factors per row, offset of a block with top left coordinate `(sf_outer, sf_inner)` (using the same correspondence to matrix coordinates as noted above) can be computed using the following pseudocode:



```c++

// Indices -> offset
//   note that sf_inner is a multiple of 4 due to the tiling layout
offset = (sf_inner + sf_outer * sf_inner_dim) * 128


```


> **Note**

Note
Starting addresses of scaling factors must be 16B aligned.


> **Note**

Note
Note that the layout described above does not allow transposition. This means that even though the input tensors can be transposed, the layout of scaling factors does not change.


> **Note**

Note
Note that when tensor dimensions are not multiples of the tile size above, it is necessary to still allocate full tile for storage and fill out of bounds values with zeroes. Moreover, when writing output scaling factors, kernels may write additional zeroes, so it is best to not make any assuptions regarding the persistence of out of bounds values.






#### 3.1.4.5. 128-element 1D and 128x128 2D Block Scaling For FP8 Data Types


These two scaling modes apply principles of the scaling approach described [16/32-Element 1D Block Scaling for FP8 and FP4 Data Types](#d-block-scaling-for-fp8-and-fp4-data-types) to the Hopper GPU architecture. However, here the scaling data type is `CUDA_R_32F`, and different scaling modes can be used for \(A\) and \(B\), and the only supported precisions for \(D\) are `CUDA_R_16F`, `CUDA_R_16BF`, and `CUDA_R_32F`.


To enable this scaling mode, the `CUBLASLT_MATMUL_DESC_{X}_SCALE_MODE` attributes (here `X` stands for `A` or `B`), must be set to `CUBLASLT_MATMUL_MATRIX_SCALE_VEC128_32F` or `CUBLASLT_MATMUL_MATRIX_SCALE_BLK128x128_32F`, while all the other scaling modes must not be modified. The following table shows supported combinations:


| CUBLASLT_MATMUL_DESC_A_SCALE_MODE | CUBLASLT_MATMUL_DESC_B_SCALE_MODE | Supported? |
| --- | --- | --- |
| CUBLASLT_MATMUL_MATRIX_SCALE_VEC128_32F | CUBLASLT_MATMUL_MATRIX_SCALE_VEC128_32F | Yes |
| CUBLASLT_MATMUL_MATRIX_SCALE_VEC128_32F | CUBLASLT_MATMUL_MATRIX_SCALE_BLK128x128_32F | Yes |
| CUBLASLT_MATMUL_MATRIX_SCALE_BLK128x128_32F | CUBLASLT_MATMUL_MATRIX_SCALE_VEC128_32F | Yes |
| CUBLASLT_MATMUL_MATRIX_SCALE_BLK128x128_32F | CUBLASLT_MATMUL_MATRIX_SCALE_BLK128x128_32F | No |


Using the notation from the [16/32-Element 1D Block Scaling for FP8 and FP4 Data Types](#d-block-scaling-for-fp8-and-fp4-data-types), we can define sequences of scaled blocks for the \(i\)-th row of \(A\) in the following way:



$$\begin{split}L & = \lceil \frac{K}{128} \rceil, \\
A^{128}_i & = \left\{{scale_A}_{i,b}, \left[A_{i,(b-1)128+l}\right]_{l=1}^{128}\right\}_{b=1}^L, \text{(this is the 128-element 1D block scaling)} \\
\\
p & = \lceil \frac{i}{128} \rceil, \\
A^{128 \times 128}_i & = \left\{{scale_A}_{p,b}, \left[A_{i,(b-1)128+l}\right]_{l=1}^{128}\right\}_{b=1}^L. \text{(this is the 128x128-element 2D block scaling)} \\\end{split}$$
Definitions for \(B\) are similar. The matmul is then defined as in [16/32-Element 1D Block Scaling for FP8 and FP4 Data Types](#d-block-scaling-for-fp8-and-fp4-data-types) with the notable difference that when using the 2D block scaling a single scaling factor is used for the whole 128x128 block of elements.




3.1.4.5.1. Scaling factors layouts

> **Note**

Note
Starting addresses of scaling factors must be 16B aligned.


> **Note**

Note
\(M\) and \(N\) must be multiples of 4.


Then for the `CUBLASLT_MATMUL_MATRIX_SCALE_VEC128_32F` scaling mode, the scaling factors are:


- \(M\)-major for \(A\) with shape \(M \times L\) (\(M\)-major means that elements along the \(M\) dimension are contiguous in memory),
- \(N\)-major for \(B\) with shape \(N \times L\).


For the `CUBLASLT_MATMUL_MATRIX_SCALE_BLK128x128_32F` scaling mode, the scaling factors are \(K\)-major and the stride between the consecutive columns must be a multiple of 4. Let \(L_4 = \lceil L \rceil_4\), where the \(\lceil \cdot \rceil_4\) denotes rounding up to the nearest multiple of 4. Then


- for \(A\), the shape of the scaling factors is \(L_4 \times \lceil \frac{M}{128} \rceil\),
- for \(B\), the shape of the scaling factors is \(L_4 \times \lceil \frac{N}{128} \rceil\).







### 3.1.5. Disabling CPU Instructions


As mentioned in the [Heuristics Cache](#heuristics-cache) section, cuBLASLt heuristics perform some compute-intensive operations on the host CPU.
To speed-up the operations, the implementation detects CPU capabilities and may use special instructions, such as Advanced Vector Extensions (AVX) on x86-64 CPUs.
However, in some rare cases this might be not desirable. For instance, using advanced instructions may result in CPU running at a lower frequency, which would affect performance of the other host code.


The user can optionally instruct the cuBLASLt library to not use some CPU instructions with the `CUBLASLT_DISABLE_CPU_INSTRUCTIONS_MASK` environment variable or with the [cublasLtDisableCpuInstructionsSetMask()](#cublasltdisablecpuinstructionssetmask) function which has higher precedence.
The default mask is 0, meaning that there are no restrictions.


Please check [cublasLtDisableCpuInstructionsSetMask()](#cublasltdisablecpuinstructionssetmask) for more information.







cuBLASLt 日志记录机制可以通过在启动目标应用程序之前设置以下环境变量来启用：

- `CUBLASLT_LOG_LEVEL=<level>`，其中 `<level>` 为以下级别之一：

  - 0 - 关闭 - 日志记录被禁用（默认）
  - 1 - 错误 - 仅记录错误
  - 2 - 跟踪 - 启动 CUDA 内核的 API 调用将记录其参数和重要信息
  - 3 - 提示 - 可能提高应用程序性能的提示
  - 4 - 信息 - 提供有关库执行的一般信息，可能包含启发式状态详情
  - 5 - API 跟踪 - API 调用将记录其参数和重要信息

- `CUBLASLT_LOG_MASK=<mask>`，其中 `<mask>` 是以下标志的组合：

  - 0 - 关闭
  - 1 - 错误
  - 2 - 跟踪
  - 4 - 提示
  - 8 - 信息
  - 16 - API 跟踪

  例如，使用 `CUBLASLT_LOG_MASK=5` 可启用错误和提示消息。

- `CUBLASLT_LOG_FILE=<file_name>`，其中 `<file_name>` 是日志文件的路径。文件名可以包含 `%i`，它将被替换为进程 ID。例如 `file_name_%i.log`。

如果未设置 `CUBLASLT_LOG_FILE`，日志消息将打印到标准输出。

另一种选择是使用实验性的 cuBLASLt 日志记录 API。请参阅：

`cublasLtLoggerSetCallback()`、`cublasLtLoggerSetFile()`、`cublasLtLoggerOpenFile()`、`cublasLtLoggerSetLevel()`、`cublasLtLoggerSetMask()`、`cublasLtLoggerForceDisable()`
## 3.2. cuBLASLt Code Examples


Please visit [https://github.com/NVIDIA/CUDALibrarySamples/tree/main/cuBLASLt](https://github.com/NVIDIA/CUDALibrarySamples/tree/main/cuBLASLt) for updated code examples.





## 3.3. cuBLASLt Datatypes Reference




##### 3.3.1. cublasLtClusterShape_t
##### 3.3.2. cublasLtEpilogue_t
##### 3.3.3. cublasLtHandle_t
##### 3.3.4. cublasLtLoggerCallback_t
##### 3.3.5. cublasLtMatmulAlgo_t
##### 3.3.6. cublasLtMatmulAlgoCapAttributes_t
##### 3.3.7. cublasLtMatmulAlgoConfigAttributes_t
##### 3.3.8. cublasLtMatmulDesc_t
##### 3.3.9. cublasLtMatmulDescAttributes_t
##### 3.3.10. cublasLtMatmulHeuristicResult_t
##### 3.3.11. cublasLtMatmulInnerShape_t
##### 3.3.12. cublasLtMatmulPreference_t
##### 3.3.13. cublasLtMatmulPreferenceAttributes_t
##### 3.3.14. cublasLtMatmulSearch_t
##### 3.3.15. cublasLtMatmulTile_t
##### 3.3.16. cublasLtMatmulStages_t
##### 3.3.17. cublasLtNumericalImplFlags_t
##### 3.3.18. cublasLtMatrixLayout_t
##### 3.3.19. cublasLtMatrixLayoutAttribute_t
##### 3.3.20. cublasLtIntegerWidth_t
##### 3.3.21. cublasLtMatrixTransformDesc_t
##### 3.3.22. cublasLtMatrixTransformDescAttributes_t
##### 3.3.23. cublasLtOrder_t
##### 3.3.24. cublasLtPointerMode_t
##### 3.3.25. cublasLtPointerModeMask_t
##### 3.3.26. cublasLtReductionScheme_t
##### 3.3.27. cublasLtMatmulMatrixScale_t
##### 3.3.28. cublasLtBatchMode_t
##### 3.3.29. cublasLtEmulationDesc_t
##### 3.3.30. cublasLtEmulationDescAttributes_t
### 3.3.1. cublasLtClusterShape_t


[cublasLtClusterShape_t](#cublasltclustershape-t) is an enumerated type used to configure thread block cluster dimensions. Thread block clusters add an optional hierarchical level and are made up of thread blocks. Similar to thread blocks, these can be one, two, or three-dimensional. See also [Thread Block Clusters](https://docs.nvidia.com/cuda/cuda-c-programming-guide/index.html#thread-block-clusters).


| Value | Description |
| --- | --- |
| CUBLASLT_CLUSTER_SHAPE_AUTO | Cluster shape is automatically selected. |
| CUBLASLT_CLUSTER_SHAPE_1x1x1 | Cluster shape is 1 x 1 x 1. |
| CUBLASLT_CLUSTER_SHAPE_1x2x1 | Cluster shape is 1 x 2 x 1. |
| CUBLASLT_CLUSTER_SHAPE_1x4x1 | Cluster shape is 1 x 4 x 1. |
| CUBLASLT_CLUSTER_SHAPE_2x1x1 | Cluster shape is 2 x 1 x 1. |
| CUBLASLT_CLUSTER_SHAPE_2x2x1 | Cluster shape is 2 x 2 x 1. |
| CUBLASLT_CLUSTER_SHAPE_2x4x1 | Cluster shape is 2 x 4 x 1. |
| CUBLASLT_CLUSTER_SHAPE_4x1x1 | Cluster shape is 4 x 1 x 1. |
| CUBLASLT_CLUSTER_SHAPE_4x2x1 | Cluster shape is 4 x 2 x 1. |
| CUBLASLT_CLUSTER_SHAPE_4x4x1 | Cluster shape is 4 x 4 x 1. |
| CUBLASLT_CLUSTER_SHAPE_1x8x1 | Cluster shape is 1 x 8 x 1. |
| CUBLASLT_CLUSTER_SHAPE_8x1x1 | Cluster shape is 8 x 1 x 1. |
| CUBLASLT_CLUSTER_SHAPE_2x8x1 | Cluster shape is 2 x 8 x 1. |
| CUBLASLT_CLUSTER_SHAPE_8x2x1 | Cluster shape is 8 x 2 x 1. |
| CUBLASLT_CLUSTER_SHAPE_1x16x1 | Cluster shape is 1 x 16 x 1. |
| CUBLASLT_CLUSTER_SHAPE_16x1x1 | Cluster shape is 16 x 1 x 1. |
| CUBLASLT_CLUSTER_SHAPE_1x3x1 | Cluster shape is 1 x 3 x 1. |
| CUBLASLT_CLUSTER_SHAPE_1x5x1 | Cluster shape is 1 x 5 x 1. |
| CUBLASLT_CLUSTER_SHAPE_1x6x1 | Cluster shape is 1 x 6 x 1. |
| CUBLASLT_CLUSTER_SHAPE_1x7x1 | Cluster shape is 1 x 7 x 1. |
| CUBLASLT_CLUSTER_SHAPE_1x9x1 | Cluster shape is 1 x 9 x 1. |
| CUBLASLT_CLUSTER_SHAPE_1x10x1 | Cluster shape is 1 x 10 x 1. |
| CUBLASLT_CLUSTER_SHAPE_1x11x1 | Cluster shape is 1 x 11 x 1. |
| CUBLASLT_CLUSTER_SHAPE_1x12x1 | Cluster shape is 1 x 12 x 1. |
| CUBLASLT_CLUSTER_SHAPE_1x13x1 | Cluster shape is 1 x 13 x 1. |
| CUBLASLT_CLUSTER_SHAPE_1x14x1 | Cluster shape is 1 x 14 x 1. |
| CUBLASLT_CLUSTER_SHAPE_1x15x1 | Cluster shape is 1 x 15 x 1. |
| CUBLASLT_CLUSTER_SHAPE_2x3x1 | Cluster shape is 2 x 3 x 1. |
| CUBLASLT_CLUSTER_SHAPE_2x5x1 | Cluster shape is 2 x 5 x 1. |
| CUBLASLT_CLUSTER_SHAPE_2x6x1 | Cluster shape is 2 x 6 x 1. |
| CUBLASLT_CLUSTER_SHAPE_2x7x1 | Cluster shape is 2 x 7 x 1. |
| CUBLASLT_CLUSTER_SHAPE_3x1x1 | Cluster shape is 3 x 1 x 1. |
| CUBLASLT_CLUSTER_SHAPE_3x2x1 | Cluster shape is 3 x 2 x 1. |
| CUBLASLT_CLUSTER_SHAPE_3x3x1 | Cluster shape is 3 x 3 x 1. |
| CUBLASLT_CLUSTER_SHAPE_3x4x1 | Cluster shape is 3 x 4 x 1. |
| CUBLASLT_CLUSTER_SHAPE_3x5x1 | Cluster shape is 3 x 5 x 1. |
| CUBLASLT_CLUSTER_SHAPE_4x3x1 | Cluster shape is 4 x 3 x 1. |
| CUBLASLT_CLUSTER_SHAPE_5x1x1 | Cluster shape is 5 x 1 x 1. |
| CUBLASLT_CLUSTER_SHAPE_5x2x1 | Cluster shape is 5 x 2 x 1. |
| CUBLASLT_CLUSTER_SHAPE_5x3x1 | Cluster shape is 5 x 3 x 1. |
| CUBLASLT_CLUSTER_SHAPE_6x1x1 | Cluster shape is 6 x 1 x 1. |
| CUBLASLT_CLUSTER_SHAPE_6x2x1 | Cluster shape is 6 x 2 x 1. |
| CUBLASLT_CLUSTER_SHAPE_7x1x1 | Cluster shape is 7 x 1 x 1. |
| CUBLASLT_CLUSTER_SHAPE_7x2x1 | Cluster shape is 7 x 2 x 1. |
| CUBLASLT_CLUSTER_SHAPE_9x1x1 | Cluster shape is 9 x 1 x 1. |
| CUBLASLT_CLUSTER_SHAPE_10x1x1 | Cluster shape is 10 x 1 x 1. |
| CUBLASLT_CLUSTER_SHAPE_11x1x1 | Cluster shape is 11 x 1 x 1. |
| CUBLASLT_CLUSTER_SHAPE_12x1x1 | Cluster shape is 12 x 1 x 1. |
| CUBLASLT_CLUSTER_SHAPE_13x1x1 | Cluster shape is 13 x 1 x 1. |
| CUBLASLT_CLUSTER_SHAPE_14x1x1 | Cluster shape is 14 x 1 x 1. |
| CUBLASLT_CLUSTER_SHAPE_15x1x1 | Cluster shape is 15 x 1 x 1. |





### 3.3.2. cublasLtEpilogue_t


The [cublasLtEpilogue_t](#cublasltepilogue-t) is an enum type to set the postprocessing options for the epilogue.


| Value | Description |
| --- | --- |
| CUBLASLT_EPILOGUE_DEFAULT = 1 | No special postprocessing, just scale and quantize the results if necessary. |
| CUBLASLT_EPILOGUE_RELU = 2 | Apply ReLU point-wise transform to the results (x := max(x, 0)). |
| CUBLASLT_EPILOGUE_RELU_AUX = CUBLASLT_EPILOGUE_RELU | 128 | Apply ReLU point-wise transform to the results (x := max(x, 0)). This epilogue mode produces an extra output, see CUBLASLT_MATMUL_DESC_EPILOGUE_AUX_POINTER of cublasLtMatmulDescAttributes_t. |
| CUBLASLT_EPILOGUE_BIAS = 4 | Apply (broadcast) bias from the bias vector. Bias vector length must match matrix D rows, and it must be packed (such as stride between vector elements is 1). Bias vector is broadcast to all columns and added before applying the final postprocessing. |
| CUBLASLT_EPILOGUE_RELU_BIAS = CUBLASLT_EPILOGUE_RELU = CUBLASLT_EPILOGUE_BIAS | Apply bias and then ReLU transform. |
| CUBLASLT_EPILOGUE_RELU_AUX_BIAS = CUBLASLT_EPILOGUE_RELU_AUX = CUBLASLT_EPILOGUE_BIAS | Apply bias and then ReLU transform. This epilogue mode produces an extra output, see CUBLASLT_MATMUL_DESC_EPILOGUE_AUX_POINTER of cublasLtMatmulDescAttributes_t. |
| CUBLASLT_EPILOGUE_DRELU = 8 | 128 | Apply ReLu gradient to matmul output. Store ReLu gradient in the output matrix. This epilogue mode requires an extra input, see CUBLASLT_MATMUL_DESC_EPILOGUE_AUX_POINTER of cublasLtMatmulDescAttributes_t. |
| CUBLASLT_EPILOGUE_DRELU_BGRAD = CUBLASLT_EPILOGUE_DRELU | 16 | Apply independently ReLu and Bias gradient to matmul output. Store ReLu gradient in the output matrix, and Bias gradient in the bias buffer (see CUBLASLT_MATMUL_DESC_BIAS_POINTER). This epilogue mode requires an extra input, see CUBLASLT_MATMUL_DESC_EPILOGUE_AUX_POINTER of cublasLtMatmulDescAttributes_t. |
| CUBLASLT_EPILOGUE_GELU = 32 | Apply GELU point-wise transform to the results (x := GELU(x)). |
| CUBLASLT_EPILOGUE_GELU_AUX = CUBLASLT_EPILOGUE_GELU | 128 | Apply GELU point-wise transform to the results (x := GELU(x)). This epilogue mode outputs GELU input as a separate matrix (useful for training). See CUBLASLT_MATMUL_DESC_EPILOGUE_AUX_POINTER of cublasLtMatmulDescAttributes_t. |
| CUBLASLT_EPILOGUE_GELU_BIAS = CUBLASLT_EPILOGUE_GELU | CUBLASLT_EPILOGUE_BIAS | Apply Bias and then GELU transform 5. |
| CUBLASLT_EPILOGUE_GELU_AUX_BIAS = CUBLASLT_EPILOGUE_GELU_AUX | CUBLASLT_EPILOGUE_BIAS | Apply Bias and then GELU transform 5. This epilogue mode outputs GELU input as a separate matrix (useful for training). See CUBLASLT_MATMUL_DESC_EPILOGUE_AUX_POINTER of cublasLtMatmulDescAttributes_t. |
| CUBLASLT_EPILOGUE_DGELU = 64 | 128 | Apply GELU gradient to matmul output. Store GELU gradient in the output matrix. This epilogue mode requires an extra input, see CUBLASLT_MATMUL_DESC_EPILOGUE_AUX_POINTER of cublasLtMatmulDescAttributes_t. |
| CUBLASLT_EPILOGUE_DGELU_BGRAD = CUBLASLT_EPILOGUE_DGELU | 16 | Apply independently GELU and Bias gradient to matmul output. Store GELU gradient in the output matrix, and Bias gradient in the bias buffer (see CUBLASLT_MATMUL_DESC_BIAS_POINTER). This epilogue mode requires an extra input, see CUBLASLT_MATMUL_DESC_EPILOGUE_AUX_POINTER of cublasLtMatmulDescAttributes_t. |
| CUBLASLT_EPILOGUE_BGRADA = 256 | Apply Bias gradient to the input matrix A. The bias size corresponds to the number of rows of the matrix D. The reduction happens over the GEMM’s “k” dimension. Store Bias gradient in the bias buffer, see CUBLASLT_MATMUL_DESC_BIAS_POINTER of cublasLtMatmulDescAttributes_t. |
| CUBLASLT_EPILOGUE_BGRADB = 512 | Apply Bias gradient to the input matrix B. The bias size corresponds to the number of columns of the matrix D. The reduction happens over the GEMM’s “k” dimension. Store Bias gradient in the bias buffer, see CUBLASLT_MATMUL_DESC_BIAS_POINTER of cublasLtMatmulDescAttributes_t. |


**NOTES:**


**5(1,2)**
: GELU (Gaussian Error Linear Unit) is approximated by: \({0.5}x\left( 1 + \text{tanh}\left( \sqrt{2/\pi}\left( x + {0.044715}x^{3} \right) \right) \right)\)



> **Note**

Note
Only CUBLASLT_EPILOGUE_DEFAULT is supported when cublasLtBatchMode_t of any matrix is set to CUBLASLT_BATCH_MODE_POINTER_ARRAY.
Only CUBLASLT_EPILOGUE_DEFAULT and CUBLASLT_EPILOGUE_BIAS are supported when cublasLtBatchMode_t of any matrix is set to CUBLASLT_BATCH_MODE_GROUPED.





### 3.3.3. cublasLtHandle_t


The [cublasLtHandle_t](#cublaslthandle-t) type is a pointer type to an opaque structure holding the cuBLASLt  library context. Use [cublasLtCreate()](#cublasltcreate) to initialize the cuBLASLt library context and return a handle to an opaque structure holding the cuBLASLt library context, and use [cublasLtDestroy()](#cublasltdestroy) to destroy a previously created cuBLASLt library context descriptor and release the resources.


> **Note**

Note
cuBLAS handle (cublasHandle_t) encapsulates a cuBLASLt handle. Any valid cublasHandle_t can be used in place of cublasLtHandle_t with a simple cast. However, unlike a cuBLAS handle, a cuBLASLt handle is not tied to any particular CUDA context with the exception of CUDA contexts tied to a graphics context (starting from CUDA 12.8). If a cuBLASLt handle is created when the current CUDA context is tied to a graphics context, then cuBLASLt detects the corresponding shared memory limitations and records it in the handle.





### 3.3.4. cublasLtLoggerCallback_t


[cublasLtLoggerCallback_t](#cublasltloggercallback-t) is a callback function pointer type. A callback function can be set using [cublasLtLoggerSetCallback()](#cublasltloggersetcallback).


**Parameters**:


| Parameter | Memory | Input / Output | Description |
| --- | --- | --- | --- |
| logLevel |  | Output | See cuBLASLt Logging. |
| functionName |  | Output | The name of the API that logged this message. |
| message |  | Output | The log message. |





### 3.3.5. cublasLtMatmulAlgo_t


[cublasLtMatmulAlgo_t](#cublasltmatmulalgo-t) is an opaque structure holding the description of the matrix multiplication algorithm. This structure can be trivially serialized and later restored for use with the same version of cuBLAS library to save on selecting the right configuration again.





### 3.3.6. cublasLtMatmulAlgoCapAttributes_t


[cublasLtMatmulAlgoCapAttributes_t](#cublasltmatmulalgocapattributes-t) enumerates matrix multiplication algorithm capability attributes that can be retrieved from an initialized [cublasLtMatmulAlgo_t](#cublasltmatmulalgo-t) descriptor using [cublasLtMatmulAlgoCapGetAttribute()](#cublasltmatmulalgocapgetattribute).


| Value | Description | Data Type |
| --- | --- | --- |
| CUBLASLT_ALGO_CAP_SPLITK_SUPPORT | Support for split-K. Boolean (0 or 1) to express if split-K implementation is supported. 0 means no support, and supported otherwise. See CUBLASLT_ALGO_CONFIG_SPLITK_NUM of cublasLtMatmulAlgoConfigAttributes_t. | int32_t |
| CUBLASLT_ALGO_CAP_REDUCTION_SCHEME_MASK | Mask to express the types of reduction schemes supported, see cublasLtReductionScheme_t. If the reduction scheme is not masked out then it is supported. For example: int isReductionSchemeComputeTypeSupported ? (reductionSchemeMask & CUBLASLT_REDUCTION_SCHEME_COMPUTE_TYPE) == CUBLASLT_REDUCTION_SCHEME_COMPUTE_TYPE ? 1 : 0; | uint32_t |
| CUBLASLT_ALGO_CAP_CTA_SWIZZLING_SUPPORT | Support for CTA-swizzling. Boolean (0 or 1) to express if CTA-swizzling implementation is supported. 0 means no support, and 1 means supported value of 1; other values are reserved. See also CUBLASLT_ALGO_CONFIG_CTA_SWIZZLING of cublasLtMatmulAlgoConfigAttributes_t. | uint32_t |
| CUBLASLT_ALGO_CAP_STRIDED_BATCH_SUPPORT | Support strided batch. 0 means no support, supported otherwise. | int32_t |
| CUBLASLT_ALGO_CAP_POINTER_ARRAY_BATCH_SUPPORT | Support pointer array batch. 0 means no support, supported otherwise. | int32_t |
| CUBLASLT_ALGO_CAP_POINTER_ARRAY_GROUPED_SUPPORT | Experimental: Support pointer array grouped batch. 0 means no support, supported otherwise. See CUBLASLT_BATCH_MODE_GROUPED of cublasLtBatchMode_t. | int32_t |
| CUBLASLT_ALGO_CAP_OUT_OF_PLACE_RESULT_SUPPORT | Support results out of place (D != C in D = alpha.A.B + beta.C). 0 means no support, supported otherwise. | int32_t |
| CUBLASLT_ALGO_CAP_UPLO_SUPPORT | Syrk (symmetric rank k update)/herk (Hermitian rank k update) support (on top of regular gemm). 0 means no support, supported otherwise. | int32_t |
| CUBLASLT_ALGO_CAP_TILE_IDS | The tile ids possible to use. See cublasLtMatmulTile_t. If no tile ids are supported then use CUBLASLT_MATMUL_TILE_UNDEFINED. Use cublasLtMatmulAlgoCapGetAttribute() with sizeInBytes = 0 to query the actual count. | uint32_t[] |
| CUBLASLT_ALGO_CAP_STAGES_IDS | The stages ids possible to use. See cublasLtMatmulStages_t. If no stages ids are supported then use CUBLASLT_MATMUL_STAGES_UNDEFINED. Use cublasLtMatmulAlgoCapGetAttribute() with sizeInBytes = 0 to query the actual count. | uint32_t[] |
| CUBLASLT_ALGO_CAP_CUSTOM_OPTION_MAX | Custom option range is from 0 to CUBLASLT_ALGO_CAP_CUSTOM_OPTION_MAX (inclusive). See CUBLASLT_ALGO_CONFIG_CUSTOM_OPTION of cublasLtMatmulAlgoConfigAttributes_t . | int32_t |
| CUBLASLT_ALGO_CAP_MATHMODE_IMPL | Indicates whether the algorithm is using regular compute or tensor operations. 0 means regular compute, 1 means tensor operations.
DEPRECATED | int32_t |
| CUBLASLT_ALGO_CAP_GAUSSIAN_IMPL | Indicate whether the algorithm implements the Gaussian optimization of complex matrix multiplication. 0 means regular compute; 1 means Gaussian. See cublasMath_t.
DEPRECATED | int32_t |
| CUBLASLT_ALGO_CAP_CUSTOM_MEMORY_ORDER | Indicates whether the algorithm supports custom (not COL or ROW memory order). 0 means only COL and ROW memory order is allowed, non-zero means that algo might have different requirements. See cublasLtOrder_t. | int32_t |
| CUBLASLT_ALGO_CAP_POINTER_MODE_MASK | Bitmask enumerating the pointer modes the algorithm supports. See cublasLtPointerModeMask_t. | uint32_t |
| CUBLASLT_ALGO_CAP_EPILOGUE_MASK | Bitmask enumerating the kinds of postprocessing algorithm supported in the epilogue. See cublasLtEpilogue_t. | uint32_t |
| CUBLASLT_ALGO_CAP_LD_NEGATIVE | Support for negative leading dimension for all of the matrices. 0 means no support, supported otherwise. | uint32_t |
| CUBLASLT_ALGO_CAP_NUMERICAL_IMPL_FLAGS | Details about algorithm’s implementation that affect it’s numerical behavior. See cublasLtNumericalImplFlags_t. | uint64_t |
| CUBLASLT_ALGO_CAP_MIN_ALIGNMENT_A_BYTES | Minimum alignment required for A matrix in bytes. | uint32_t |
| CUBLASLT_ALGO_CAP_MIN_ALIGNMENT_B_BYTES | Minimum alignment required for B matrix in bytes. | uint32_t |
| CUBLASLT_ALGO_CAP_MIN_ALIGNMENT_C_BYTES | Minimum alignment required for C matrix in bytes. | uint32_t |
| CUBLASLT_ALGO_CAP_MIN_ALIGNMENT_D_BYTES | Minimum alignment required for D matrix in bytes. | uint32_t |
| CUBLASLT_ALGO_CAP_FLOATING_POINT_EMULATION_SUPPORT | Support for for floating point emulation. See Floating Point Emulation. | int32_t |





### 3.3.7. cublasLtMatmulAlgoConfigAttributes_t


[cublasLtMatmulAlgoConfigAttributes_t](#cublasltmatmulalgoconfigattributes-t) is an enumerated type that contains the configuration attributes for cuBLASLt matrix multiply algorithms. The configuration attributes are algorithm-specific, and can be set. The attributes configuration of a given algorithm should agree with its capability attributes. Use [cublasLtMatmulAlgoConfigGetAttribute()](#cublasltmatmulalgoconfiggetattribute) and [cublasLtMatmulAlgoConfigSetAttribute()](#cublasltmatmulalgoconfigsetattribute) to get and set the attribute value of a matmul algorithm descriptor.


| Value | Description | Data Type |
| --- | --- | --- |
| CUBLASLT_ALGO_CONFIG_ID | Read-only attribute. Algorithm index. See cublasLtMatmulAlgoGetIds(). Set by cublasLtMatmulAlgoInit(). | int32_t |
| CUBLASLT_ALGO_CONFIG_TILE_ID | Tile id. See cublasLtMatmulTile_t. Default: CUBLASLT_MATMUL_TILE_UNDEFINED. | uint32_t |
| CUBLASLT_ALGO_CONFIG_STAGES_ID | stages id, see cublasLtMatmulStages_t. Default: CUBLASLT_MATMUL_STAGES_UNDEFINED. | uint32_t |
| CUBLASLT_ALGO_CONFIG_SPLITK_NUM | Number of K splits. If the number of K splits is greater than one, SPLITK_NUM parts of matrix multiplication will be computed in parallel. The results will be accumulated according to CUBLASLT_ALGO_CONFIG_REDUCTION_SCHEME. | uint32_t |
| CUBLASLT_ALGO_CONFIG_REDUCTION_SCHEME | Reduction scheme to use when splitK value > 1. Default: CUBLASLT_REDUCTION_SCHEME_NONE. See cublasLtReductionScheme_t. | uint32_t |
| CUBLASLT_ALGO_CONFIG_CTA_SWIZZLING | Enable/Disable CTA swizzling. Change mapping from CUDA grid coordinates to parts of the matrices. Possible values: 0 and 1; other values reserved. | uint32_t |
| CUBLASLT_ALGO_CONFIG_CUSTOM_OPTION | Custom option value. Each algorithm can support some custom options that don’t fit the description of the other configuration attributes. See the CUBLASLT_ALGO_CAP_CUSTOM_OPTION_MAX of cublasLtMatmulAlgoCapAttributes_t for the accepted range for a specific case. | uint32_t |
| CUBLASLT_ALGO_CONFIG_INNER_SHAPE_ID | Inner shape ID. Refer to cublasLtMatmulInnerShape_t. Default: CUBLASLT_MATMUL_INNER_SHAPE_UNDEFINED. | uint16_t |
| CUBLASLT_ALGO_CONFIG_CLUSTER_SHAPE_ID | Cluster shape ID. Refer to cublasLtClusterShape_t. Default: CUBLASLT_CLUSTER_SHAPE_AUTO. | uint16_t |





### 3.3.8. cublasLtMatmulDesc_t


The [cublasLtMatmulDesc_t](#cublasltmatmuldesc-t) is a pointer to an opaque structure holding the description of the matrix multiplication operation [cublasLtMatmul()](#cublasltmatmul). A descriptor can be created by calling [cublasLtMatmulDescCreate()](#cublasltmatmuldesccreate) and destroyed by calling [cublasLtMatmulDescDestroy()](#cublasltmatmuldescdestroy).





### 3.3.9. cublasLtMatmulDescAttributes_t


[cublasLtMatmulDescAttributes_t](#cublasltmatmuldescattributes-t) is a descriptor structure containing the attributes that define the specifics of the matrix multiply operation. Use [cublasLtMatmulDescGetAttribute()](#cublasltmatmuldescgetattribute) and [cublasLtMatmulDescSetAttribute()](#cublasltmatmuldescsetattribute) to get and set the attribute value of a matmul descriptor.


| Value | Description | Data Type |
| --- | --- | --- |
| CUBLASLT_MATMUL_DESC_COMPUTE_TYPE | Compute type. Defines the data type used for multiply and accumulate operations, and the accumulator during the matrix multiplication. See cublasComputeType_t. | int32_t |
| CUBLASLT_MATMUL_DESC_SCALE_TYPE | Scale type. Defines the data type of the scaling factors alpha and beta. The accumulator value and the value from matrix C are typically converted to scale type before final scaling. The value is then converted from scale type to the type of matrix D before storing in memory. The default value depends on CUBLASLT_MATMUL_DESC_COMPUTE_TYPE. See cudaDataType_t. | int32_t |
| CUBLASLT_MATMUL_DESC_POINTER_MODE | Specifies alpha and beta are passed by reference, whether they are scalars on the host or on the device, or device vectors. Default value is: CUBLASLT_POINTER_MODE_HOST (i.e., on the host). See cublasLtPointerMode_t. | int32_t |
| CUBLASLT_MATMUL_DESC_TRANSA | Specifies the type of transformation operation that should be performed on matrix A. Default value is: CUBLAS_OP_N (i.e., non-transpose operation). See cublasOperation_t. | int32_t |
| CUBLASLT_MATMUL_DESC_TRANSB | Specifies the type of transformation operation that should be performed on matrix B. Default value is: CUBLAS_OP_N (i.e., non-transpose operation). See cublasOperation_t. | int32_t |
| CUBLASLT_MATMUL_DESC_TRANSC | Specifies the type of transformation operation that should be performed on matrix C. Currently only CUBLAS_OP_N is supported. Default value is: CUBLAS_OP_N (i.e., non-transpose operation). See cublasOperation_t. | int32_t |
| CUBLASLT_MATMUL_DESC_FILL_MODE | Indicates whether the lower or upper part of the dense matrix was filled, and consequently should be used by the function. Currently this flag is not supported for bfloat16 or FP8 data types and is not supported on the following GPUs: Hopper, Blackwell. Default value is: CUBLAS_FILL_MODE_FULL. See cublasFillMode_t. | int32_t |
| CUBLASLT_MATMUL_DESC_EPILOGUE | Epilogue function. See cublasLtEpilogue_t. Default value is: CUBLASLT_EPILOGUE_DEFAULT. | uint32_t |
| CUBLASLT_MATMUL_DESC_BIAS_POINTER | Bias or Bias gradient vector pointer in the device memory.

Input vector with length that matches the number of rows of matrix D when one of the following epilogues is used: CUBLASLT_EPILOGUE_BIAS, CUBLASLT_EPILOGUE_RELU_BIAS, CUBLASLT_EPILOGUE_RELU_AUX_BIAS, CUBLASLT_EPILOGUE_GELU_BIAS, CUBLASLT_EPILOGUE_GELU_AUX_BIAS.
Output vector with length that matches the number of rows of matrix D when one of the following epilogues is used: CUBLASLT_EPILOGUE_DRELU_BGRAD, CUBLASLT_EPILOGUE_DGELU_BGRAD, CUBLASLT_EPILOGUE_BGRADA.
Output vector with length that matches the number of columns of matrix D when one of the following epilogues is used: CUBLASLT_EPILOGUE_BGRADB.

Bias vector elements are the same type as alpha and beta (see CUBLASLT_MATMUL_DESC_SCALE_TYPE in this table) when matrix D datatype is CUDA_R_8I and same as matrix D datatype otherwise. See the datatypes table under cublasLtMatmul() for detailed mapping. Default value is: NULL. | void * / const void * |
| CUBLASLT_MATMUL_DESC_BIAS_BATCH_STRIDE | Stride (in elements) to the next bias or bias gradient vector for strided batch operations. If cublasLtBatchMode_t of any matrix is set to CUBLASLT_BATCH_MODE_GROUPED and CUBLASLT_MATMUL_DESC_EPILOGUE includes CUBLASLT_EPILOGUE_BIAS then CUBLASLT_MATMUL_DESC_BIAS_BATCH_STRIDE must be set to 1. The default value is 0. | int64_t |
| CUBLASLT_MATMUL_DESC_EPILOGUE_AUX_POINTER | Pointer for epilogue auxiliary buffer.

Output vector for ReLu bit-mask in forward pass when CUBLASLT_EPILOGUE_RELU_AUX or CUBLASLT_EPILOGUE_RELU_AUX_BIAS epilogue is used.
Input vector for ReLu bit-mask in backward pass when CUBLASLT_EPILOGUE_DRELU or CUBLASLT_EPILOGUE_DRELU_BGRAD epilogue is used.
Output of GELU input matrix in forward pass when CUBLASLT_EPILOGUE_GELU_AUX_BIAS epilogue is used.
Input of GELU input matrix for backward pass when CUBLASLT_EPILOGUE_DGELU or CUBLASLT_EPILOGUE_DGELU_BGRAD epilogue is used.

For aux data type, see CUBLASLT_MATMUL_DESC_EPILOGUE_AUX_DATA_TYPE. Routines that don’t dereference this pointer, like cublasLtMatmulAlgoGetHeuristic() depend on its value to determine expected pointer alignment. Requires setting the CUBLASLT_MATMUL_DESC_EPILOGUE_AUX_LD attribute. | void * / const void * |
| CUBLASLT_MATMUL_DESC_EPILOGUE_AUX_LD | Leading dimension for epilogue auxiliary buffer.

ReLu bit-mask matrix leading dimension in elements (i.e. bits) when CUBLASLT_EPILOGUE_RELU_AUX, CUBLASLT_EPILOGUE_RELU_AUX_BIAS, CUBLASLT_EPILOGUE_DRELU_BGRAD, or CUBLASLT_EPILOGUE_DRELU_BGRAD epilogue is used. Must be divisible by 128 and be no less than the number of rows in the output matrix.
GELU input matrix leading dimension in elements when CUBLASLT_EPILOGUE_GELU_AUX_BIAS, CUBLASLT_EPILOGUE_DGELU,  or CUBLASLT_EPILOGUE_DGELU_BGRAD epilogue used. Must be divisible by 8 and be no less than the number of rows in the output matrix. | int64_t |
| CUBLASLT_MATMUL_DESC_EPILOGUE_AUX_BATCH_STRIDE | Batch stride for epilogue auxiliary buffer.

ReLu bit-mask matrix batch stride in elements (i.e. bits) when CUBLASLT_EPILOGUE_RELU_AUX, CUBLASLT_EPILOGUE_RELU_AUX_BIAS or CUBLASLT_EPILOGUE_DRELU_BGRAD epilogue is used. Must be divisible by 128.
GELU input matrix batch stride in elements when CUBLASLT_EPILOGUE_GELU_AUX_BIAS, CUBLASLT_EPILOGUE_DRELU, or CUBLASLT_EPILOGUE_DGELU_BGRAD epilogue used. Must be divisible by 8.

Default value: 0. | int64_t |
| CUBLASLT_MATMUL_DESC_ALPHA_VECTOR_BATCH_STRIDE | Batch stride for alpha vector. Used together with CUBLASLT_POINTER_MODE_ALPHA_DEVICE_VECTOR_BETA_HOST when matrix D’s CUBLASLT_MATRIX_LAYOUT_BATCH_COUNT is greater than 1. If CUBLASLT_POINTER_MODE_ALPHA_DEVICE_VECTOR_BETA_ZERO is set then CUBLASLT_MATMUL_DESC_ALPHA_VECTOR_BATCH_STRIDE must be set to 0 as this mode doesn’t support batched alpha vector. If cublasLtBatchMode_t of any matrix is not set to CUBLASLT_BATCH_MODE_STRIDED then CUBLASLT_MATMUL_DESC_ALPHA_VECTOR_BATCH_STRIDE must be set to 0. Default value: 0. | int64_t |
| CUBLASLT_MATMUL_DESC_SM_COUNT_TARGET | Number of SMs to target for parallel execution. Optimizes heuristics for execution on a different number of SMs when user expects a concurrent stream to be using some of the device resources. Default value: 0. | int32_t |
| CUBLASLT_MATMUL_DESC_A_SCALE_POINTER | Device pointer to the scale factor value that converts data in matrix A to the compute data type range. The scaling factor must have the same type as the compute type. If not specified, or set to NULL, the scaling factor is assumed to be 1. If set for an unsupported matrix data, scale, and compute type combination, calling cublasLtMatmul() will return CUBLAS_INVALID_VALUE. Default value: NULL | const void * |
| CUBLASLT_MATMUL_DESC_B_SCALE_POINTER | Equivalent to CUBLASLT_MATMUL_DESC_A_SCALE_POINTER for matrix B. Default value: NULL | const void * |
| CUBLASLT_MATMUL_DESC_C_SCALE_POINTER | Equivalent to CUBLASLT_MATMUL_DESC_A_SCALE_POINTER for matrix C. Default value: NULL | const void * |
| CUBLASLT_MATMUL_DESC_D_SCALE_POINTER | Equivalent to CUBLASLT_MATMUL_DESC_A_SCALE_POINTER for matrix D. Default value: NULL | const void * |
| CUBLASLT_MATMUL_DESC_AMAX_D_POINTER | Device pointer to the memory location that on completion will be set to the maximum of absolute values in the output matrix. The computed value has the same type as the compute type. If not specified, or set to NULL, the maximum absolute value is not computed. If set for an unsupported matrix data, scale, and compute type combination, calling cublasLtMatmul() will return CUBLAS_INVALID_VALUE. Default value: NULL | void * |
| CUBLASLT_MATMUL_DESC_EPILOGUE_AUX_DATA_TYPE | The type of the data that will be stored in CUBLASLT_MATMUL_DESC_EPILOGUE_AUX_POINTER. If unset (or set to the default value of -1), the data type is set to be the output matrix element data type (DType) with some exceptions:

ReLu uses a bit-mask.
For FP8 kernels with an output type (DType) of CUDA_R_8F_E4M3, the data type can be set to a non-default value if:


AType and BType are CUDA_R_8F_E4M3.
Bias Type is CUDA_R_16F.
CType is CUDA_R_16BF or CUDA_R_16F
CUBLASLT_MATMUL_DESC_EPILOGUE is set to CUBLASLT_EPILOGUE_GELU_AUX

When CType is CUDA_R_16F, the data type may be set to CUDA_R_16F or CUDA_R_8F_E4M3. When CType is CUDA_R_16BF, the data type may be set to CUDA_R_16BF. Otherwise, the data type should be left unset or set to the default value of -1.
If set for an unsupported matrix data, scale, and compute type combination, calling cublasLtMatmul() will return CUBLAS_INVALID_VALUE. Default value: -1 | int32_t (cudaDataType_t) |
| CUBLASLT_MATMUL_DESC_EPILOGUE_AUX_SCALE_POINTER | Device pointer to the scaling factor value to convert results from compute type data range to storage data range in the auxiliary matrix that is set via CUBLASLT_MATMUL_DESC_EPILOGUE_AUX_POINTER. The scaling factor value must have the same type as the compute type. If not specified, or set to NULL, the scaling factor is assumed to be 1. If set for an unsupported matrix data, scale, and compute type combination, calling cublasLtMatmul() will return CUBLAS_INVALID_VALUE. Default value: NULL | void * |
| CUBLASLT_MATMUL_DESC_EPILOGUE_AUX_AMAX_POINTER | Device pointer to the memory location that on completion will be set to the maximum of absolute values in the buffer that is set via CUBLASLT_MATMUL_DESC_EPILOGUE_AUX_POINTER. The computed value has the same type as the compute type. If not specified, or set to NULL, the maximum absolute value is not computed. If set for an unsupported matrix data, scale, and compute type combination, calling cublasLtMatmul() will return CUBLAS_INVALID_VALUE. Default value: NULL | void * |
| CUBLASLT_MATMUL_DESC_FAST_ACCUM | Flag for managing FP8 fast accumulation mode. When enabled, on some GPUs problem execution might be faster but at the cost of lower accuracy because intermediate results will not periodically be promoted to a higher precision. Currently this flag has an effect on the following GPUs: Ada, Hopper. Default value: 0 - fast accumulation mode is disabled | int8_t |
| CUBLASLT_MATMUL_DESC_BIAS_DATA_TYPE | Type of the bias or bias gradient vector in the device memory. Bias case: see CUBLASLT_EPILOGUE_BIAS. If unset (or set to the default value of -1), the bias vector elements are the same type as the elements of the output matrix (Dtype) with the following exceptions:

IMMA kernels with computeType=CUDA_R_32I and Ctype=CUDA_R_8I where the bias vector elements are the same type as alpha, beta (CUBLASLT_MATMUL_DESC_SCALE_TYPE=CUDA_R_32F)
For FP8 kernels with an output type of CUDA_R_32F, CUDA_R_8F_E4M3 or CUDA_R_8F_E5M2. See cublasLtMatmul() for more details.

Default value: -1 | int32_t (cudaDataType_t) |
| CUBLASLT_MATMUL_DESC_A_SCALE_MODE | Scaling mode that defines how the matrix scaling factor for matrix A is interpreted. Default value: 0. See cublasLtMatmulMatrixScale_t. | int32_t |
| CUBLASLT_MATMUL_DESC_B_SCALE_MODE | Scaling mode that defines how the matrix scaling factor for matrix B is interpreted. Default value: 0. See cublasLtMatmulMatrixScale_t. | int32_t |
| CUBLASLT_MATMUL_DESC_C_SCALE_MODE | Scaling mode that defines how the matrix scaling factor for matrix C is interpreted. Default value: 0. See cublasLtMatmulMatrixScale_t. | int32_t |
| CUBLASLT_MATMUL_DESC_D_SCALE_MODE | Scaling mode that defines how the matrix scaling factor for matrix D is interpreted. Default value: 0. See cublasLtMatmulMatrixScale_t. | int32_t |
| CUBLASLT_MATMUL_DESC_EPILOGUE_AUX_SCALE_MODE | Scaling mode that defines how the matrix scaling factor for the auxiliary matrix is interpreted. Default value: 0. See cublasLtMatmulMatrixScale_t. | int32_t |
| CUBLASLT_MATMUL_DESC_D_OUT_SCALE_POINTER | Device pointer to the scale factors that are used to convert data in matrix D to the compute data type range. The scaling factor value type is defined by the scaling mode (see CUBLASLT_MATMUL_DESC_D_OUT_SCALE_MODE). If set for an unsupported matrix data, scale, scale mode, and compute type combination, or missing for a supported combination, then calling cublasLtMatmul() will return CUBLAS_INVALID_VALUE. Default value: NULL. | void * |
| CUBLASLT_MATMUL_DESC_D_OUT_SCALE_MODE | Scaling mode that defines how the output matrix scaling factor for matrix D is interpreted. Default value: 0. See cublasLtMatmulMatrixScale_t. | int32_t |
| CUBLASLT_MATMUL_DESC_EMULATION_DESCRIPTOR | Emulation descriptor to configure floating point emulation parameters. Default value: NULL. | int32_t |
| CUBLASLT_MATMUL_DESC_ALPHA_BATCH_STRIDE | Experimental: Batch stride for alpha. Applicable when matrix D’s CUBLASLT_MATRIX_LAYOUT_BATCH_COUNT is greater than 1. Supported values are 0 and 1. Default value is 0. When the value is set to 1, the parameter alpha of cublasLtMatmul() must contain a device array of pointers of length CUBLASLT_MATRIX_LAYOUT_BATCH_COUNT. This setting is currently only supported if cublasLtBatchMode_t of all matrices is set to CUBLASLT_BATCH_MODE_GROUPED and CUBLASLT_MATMUL_DESC_POINTER_MODE is set to CUBLASLT_POINTER_MODE_DEVICE. | int64_t |
| CUBLASLT_MATMUL_DESC_BETA_BATCH_STRIDE | Experimental: Batch stride for beta. Applicable when matrix D’s CUBLASLT_MATRIX_LAYOUT_BATCH_COUNT is greater than 1. Supported values are 0 and 1. Default value is 0. When the value is set to 1, the parameter beta of cublasLtMatmul() must contain a device array of pointers of length CUBLASLT_MATRIX_LAYOUT_BATCH_COUNT. This setting is currently only supported if cublasLtBatchMode_t of all matrices is set to CUBLASLT_BATCH_MODE_GROUPED and CUBLASLT_MATMUL_DESC_POINTER_MODE is set to CUBLASLT_POINTER_MODE_DEVICE. | int64_t |


> **Note**

Note
The batch mode of a matmul operation is inferred from the batch modes of matrix descriptors, which must all be the same. The following table describes rules for operands that do not have a descriptor, like scaling factors. The expected parameter value depends on the batch mode of the matmul operation and the operand stride configured via a CUBLASLT_MATMUL_DESC_{ATTR}_BATCH_STRIDE attribute.


| Matmul batch mode | Operand stride | Expected parameter value | Usage scenario |
| --- | --- | --- | --- |
| Strided | 0 | Pointer to a buffer for a single batch element | Reuse the value across the batch |
| Non-zero | Pointer to a buffer with distinct values for each batch element | Use distinct values for each batch element |
| Pointer array or grouped | 0 | Pointer to a for a single batch element | Reuse the value across the batch |
| 1 | Pointer to a device array of pointers to buffers, one for each batch element | Use distinct values for each batch element |
| Other values | Not supported | None |





### 3.3.10. cublasLtMatmulHeuristicResult_t


[cublasLtMatmulHeuristicResult_t](#cublasltmatmulheuristicresult-t) is a descriptor that holds the configured matrix multiplication algorithm descriptor and its runtime properties.


| Member | Description |
| --- | --- |
| cublasLtMatmulAlgo_t algo | Must be initialized with cublasLtMatmulAlgoInit() if the preference CUBLASLT_MATMUL_PERF_SEARCH_MODE is set to CUBLASLT_SEARCH_LIMITED_BY_ALGO_ID. See cublasLtMatmulSearch_t. |
| size_t workspaceSize; | Actual size of workspace memory required. |
| cublasStatus_t state; | Result status. Other fields are valid only if, after call to cublasLtMatmulAlgoGetHeuristic(), this member is set to CUBLAS_STATUS_SUCCESS. |
| float wavesCount; | Waves count is a device utilization metric. A wavesCount value of 1.0f suggests that when the kernel is launched it will fully occupy the GPU. |
| int reserved[4]; | Reserved. |





### 3.3.11. cublasLtMatmulInnerShape_t


[cublasLtMatmulInnerShape_t](#cublasltmatmulinnershape-t) is an enumerated type used to configure various aspects of the internal kernel design. This does not impact the CUDA grid size.


| Value | Description |
| --- | --- |
| CUBLASLT_MATMUL_INNER_SHAPE_UNDEFINED | Inner shape is undefined. |
| CUBLASLT_MATMUL_INNER_SHAPE_MMA884 | Inner shape is MMA884. |
| CUBLASLT_MATMUL_INNER_SHAPE_MMA1684 | Inner shape is MMA1684. |
| CUBLASLT_MATMUL_INNER_SHAPE_MMA1688 | Inner shape is MMA1688. |
| CUBLASLT_MATMUL_INNER_SHAPE_MMA16816 | Inner shape is MMA16816. |





### 3.3.12. cublasLtMatmulPreference_t


The [cublasLtMatmulPreference_t](#cublasltmatmulpreference-t) is a pointer to an opaque structure holding the description of the preferences for [cublasLtMatmulAlgoGetHeuristic()](#cublasltmatmulalgogetheuristic) configuration. Use [cublasLtMatmulPreferenceCreate()](#cublasltmatmulpreferencecreate) to create one instance of the descriptor and [cublasLtMatmulPreferenceDestroy()](#cublasltmatmulpreferencedestroy) to destroy a previously created descriptor and release the resources.





### 3.3.13. cublasLtMatmulPreferenceAttributes_t


[cublasLtMatmulPreferenceAttributes_t](#cublasltmatmulpreferenceattributes-t) is an enumerated type used to apply algorithm search preferences while fine-tuning the heuristic function. Use [cublasLtMatmulPreferenceGetAttribute()](#cublasltmatmulpreferencegetattribute) and [cublasLtMatmulPreferenceSetAttribute()](#cublasltmatmulpreferencesetattribute) to get and set the attribute value of a matmul preference descriptor.


| Value | Description | Data Type |
| --- | --- | --- |
| CUBLASLT_MATMUL_PREF_SEARCH_MODE | Search mode. See cublasLtMatmulSearch_t. Default is CUBLASLT_SEARCH_BEST_FIT. | uint32_t |
| CUBLASLT_MATMUL_PREF_MAX_WORKSPACE_BYTES | Maximum allowed workspace memory. Default is 0 (no workspace memory allowed). | uint64_t |
| CUBLASLT_MATMUL_PREF_REDUCTION_SCHEME_MASK | Reduction scheme mask. See cublasLtReductionScheme_t. Only algorithm configurations specifying CUBLASLT_ALGO_CONFIG_REDUCTION_SCHEME that is not masked out by this attribute are allowed. For example, a mask value of 0x03 will allow only INPLACE and COMPUTE_TYPE reduction schemes. Default is CUBLASLT_REDUCTION_SCHEME_MASK (i.e., allows all reduction schemes). | uint32_t |
| CUBLASLT_MATMUL_PREF_MIN_ALIGNMENT_A_BYTES | Minimum buffer alignment for matrix A (in bytes). Selecting a smaller value will exclude algorithms that can not work with matrix A, which is not as strictly aligned as the algorithms need. Default is 256 bytes. | uint32_t |
| CUBLASLT_MATMUL_PREF_MIN_ALIGNMENT_B_BYTES | Minimum buffer alignment for matrix B (in bytes). Selecting a smaller value will exclude algorithms that can not work with matrix B, which is not as strictly aligned as the algorithms need. Default is 256 bytes. | uint32_t |
| CUBLASLT_MATMUL_PREF_MIN_ALIGNMENT_C_BYTES | Minimum buffer alignment for matrix C (in bytes). Selecting a smaller value will exclude algorithms that can not work with matrix C, which is not as strictly aligned as the algorithms need. Default is 256 bytes. | uint32_t |
| CUBLASLT_MATMUL_PREF_MIN_ALIGNMENT_D_BYTES | Minimum buffer alignment for matrix D (in bytes). Selecting a smaller value will exclude algorithms that can not work with matrix D, which is not as strictly aligned as the algorithms need. Default is 256 bytes. | uint32_t |
| CUBLASLT_MATMUL_PREF_MAX_WAVES_COUNT | Maximum wave count. See cublasLtMatmulHeuristicResult_t::wavesCount. Selecting a non-zero value will exclude algorithms that report device utilization higher than specified. Default is 0.0f. | float |
| CUBLASLT_MATMUL_PREF_IMPL_MASK | Numerical implementation details mask. See cublasLtNumericalImplFlags_t. Filters heuristic result to only include algorithms that use the allowed implementations. default: uint64_t(-1) (allow everything) | uint64_t |
| CUBLASLT_MATMUL_PREF_GROUPED_AVERAGE_REDUCTION_DIM | Experimental: Average reduction dimension. This is only supported when all matrix descriptors have CUBLASLT_MATRIX_LAYOUT_BATCH_MODE set to CUBLASLT_BATCH_MODE_GROUPED. Default value is 0. | uint32_t |
| CUBLASLT_MATMUL_PREF_GROUPED_DESC_D_AVERAGE_ROWS | Experimental: Average rows of matrix D. This is only supported when all matrix descriptors have CUBLASLT_MATRIX_LAYOUT_BATCH_MODE set to CUBLASLT_BATCH_MODE_GROUPED. Default value is 0. | uint32_t |
| CUBLASLT_MATMUL_PREF_GROUPED_DESC_D_AVERAGE_COLS | Experimental: Average columns of matrix D. This is only supported when all matrix descriptors have CUBLASLT_MATRIX_LAYOUT_BATCH_MODE set to CUBLASLT_BATCH_MODE_GROUPED. Default value is 0. | uint32_t |





### 3.3.14. cublasLtMatmulSearch_t


[cublasLtMatmulSearch_t](#cublasltmatmulsearch-t) is an enumerated type that contains the attributes for heuristics search type.


| Value | Description | Data Type |
| --- | --- | --- |
| CUBLASLT_SEARCH_BEST_FIT | Request heuristics for the best algorithm for the given use case. |  |
| CUBLASLT_SEARCH_LIMITED_BY_ALGO_ID | Request heuristics only for the pre-configured algo id. |  |





### 3.3.15. cublasLtMatmulTile_t


[cublasLtMatmulTile_t](#cublasltmatmultile-t) is an enumerated type used to set the tile size in `rows x columns.` See also [CUTLASS: Fast Linear Algebra in CUDA C++](https://www.google.com/url?q=https://devblogs.nvidia.com/cutlass-linear-algebra-cuda/&sa=D&ust=1543610995532000&usg=AFQjCNE3tHlNsXDOnOhbVeeH1uXWQFLzLA).


| Value | Description |
| --- | --- |
| CUBLASLT_MATMUL_TILE_UNDEFINED | Tile size is undefined. |
| CUBLASLT_MATMUL_TILE_8x8 | Tile size is 8 rows x 8 columns. |
| CUBLASLT_MATMUL_TILE_8x16 | Tile size is 8 rows x 16 columns. |
| CUBLASLT_MATMUL_TILE_16x8 | Tile size is 16 rows x 8 columns. |
| CUBLASLT_MATMUL_TILE_8x32 | Tile size is 8 rows x 32 columns. |
| CUBLASLT_MATMUL_TILE_16x16 | Tile size is 16 rows x 16 columns. |
| CUBLASLT_MATMUL_TILE_32x8 | Tile size is 32 rows x 8 columns. |
| CUBLASLT_MATMUL_TILE_8x64 | Tile size is 8 rows x 64 columns. |
| CUBLASLT_MATMUL_TILE_16x32 | Tile size is 16 rows x 32 columns. |
| CUBLASLT_MATMUL_TILE_32x16 | Tile size is 32 rows x 16 columns. |
| CUBLASLT_MATMUL_TILE_64x8 | Tile size is 64 rows x 8 columns. |
| CUBLASLT_MATMUL_TILE_32x32 | Tile size is 32 rows x 32 columns. |
| CUBLASLT_MATMUL_TILE_32x64 | Tile size is 32 rows x 64 columns. |
| CUBLASLT_MATMUL_TILE_64x32 | Tile size is 64 rows x 32 columns. |
| CUBLASLT_MATMUL_TILE_32x128 | Tile size is 32 rows x 128 columns. |
| CUBLASLT_MATMUL_TILE_64x64 | Tile size is 64 rows x 64 columns. |
| CUBLASLT_MATMUL_TILE_128x32 | Tile size is 128 rows x 32 columns. |
| CUBLASLT_MATMUL_TILE_64x128 | Tile size is 64 rows x 128 columns. |
| CUBLASLT_MATMUL_TILE_128x64 | Tile size is 128 rows x 64 columns. |
| CUBLASLT_MATMUL_TILE_64x256 | Tile size is 64 rows x 256 columns. |
| CUBLASLT_MATMUL_TILE_128x128 | Tile size is 128 rows x 128 columns. |
| CUBLASLT_MATMUL_TILE_256x64 | Tile size is 256 rows x 64 columns. |
| CUBLASLT_MATMUL_TILE_64x512 | Tile size is 64 rows x 512 columns. |
| CUBLASLT_MATMUL_TILE_128x256 | Tile size is 128 rows x 256 columns. |
| CUBLASLT_MATMUL_TILE_256x128 | Tile size is 256 rows x 128 columns. |
| CUBLASLT_MATMUL_TILE_512x64 | Tile size is 512 rows x 64 columns. |
| CUBLASLT_MATMUL_TILE_64x96 | Tile size is 64 rows x 96 columns. |
| CUBLASLT_MATMUL_TILE_96x64 | Tile size is 96 rows x 64 columns. |
| CUBLASLT_MATMUL_TILE_96x128 | Tile size is 96 rows x 128 columns. |
| CUBLASLT_MATMUL_TILE_128x160 | Tile size is 128 rows x 160 columns. |
| CUBLASLT_MATMUL_TILE_160x128 | Tile size is 160 rows x 128 columns. |
| CUBLASLT_MATMUL_TILE_192x128 | Tile size is 192 rows x 128 columns. |
| CUBLASLT_MATMUL_TILE_128x192 | Tile size is 128 rows x 192 columns. |
| CUBLASLT_MATMUL_TILE_128x96 | Tile size is 128 rows x 96 columns. |





### 3.3.16. cublasLtMatmulStages_t


[cublasLtMatmulStages_t](#cublasltmatmulstages-t) is an enumerated type used to configure the size and number of shared memory buffers where input elements are staged. Number of staging buffers defines kernel’s pipeline depth.


| Value | Description |
| --- | --- |
| CUBLASLT_MATMUL_STAGES_UNDEFINED | Stage size is undefined. |
| CUBLASLT_MATMUL_STAGES_16x1 | Stage size is 16, number of stages is 1. |
| CUBLASLT_MATMUL_STAGES_16x2 | Stage size is 16, number of stages is 2. |
| CUBLASLT_MATMUL_STAGES_16x3 | Stage size is 16, number of stages is 3. |
| CUBLASLT_MATMUL_STAGES_16x4 | Stage size is 16, number of stages is 4. |
| CUBLASLT_MATMUL_STAGES_16x5 | Stage size is 16, number of stages is 5. |
| CUBLASLT_MATMUL_STAGES_16x6 | Stage size is 16, number of stages is 6. |
| CUBLASLT_MATMUL_STAGES_32x1 | Stage size is 32, number of stages is 1. |
| CUBLASLT_MATMUL_STAGES_32x2 | Stage size is 32, number of stages is 2. |
| CUBLASLT_MATMUL_STAGES_32x3 | Stage size is 32, number of stages is 3. |
| CUBLASLT_MATMUL_STAGES_32x4 | Stage size is 32, number of stages is 4. |
| CUBLASLT_MATMUL_STAGES_32x5 | Stage size is 32, number of stages is 5. |
| CUBLASLT_MATMUL_STAGES_32x6 | Stage size is 32, number of stages is 6. |
| CUBLASLT_MATMUL_STAGES_64x1 | Stage size is 64, number of stages is 1. |
| CUBLASLT_MATMUL_STAGES_64x2 | Stage size is 64, number of stages is 2. |
| CUBLASLT_MATMUL_STAGES_64x3 | Stage size is 64, number of stages is 3. |
| CUBLASLT_MATMUL_STAGES_64x4 | Stage size is 64, number of stages is 4. |
| CUBLASLT_MATMUL_STAGES_64x5 | Stage size is 64, number of stages is 5. |
| CUBLASLT_MATMUL_STAGES_64x6 | Stage size is 64, number of stages is 6. |
| CUBLASLT_MATMUL_STAGES_128x1 | Stage size is 128, number of stages is 1. |
| CUBLASLT_MATMUL_STAGES_128x2 | Stage size is 128, number of stages is 2. |
| CUBLASLT_MATMUL_STAGES_128x3 | Stage size is 128, number of stages is 3. |
| CUBLASLT_MATMUL_STAGES_128x4 | Stage size is 128, number of stages is 4. |
| CUBLASLT_MATMUL_STAGES_128x5 | Stage size is 128, number of stages is 5. |
| CUBLASLT_MATMUL_STAGES_128x6 | Stage size is 128, number of stages is 6. |
| CUBLASLT_MATMUL_STAGES_32x10 | Stage size is 32, number of stages is 10. |
| CUBLASLT_MATMUL_STAGES_8x4 | Stage size is 8, number of stages is 4. |
| CUBLASLT_MATMUL_STAGES_16x10 | Stage size is 16, number of stages is 10. |
| CUBLASLT_MATMUL_STAGES_8x5 | Stage size is 8, number of stages is 5. |
| CUBLASLT_MATMUL_STAGES_8x3 | Stage size is 8, number of stages is 3. |
| CUBLASLT_MATMUL_STAGES_8xAUTO | Stage size is 8, number of stages is selected automatically. |
| CUBLASLT_MATMUL_STAGES_16xAUTO | Stage size is 16, number of stages is selected automatically. |
| CUBLASLT_MATMUL_STAGES_32xAUTO | Stage size is 32, number of stages is selected automatically. |
| CUBLASLT_MATMUL_STAGES_64xAUTO | Stage size is 64, number of stages is selected automatically. |
| CUBLASLT_MATMUL_STAGES_128xAUTO | Stage size is 128, number of stages is selected automatically. |
| CUBLASLT_MATMUL_STAGES_256xAUTO | Stage size is 256, number of stages is selected automatically. |
| CUBLASLT_MATMUL_STAGES_768xAUTO | Stage size is 768, number of stages is selected automatically. |





### 3.3.17. cublasLtNumericalImplFlags_t


[cublasLtNumericalImplFlags_t](#cublasltnumericalimplflags-t): a set of bit-flags that can be specified to select implementation details that may affect numerical behavior of algorithms.


Flags below can be combined using the bit OR operator “|”.


| Value | Description |
| --- | --- |
| CUBLASLT_NUMERICAL_IMPL_FLAGS_FMA | Specify that the implementation is based on [H,F,D]FMA (fused multiply-add) family instructions. |
| CUBLASLT_NUMERICAL_IMPL_FLAGS_HMMA | Specify that the implementation is based on HMMA (tensor operation) family instructions. |
| CUBLASLT_NUMERICAL_IMPL_FLAGS_IMMA | Specify that the implementation is based on IMMA (integer tensor operation) family instructions. |
| CUBLASLT_NUMERICAL_IMPL_FLAGS_DMMA | Specify that the implementation is based on DMMA (double precision tensor operation) family instructions. |
| CUBLASLT_NUMERICAL_IMPL_FLAGS_TENSOR_OP_MASK | Mask to filter implementations using any of the above kinds of tensor operations. |
| CUBLASLT_NUMERICAL_IMPL_FLAGS_OP_TYPE_MASK | Mask to filter implementation details about multiply-accumulate instructions used. |
|  |  |
| CUBLASLT_NUMERICAL_IMPL_FLAGS_ACCUMULATOR_16F | Specify that the implementation’s inner dot product is using half precision accumulator. |
| CUBLASLT_NUMERICAL_IMPL_FLAGS_ACCUMULATOR_32F | Specify that the implementation’s inner dot product is using single precision accumulator. |
| CUBLASLT_NUMERICAL_IMPL_FLAGS_ACCUMULATOR_64F | Specify that the implementation’s inner dot product is using double precision accumulator. |
| CUBLASLT_NUMERICAL_IMPL_FLAGS_ACCUMULATOR_32I | Specify that the implementation’s inner dot product is using 32 bit signed integer precision accumulator. |
| CUBLASLT_NUMERICAL_IMPL_FLAGS_ACCUMULATOR_TYPE_MASK | Mask to filter implementation details about accumulator used. |
|  |  |
| CUBLASLT_NUMERICAL_IMPL_FLAGS_INPUT_16F | Specify that the implementation’s inner dot product multiply-accumulate instruction is using half-precision inputs. |
| CUBLASLT_NUMERICAL_IMPL_FLAGS_INPUT_16BF | Specify that the implementation’s inner dot product multiply-accumulate instruction is using bfloat16 inputs. |
| CUBLASLT_NUMERICAL_IMPL_FLAGS_INPUT_TF32 | Specify that the implementation’s inner dot product multiply-accumulate instruction is using TF32 inputs. |
| CUBLASLT_NUMERICAL_IMPL_FLAGS_INPUT_32F | Specify that the implementation’s inner dot product multiply-accumulate instruction is using single-precision inputs. |
| CUBLASLT_NUMERICAL_IMPL_FLAGS_INPUT_64F | Specify that the implementation’s inner dot product multiply-accumulate instruction is using double-precision inputs. |
| CUBLASLT_NUMERICAL_IMPL_FLAGS_INPUT_8I | Specify that the implementation’s inner dot product multiply-accumulate instruction is using 8-bit integer inputs. |
| CUBLASLT_NUMERICAL_IMPL_FLAGS_OP_INPUT_TYPE_MASK | Mask to filter implementation details about accumulator input used. |
|  |  |
| CUBLASLT_NUMERICAL_IMPL_FLAGS_GAUSSIAN | Specify that the implementation applies Gauss complexity reduction algorithm to reduce arithmetic complexity of the complex matrix multiplication problem |





### 3.3.18. cublasLtMatrixLayout_t


The [cublasLtMatrixLayout_t](#cublasltmatrixlayout-t) is a pointer to an opaque structure holding the description of a matrix layout. Use [cublasLtMatrixLayoutCreate()](#cublasltmatrixlayoutcreate) or [cublasLtGroupedMatrixLayoutCreate()](#cublasltgroupedmatrixlayoutcreate) to create one instance of the descriptor and [cublasLtMatrixLayoutDestroy()](#cublasltmatrixlayoutdestroy) to destroy a previously created descriptor and release the resources.





### 3.3.19. cublasLtMatrixLayoutAttribute_t


[cublasLtMatrixLayoutAttribute_t](#cublasltmatrixlayoutattribute-t) is a descriptor structure containing the attributes that define the details of the matrix operation. Use [cublasLtMatrixLayoutGetAttribute()](#cublasltmatrixlayoutgetattribute) and [cublasLtMatrixLayoutSetAttribute()](#cublasltmatrixlayoutsetattribute) to get and set the attribute value of a matrix layout descriptor.


| Value | Description | Data Type |
| --- | --- | --- |
| CUBLASLT_MATRIX_LAYOUT_TYPE | Specifies the data precision type. See cudaDataType_t. | uint32_t |
| CUBLASLT_MATRIX_LAYOUT_ORDER | Specifies the memory order of the data of the matrix. Default value is CUBLASLT_ORDER_COL. See cublasLtOrder_t . | int32_t |
| CUBLASLT_MATRIX_LAYOUT_ROWS | Describes the number of rows in the matrix. Normally only values that can be expressed as int32_t are supported. | uint64_t |
| CUBLASLT_MATRIX_LAYOUT_COLS | Describes the number of columns in the matrix. Normally only values that can be expressed as int32_t are supported. | uint64_t |
| CUBLASLT_MATRIX_LAYOUT_LD | The leading dimension of the matrix. For CUBLASLT_ORDER_COL this is the stride (in elements) of matrix column. See also cublasLtOrder_t.

Currently only non-negative values are supported.
Must be large enough so that matrix memory locations are not overlapping (e.g., greater or equal to CUBLASLT_MATRIX_LAYOUT_ROWS in case of CUBLASLT_ORDER_COL). | int64_t |
| CUBLASLT_MATRIX_LAYOUT_BATCH_COUNT | Number of matmul operations to perform in the batch. Default value is 1. See also CUBLASLT_ALGO_CAP_STRIDED_BATCH_SUPPORT, CUBLASLT_ALGO_CAP_POINTER_ARRAY_BATCH_SUPPORT and CUBLASLT_ALGO_CAP_POINTER_ARRAY_GROUPED_SUPPORT in cublasLtMatmulAlgoCapAttributes_t. | int32_t |
| CUBLASLT_MATRIX_LAYOUT_STRIDED_BATCH_OFFSET | Stride (in elements) to the next matrix for the strided batch operation. Default value is 0. When matrix type is planar-complex (CUBLASLT_MATRIX_LAYOUT_PLANE_OFFSET != 0), batch stride is interpreted by cublasLtMatmul() in number of real valued sub-elements. E.g. for data of type CUDA_C_16F, offset of 1024B is encoded as a stride of value 512 (since each element of the real and imaginary matrices is a 2B (16bit) floating point type). NOTE: A bug in cublasLtMatrixTransform() causes it to interpret the batch stride for a planar-complex matrix as if it was specified in number of complex elements. Therefore an offset of 1024B must be encoded as stride value 256 when calling cublasLtMatrixTransform() (each complex element is 4B with real and imaginary values 2B each). This behavior is expected to be corrected in the next major cuBLAS version. | int64_t |
| CUBLASLT_MATRIX_LAYOUT_PLANE_OFFSET | Stride (in bytes) to the imaginary plane for planar-complex layout. Default value is 0, indicating that the layout is regular (real and imaginary parts of complex numbers are interleaved in memory for each element). | int64_t |
| CUBLASLT_MATRIX_LAYOUT_BATCH_MODE | The batch mode of the matrix. Default value is CUBLASLT_BATCH_MODE_STRIDED. See cublasLtBatchMode_t . | int32_t |
| CUBLASLT_GROUPED_MATRIX_LAYOUT_ROWS_ARRAY | Experimental: a device pointer to the array of rows in a grouped matrix. The length of the array must be equal to CUBLASLT_MATRIX_LAYOUT_BATCH_COUNT. The width of each element in the array is determined by CUBLASLT_GROUPED_MATRIX_LAYOUT_ROWS_COLS_ARRAY_INTEGER_WIDTH. Default value is NULL. | void * |
| CUBLASLT_GROUPED_MATRIX_LAYOUT_COLS_ARRAY | Experimental: a device pointer to the array of columns in a grouped matrix. The length of the array must be equal to CUBLASLT_MATRIX_LAYOUT_BATCH_COUNT. The width of each element in the array is determined by CUBLASLT_GROUPED_MATRIX_LAYOUT_ROWS_COLS_ARRAY_INTEGER_WIDTH. Default value is NULL. | void * |
| CUBLASLT_GROUPED_MATRIX_LAYOUT_LD_ARRAY | Experimental: a device pointer to the array of leading dimensions in a grouped matrix. The length of the array must be equal to CUBLASLT_MATRIX_LAYOUT_BATCH_COUNT. The width of each element in the array is determined by CUBLASLT_GROUPED_MATRIX_LAYOUT_LD_ARRAY_INTEGER_WIDTH. Default value is NULL. | void * |
| CUBLASLT_GROUPED_MATRIX_LAYOUT_ROWS_COLS_ARRAY_INTEGER_WIDTH | Experimental: cublasLtIntegerWidth_t is an enumerated type used to indicate the width of integers in the rows and columns arrays of a grouped matrix. Default value is CUBLASLT_INTEGER_WIDTH_32. See cublasLtIntegerWidth_t . | int32_t |
| CUBLASLT_GROUPED_MATRIX_LAYOUT_LD_ARRAY_INTEGER_WIDTH | Experimental: cublasLtIntegerWidth_t is an enumerated type used to indicate the width of integers in the leading dimensions array of a grouped matrix. Default value is CUBLASLT_INTEGER_WIDTH_32. See cublasLtIntegerWidth_t . | int32_t |





### 3.3.20. cublasLtIntegerWidth_t


Experimental: [cublasLtIntegerWidth_t](#cublasltintegerwidth-t) is an enumerated type used to indicate the width of integers in the dimensions arrays of a grouped matrix.


| Value | Description |
| --- | --- |
| CUBLASLT_INTEGER_WIDTH_32 | 32-bit integer width. |
| CUBLASLT_INTEGER_WIDTH_64 | 64-bit integer width. |





### 3.3.21. cublasLtMatrixTransformDesc_t


The [cublasLtMatrixTransformDesc_t](#cublasltmatrixtransformdesc-t) is a pointer to an opaque structure holding the description of a matrix transformation operation. Use [cublasLtMatrixTransformDescCreate()](#cublasltmatrixtransformdesccreate) to create one instance of the descriptor and [cublasLtMatrixTransformDescDestroy()](#cublasltmatrixtransformdescdestroy) to destroy a previously created descriptor and release the resources.





### 3.3.22. cublasLtMatrixTransformDescAttributes_t


[cublasLtMatrixTransformDescAttributes_t](#cublasltmatrixtransformdescattributes-t) is a descriptor structure containing the attributes that define the specifics of the matrix transform operation. Use [cublasLtMatrixTransformDescGetAttribute()](#cublasltmatrixtransformdescgetattribute) and [cublasLtMatrixTransformDescSetAttribute()](#cublasltmatrixtransformdescsetattribute) to set the attribute value of a matrix transform descriptor.


| Value | Description | Data Type |
| --- | --- | --- |
| CUBLASLT_MATRIX_TRANSFORM_DESC_SCALE_TYPE | Scale type. Inputs are converted to the scale type for scaling and summation, and results are then converted to the output type to store in the memory. For the supported data types see cudaDataType_t. | int32_t |
| CUBLASLT_MATRIX_TRANSFORM_DESC_POINTER_MODE | Specifies the scalars alpha and beta are passed by reference whether on the host or on the device. Default value is: CUBLASLT_POINTER_MODE_HOST (i.e., on the host). See cublasLtPointerMode_t. | int32_t |
| CUBLASLT_MATRIX_TRANSFORM_DESC_TRANSA | Specifies the type of operation that should be performed on the matrix A. Default value is: CUBLAS_OP_N (i.e., non-transpose operation). See cublasOperation_t. | int32_t |
| CUBLASLT_MATRIX_TRANSFORM_DESC_TRANSB | Specifies the type of operation that should be performed on the matrix B. Default value is: CUBLAS_OP_N (i.e., non-transpose operation). See cublasOperation_t. | int32_t |





### 3.3.23. cublasLtOrder_t


[cublasLtOrder_t](#cublasltorder-t) is an enumerated type used to indicate the data ordering of the matrix.


| Value | Description |
| --- | --- |
| CUBLASLT_ORDER_COL | Data is ordered in column-major format. The leading dimension is the stride (in elements) to the beginning of next column in memory. |
| CUBLASLT_ORDER_ROW | Data is ordered in row-major format. The leading dimension is the stride (in elements) to the beginning of next row in memory. |
| CUBLASLT_ORDER_COL32 | Data is ordered in column-major ordered tiles of 32 columns. The leading dimension is the stride (in elements) to the beginning of next group of 32-columns.
For example, if the matrix has 33 columns and 2 rows, then the leading dimension must be at least 32 * 2 = 64. |
| CUBLASLT_ORDER_COL4_4R2_8C | Data is ordered in column-major ordered tiles of composite tiles with total 32 columns and 8 rows. A tile is composed of interleaved inner tiles of 4 columns within 4 even or odd rows in an alternating pattern.
The leading dimension is the stride (in elements) to the beginning of the first 32 column x 8 row tile for the next 32-wide group of columns. For example, if the matrix has 33 columns and 1 row,
the leading dimension must be at least (32 * 8) * 1 = 256. |
| CUBLASLT_ORDER_COL32_2R_4R4 | Data is ordered in column-major ordered tiles of composite tiles with total 32 columns ands 32 rows. Element offset within the tile is calculated as (((row % 8) / 2 * 4 + row / 8) * 2 + row % 2) * 32 + col.
Leading dimension is the stride (in elements) to the beginning of the first 32 column x 32 row tile for the next 32-wide group of columns. E.g. if matrix has 33 columns and 1 row, then its leading dimensions
must be at least (32 * 32) * 1 = 1024. |





### 3.3.24. cublasLtPointerMode_t


[cublasLtPointerMode_t](#cublasltpointermode-t) is an enumerated type used to set the pointer mode for the scaling factors `alpha` and `beta`.


| Value | Description |
| --- | --- |
| CUBLASLT_POINTER_MODE_HOST = CUBLAS_POINTER_MODE_HOST | Matches CUBLAS_POINTER_MODE_HOST, and the pointer targets a single value host memory. |
| CUBLASLT_POINTER_MODE_DEVICE = CUBLAS_POINTER_MODE_DEVICE | Matches CUBLAS_POINTER_MODE_DEVICE, and the pointer targets a single value device memory. |
| CUBLASLT_POINTER_MODE_DEVICE_VECTOR = 2 | Pointers target device memory vectors of length equal to the number of rows of matrix D. |
| CUBLASLT_POINTER_MODE_ALPHA_DEVICE_VECTOR_BETA_ZERO = 3 | alpha pointer targets a device memory vector of length equal to the number of rows of matrix D, and beta is zero. |
| CUBLASLT_POINTER_MODE_ALPHA_DEVICE_VECTOR_BETA_HOST = 4 | alpha pointer targets a device memory vector of length equal to the number of rows of matrix D, and beta is a single value in host memory. |


> **Note**

Note
Only pointer modes CUBLASLT_POINTER_MODE_HOST and CUBLASLT_POINTER_MODE_DEVICE are supported when cublasLtBatchMode_t of any matrix is set to CUBLASLT_BATCH_MODE_POINTER_ARRAY or CUBLASLT_BATCH_MODE_GROUPED.





### 3.3.25. cublasLtPointerModeMask_t


[cublasLtPointerModeMask_t](#cublasltpointermodemask-t) is an enumerated type used to define and query the pointer mode capability.


| Value | Description |
| --- | --- |
| CUBLASLT_POINTER_MODE_MASK_HOST = 1 | See CUBLASLT_POINTER_MODE_HOST in cublasLtPointerMode_t. |
| CUBLASLT_POINTER_MODE_MASK_DEVICE = 2 | See CUBLASLT_POINTER_MODE_DEVICE in cublasLtPointerMode_t. |
| CUBLASLT_POINTER_MODE_MASK_DEVICE_VECTOR = 4 | See CUBLASLT_POINTER_MODE_DEVICE_VECTOR in cublasLtPointerMode_t |
| CUBLASLT_POINTER_MODE_MASK_ALPHA_DEVICE_VECTOR_BETA_ZERO = 8 | See CUBLASLT_POINTER_MODE_ALPHA_DEVICE_VECTOR_BETA_ZERO in cublasLtPointerMode_t |
| CUBLASLT_POINTER_MODE_MASK_ALPHA_DEVICE_VECTOR_BETA_HOST = 16 | See CUBLASLT_POINTER_MODE_ALPHA_DEVICE_VECTOR_BETA_HOST in cublasLtPointerMode_t |





### 3.3.26. cublasLtReductionScheme_t


[cublasLtReductionScheme_t](#cublasltreductionscheme-t) is an enumerated type used to specify a reduction scheme for the portions of the dot-product calculated in parallel (i.e., “split - K”).


| Value | Description |
| --- | --- |
| CUBLASLT_REDUCTION_SCHEME_NONE | Do not apply reduction. The dot-product will be performed in one sequence. |
| CUBLASLT_REDUCTION_SCHEME_INPLACE | Reduction is performed “in place” using the output buffer, parts are added up in the output data type. Workspace is only used for counters that guarantee sequentiality. |
| CUBLASLT_REDUCTION_SCHEME_COMPUTE_TYPE | Reduction done out of place in a user-provided workspace. The intermediate results are stored in the compute type in the workspace and reduced in a separate step. |
| CUBLASLT_REDUCTION_SCHEME_OUTPUT_TYPE | Reduction done out of place in a user-provided workspace. The intermediate results are stored in the output type in the workspace and reduced in a separate step. |
| CUBLASLT_REDUCTION_SCHEME_MASK | Allows all reduction schemes. |





### 3.3.27. cublasLtMatmulMatrixScale_t


[cublasLtMatmulMatrixScale_t](#cublasltmatmulmatrixscale-t) is an enumerated type used to specify scaling mode that defines how scaling factor pointers are interpreted.


| Value | Description |
| --- | --- |
| CUBLASLT_MATMUL_MATRIX_SCALE_SCALAR_32F | Scaling factors are single-precision scalars applied to the whole tensors (this mode is the default for fp8). This is the only value valid for CUBLASLT_MATMUL_DESC_D_SCALE_MODE when the D tensor uses a narrow precision data type. |
| CUBLASLT_MATMUL_MATRIX_SCALE_VEC16_UE4M3 | Scaling factors are tensors that contain a dedicated scaling factor stored as an 8-bit CUDA_R_8F_UE4M3 value for each 16-element block in the innermost dimension of the corresponding data tensor. |
| CUBLASLT_MATMUL_MATRIX_SCALE_VEC32_UE8M0 | Scaling factors are tensors that contain a dedicated scaling factor stored as an 8-bit CUDA_R_8F_UE8M0 value for each 32-element block in the innermost dimension of the corresponding data tensor. |
| CUBLASLT_MATMUL_MATRIX_SCALE_OUTER_VEC_32F | Scaling factors are vectors of CUDA_R_32F values. This mode is only applicable to matrices A and B, in which case the vectors are expected to have M and N elements respectively, and each (i, j)-th element of product of A and B is multiplied by i-th element of A scale and j-th element of B scale. |
| CUBLASLT_MATMUL_MATRIX_SCALE_VEC128_32F | Scaling factors are tensors that contain a dedicated CUDA_R_32F scaling factor for each 128-element block in the innermost dimension of the corresponding data tensor. |
| CUBLASLT_MATMUL_MATRIX_SCALE_BLK128x128_32F | Scaling factors are tensors that contain a dedicated CUDA_R_32F scaling factor for each 128x128-element block in the the corresponding data tensor. |
| CUBLASLT_MATMUL_MATRIX_SCALE_PER_BATCH_SCALAR_32F | Scaling factors are single-precision scalars applied successively to each matrix in a batch. This mode is only applicable to matrices A and B, in which case the scales are expected to have BATCH_COUNT elements. |





### 3.3.28. cublasLtBatchMode_t


| Value | Description |
| --- | --- |
| CUBLASLT_BATCH_MODE_STRIDED | The matrices of each instance of the batch are located at fixed offsets in number of elements from their locations in the previous instance. |
| CUBLASLT_BATCH_MODE_POINTER_ARRAY | The address of the matrix of each instance of the batch are read from device arrays of pointers. |
| CUBLASLT_BATCH_MODE_GROUPED | Experimental: The address of the matrix of each instance of the group are read from device arrays of pointers. Each group can have different columns, rows, and leading dimensions. See cublasLtMatrixLayout_t for more details. |





### 3.3.29. cublasLtEmulationDesc_t


cublasLtEmulationDesc_t is a pointer to an opaque structure holding the emulation descriptor. Use [cublasLtEmulationDescCreate()](#cublasltemulationdesccreate) to create a new emulation descriptor, and [cublasLtEmulationDescDestroy()](#cublasltemulationdescdestroy) to destroy it and release the resources.





### 3.3.30. cublasLtEmulationDescAttributes_t


cublasLtEmulationDescAttributes_t is an enumerated type used to configure floating point emulation parameters. See [Floating Point Emulation](#floating-point-emulation) documentation for more details.


| Value | Description | Data Type |
| --- | --- | --- |
| CUBLASLT_EMULATION_DESC_STRATEGY | Strategy, see cublasEmulationStrategy_t. Defines when to use floating point emulation algorithms. Default: EMULATION_STRATEGY_DEFAULT. | int32_t |
| CUBLASLT_EMULATION_DESC_SPECIAL_VALUES_SUPPORT | Special values support, see cudaEmulationSpecialValuesSupport_t. Defines a bit mask of special cases in floating-point representations that must be supported. Default: EMULATION_SPECIAL_VALUES_SUPPORT_DEFAULT. | int32_t |
| CUBLASLT_EMULATION_DESC_FIXEDPOINT_MANTISSA_CONTROL | Mantissa control, see cudaEmulationMantissaControl_t. For fixed-point emulation, defines how to compute the number of retained mantissa bits. See Floating Point Emulation documentation for more details. | int32_t |
| CUBLASLT_EMULATION_DESC_FIXEDPOINT_MAX_MANTISSA_BIT_COUNT | For fixed-point emulation only. An int32_t representing the maximum (up to quantization) number of mantissa bits to retain during fixed-point emulation. A default value of 0 allows the library to select a reasonable value based on device properties. Default: 0. | int32_t |
| CUBLASLT_EMULATION_DESC_FIXEDPOINT_MANTISSA_BIT_OFFSET | This parameter is for fixed-point emulation with CUDA_EMULATION_MANTISSA_CONTROL_DYNAMIC mantissa control (see cudaEmulationMantissaControl_t). An integer which can be used to bias the number of recommended mantissa bits. Default: 0. | int32_t |
| CUBLASLT_EMULATION_DESC_FIXEDPOINT_MANTISSA_BIT_COUNT_POINTER | This parameter is for fixed-point emulation. A device pointer which will contain the number of mantissa bits that were retained. If emulation is not used, the pointer will contain -1. Default: nullptr. | int32_t * |







| 值 | 描述 |
| --- | --- |
| CUBLASLT_BATCH_MODE_STRIDED | 批次中每个实例的矩阵以固定数量的元素偏移量位于前一实例的对应位置。 |
| CUBLASLT_BATCH_MODE_POINTER_ARRAY | 批次中每个实例的矩阵地址从设备指针数组中读取。 |
| CUBLASLT_BATCH_MODE_GROUPED | 实验性功能：每个组中实例的矩阵地址从设备指针数组中读取。每个组可以具有不同的列数、行数和前导维度。详见 cublasLtMatrixLayout_t。 |


cublasLtClusterShape_t is an enumerated type used to configure thread block cluster dimensions. Thread block clusters add an optional hierarchical level and are made up of thread blocks. Similar to thread blocks, these can be one, two, or three-dimensional. See also [Thread Block Clusters](https://docs.nvidia.com/cuda/cuda-c-programming-guide/index.html#thread-block-clusters).


| Value | Description |
| --- | --- |
| CUBLASLT_CLUSTER_SHAPE_AUTO | Cluster shape is automatically selected. |
| CUBLASLT_CLUSTER_SHAPE_1x1x1 | Cluster shape is 1 x 1 x 1. |
| CUBLASLT_CLUSTER_SHAPE_1x2x1 | Cluster shape is 1 x 2 x 1. |
| CUBLASLT_CLUSTER_SHAPE_1x4x1 | Cluster shape is 1 x 4 x 1. |
| CUBLASLT_CLUSTER_SHAPE_2x1x1 | Cluster shape is 2 x 1 x 1. |
| CUBLASLT_CLUSTER_SHAPE_2x2x1 | Cluster shape is 2 x 2 x 1. |
| CUBLASLT_CLUSTER_SHAPE_2x4x1 | Cluster shape is 2 x 4 x 1. |
| CUBLASLT_CLUSTER_SHAPE_4x1x1 | Cluster shape is 4 x 1 x 1. |
| CUBLASLT_CLUSTER_SHAPE_4x2x1 | Cluster shape is 4 x 2 x 1. |
| CUBLASLT_CLUSTER_SHAPE_4x4x1 | Cluster shape is 4 x 4 x 1. |
| CUBLASLT_CLUSTER_SHAPE_1x8x1 | Cluster shape is 1 x 8 x 1. |
| CUBLASLT_CLUSTER_SHAPE_8x1x1 | Cluster shape is 8 x 1 x 1. |
| CUBLASLT_CLUSTER_SHAPE_2x8x1 | Cluster shape is 2 x 8 x 1. |
| CUBLASLT_CLUSTER_SHAPE_8x2x1 | Cluster shape is 8 x 2 x 1. |
| CUBLASLT_CLUSTER_SHAPE_1x16x1 | Cluster shape is 1 x 16 x 1. |
| CUBLASLT_CLUSTER_SHAPE_16x1x1 | Cluster shape is 16 x 1 x 1. |
| CUBLASLT_CLUSTER_SHAPE_1x3x1 | Cluster shape is 1 x 3 x 1. |
| CUBLASLT_CLUSTER_SHAPE_1x5x1 | Cluster shape is 1 x 5 x 1. |
| CUBLASLT_CLUSTER_SHAPE_1x6x1 | Cluster shape is 1 x 6 x 1. |
| CUBLASLT_CLUSTER_SHAPE_1x7x1 | Cluster shape is 1 x 7 x 1. |
| CUBLASLT_CLUSTER_SHAPE_1x9x1 | Cluster shape is 1 x 9 x 1. |
| CUBLASLT_CLUSTER_SHAPE_1x10x1 | Cluster shape is 1 x 10 x 1. |
| CUBLASLT_CLUSTER_SHAPE_1x11x1 | Cluster shape is 1 x 11 x 1. |
| CUBLASLT_CLUSTER_SHAPE_1x12x1 | Cluster shape is 1 x 12 x 1. |
| CUBLASLT_CLUSTER_SHAPE_1x13x1 | Cluster shape is 1 x 13 x 1. |
| CUBLASLT_CLUSTER_SHAPE_1x14x1 | Cluster shape is 1 x 14 x 1. |
| CUBLASLT_CLUSTER_SHAPE_1x15x1 | Cluster shape is 1 x 15 x 1. |
| CUBLASLT_CLUSTER_SHAPE_2x3x1 | Cluster shape is 2 x 3 x 1. |
| CUBLASLT_CLUSTER_SHAPE_2x5x1 | Cluster shape is 2 x 5 x 1. |
| CUBLASLT_CLUSTER_SHAPE_2x6x1 | Cluster shape is 2 x 6 x 1. |
| CUBLASLT_CLUSTER_SHAPE_2x7x1 | Cluster shape is 2 x 7 x 1. |
| CUBLASLT_CLUSTER_SHAPE_3x1x1 | Cluster shape is 3 x 1 x 1. |
| CUBLASLT_CLUSTER_SHAPE_3x2x1 | Cluster shape is 3 x 2 x 1. |
| CUBLASLT_CLUSTER_SHAPE_3x3x1 | Cluster shape is 3 x 3 x 1. |
| CUBLASLT_CLUSTER_SHAPE_3x4x1 | Cluster shape is 3 x 4 x 1. |
| CUBLASLT_CLUSTER_SHAPE_3x5x1 | Cluster shape is 3 x 5 x 1. |
| CUBLASLT_CLUSTER_SHAPE_4x3x1 | Cluster shape is 4 x 3 x 1. |
| CUBLASLT_CLUSTER_SHAPE_5x1x1 | Cluster shape is 5 x 1 x 1. |
| CUBLASLT_CLUSTER_SHAPE_5x2x1 | Cluster shape is 5 x 2 x 1. |
| CUBLASLT_CLUSTER_SHAPE_5x3x1 | Cluster shape is 5 x 3 x 1. |
| CUBLASLT_CLUSTER_SHAPE_6x1x1 | Cluster shape is 6 x 1 x 1. |
| CUBLASLT_CLUSTER_SHAPE_6x2x1 | Cluster shape is 6 x 2 x 1. |
| CUBLASLT_CLUSTER_SHAPE_7x1x1 | Cluster shape is 7 x 1 x 1. |
| CUBLASLT_CLUSTER_SHAPE_7x2x1 | Cluster shape is 7 x 2 x 1. |
| CUBLASLT_CLUSTER_SHAPE_9x1x1 | Cluster shape is 9 x 1 x 1. |
| CUBLASLT_CLUSTER_SHAPE_10x1x1 | Cluster shape is 10 x 1 x 1. |
| CUBLASLT_CLUSTER_SHAPE_11x1x1 | Cluster shape is 11 x 1 x 1. |
| CUBLASLT_CLUSTER_SHAPE_12x1x1 | Cluster shape is 12 x 1 x 1. |
| CUBLASLT_CLUSTER_SHAPE_13x1x1 | Cluster shape is 13 x 1 x 1. |
| CUBLASLT_CLUSTER_SHAPE_14x1x1 | Cluster shape is 14 x 1 x 1. |
| CUBLASLT_CLUSTER_SHAPE_15x1x1 | Cluster shape is 15 x 1 x 1. |




cublasLtEmulationDesc_t是指向一个不透明结构的指针，该结构保存着仿真描述符。使用cublasLtEmulationDescCreate()创建一个新的仿真描述符，使用cublasLtEmulationDescDestroy()销毁它并释放资源。

`cublasLtEmulationDescAttributes_t` 是一个枚举类型，用于配置浮点模拟参数。更多信息请参见浮点模拟文档。

| 值 | 描述 | 数据类型 |
| --- | --- | --- |
| CUBLASLT_EMULATION_DESC_STRATEGY | 策略，参见 `cublasEmulationStrategy_t`。定义何时使用浮点模拟算法。默认值：EMULATION_STRATEGY_DEFAULT。 | int32_t |
| CUBLASLT_EMULATION_DESC_SPECIAL_VALUES_SUPPORT | 特殊值支持，参见 `cudaEmulationSpecialValuesSupport_t`。定义浮点表示中必须支持的特殊情况位掩码。默认值：EMULATION_SPECIAL_VALUES_SUPPORT_DEFAULT。 | int32_t |
| CUBLASLT_EMULATION_DESC_FIXEDPOINT_MANTISSA_CONTROL | 尾数控制，参见 `cudaEmulationMantissaControl_t`。对于定点模拟，定义如何计算保留的尾数位数。更多信息请参见浮点模拟文档。 | int32_t |
| CUBLASLT_EMULATION_DESC_FIXEDPOINT_MAX_MANTISSA_BIT_COUNT | 仅适用于定点模拟。一个 int32_t 值，表示在定点模拟期间保留的最大（考虑量化）尾数位数。默认值为 0，允许库根据设备属性选择合理的值。默认值：0。 | int32_t |
| CUBLASLT_EMULATION_DESC_FIXEDPOINT_MANTISSA_BIT_OFFSET | 此参数适用于使用 CUDA_EMULATION_MANTISSA_CONTROL_DYNAMIC 尾数控制（参见 `cudaEmulationMantissaControl_t`）的定点模拟。一个可用于偏移推荐尾数位数的整数。默认值：0。 | int32_t |
| CUBLASLT_EMULATION_DESC_FIXEDPOINT_MANTISSA_BIT_COUNT_POINTER | 此参数适用于定点模拟。一个设备指针，将包含保留的尾数位数。如果未使用模拟，指针将包含 -1。默认值：nullptr。 | int32_t * |

`cublasLtEpilogue_t` 是一个枚举类型，用于设置后处理选项。

| 值 | 描述 |
| --- | --- |
| CUBLASLT_EPILOGUE_DEFAULT = 1 | 无特殊后处理，仅在必要时对结果进行缩放和量化。 |
| CUBLASLT_EPILOGUE_RELU = 2 | 对结果应用 ReLU 点式变换 (x := max(x, 0))。 |
| CUBLASLT_EPILOGUE_RELU_AUX = CUBLASLT_EPILOGUE_RELU | 128 | 对结果应用 ReLU 点式变换 (x := max(x, 0))。此尾端模式产生一个额外输出，参见 cublasLtMatmulDescAttributes_t 中的 CUBLASLT_MATMUL_DESC_EPILOGUE_AUX_POINTER。 |
| CUBLASLT_EPILOGUE_BIAS = 4 | 应用来自偏置向量的（广播）偏置。偏置向量长度必须与矩阵 D 的行数匹配，且必须为压缩格式（即向量元素之间的步幅为 1）。偏置被广播到所有列，并在最终后处理之前添加。 |
| CUBLASLT_EPILOGUE_RELU_BIAS = CUBLASLT_EPILOGUE_RELU = CUBLASLT_EPILOGUE_BIAS | 先应用偏置，然后应用 ReLU 变换。 |
| CUBLASLT_EPILOGUE_RELU_AUX_BIAS = CUBLASLT_EPILOGUE_RELU_AUX = CUBLASLT_EPILOGUE_BIAS | 先应用偏置，然后应用 ReLU 变换。此尾端模式产生一个额外输出，参见 cublasLtMatmulDescAttributes_t 中的 CUBLASLT_MATMUL_DESC_EPILOGUE_AUX_POINTER。 |
| CUBLASLT_EPILOGUE_DRELU = 8 | 128 | 将 ReLU 梯度应用于 matmul 输出。将 ReLU 梯度存储在输出矩阵中。此尾端模式需要一个额外输入，参见 cublasLtMatmulDescAttributes_t 中的 CUBLASLT_MATMUL_DESC_EPILOGUE_AUX_POINTER。 |
| CUBLASLT_EPILOGUE_DRELU_BGRAD = CUBLASLT_EPILOGUE_DRELU | 16 | 独立地将 ReLU 和偏置梯度应用于 matmul 输出。将 ReLU 梯度存储在输出矩阵中，并将偏置梯度存储在偏置缓冲区中（参见 CUBLASLT_MATMUL_DESC_BIAS_POINTER）。此尾端模式需要一个额外输入，参见 cublasLtMatmulDescAttributes_t 中的 CUBLASLT_MATMUL_DESC_EPILOGUE_AUX_POINTER。 |
| CUBLASLT_EPILOGUE_GELU = 32 | 对结果应用 GELU 点式变换 (x := GELU(x))。 |
| CUBLASLT_EPILOGUE_GELU_AUX = CUBLASLT_EPILOGUE_GELU | 128 | 对结果应用 GELU 点式变换 (x := GELU(x))。此尾端模式将 GELU 输入作为单独矩阵输出（用于训练）。参见 cublasLtMatmulDescAttributes_t 中的 CUBLASLT_MATMUL_DESC_EPILOGUE_AUX_POINTER。 |
| CUBLASLT_EPILOGUE_GELU_BIAS = CUBLASLT_EPILOGUE_GELU | CUBLASLT_EPILOGUE_BIAS | 应用偏置，然后应用 GELU 变换⁵。 |
| CUBLASLT_EPILOGUE_GELU_AUX_BIAS = CUBLASLT_EPILOGUE_GELU_AUX | CUBLASLT_EPILOGUE_BIAS | 应用偏置，然后应用 GELU 变换⁵。此尾端模式将 GELU 输入作为单独矩阵输出（用于训练）。参见 cublasLtMatmulDescAttributes_t 中的 CUBLASLT_MATMUL_DESC_EPILOGUE_AUX_POINTER。 |
| CUBLASLT_EPILOGUE_DGELU = 64 | 128 | 将 GELU 梯度应用于 matmul 输出。将 GELU 梯度存储在输出矩阵中。此尾端模式需要一个额外输入，参见 cublasLtMatmulDescAttributes_t 中的 CUBLASLT_MATMUL_DESC_EPILOGUE_AUX_POINTER。 |
| CUBLASLT_EPILOGUE_DGELU_BGRAD = CUBLASLT_EPILOGUE_DGELU | 16 | 独立地将 GELU 和偏置梯度应用于 matmul 输出。将 GELU 梯度存储在输出矩阵中，并将偏置梯度存储在偏置缓冲区中（参见 CUBLASLT_MATMUL_DESC_BIAS_POINTER）。此尾端模式需要一个额外输入，参见 cublasLtMatmulDescAttributes_t 中的 CUBLASLT_MATMUL_DESC_EPILOGUE_AUX_POINTER。 |
| CUBLASLT_EPILOGUE_BGRADA = 256 | 将偏置梯度应用于输入矩阵 A。偏置大小对应于矩阵 D 的行数。归约发生在 GEMM 的 "k" 维度上。将偏置梯度存储在偏置缓冲区中，参见 cublasLtMatmulDescAttributes_t 中的 CUBLASLT_MATMUL_DESC_BIAS_POINTER。 |
| CUBLASLT_EPILOGUE_BGRADB = 512 | 将偏置梯度应用于输入矩阵 B。偏置大小对应于矩阵 D 的列数。归约发生在 GEMM 的 "k" 维度上。将偏置梯度存储在偏置缓冲区中，参见 cublasLtMatmulDescAttributes_t 中的 CUBLASLT_MATMUL_DESC_BIAS_POINTER。 |


**注意事项：**


**⁵(1,2)**
: GELU（高斯误差线性单元）由以下公式近似：\({0.5}x\left( 1 + \text{tanh}\left( \sqrt{2/\pi}\left( x + {0.044715}x^{3} \right) \right) \right)\)



> **注意**

当任何矩阵的 `cublasLtBatchMode_t` 设置为 `CUBLASLT_BATCH_MODE_POINTER_ARRAY` 时，仅支持 `CUBLASLT_EPILOGUE_DEFAULT`。
当任何矩阵的 `cublasLtBatchMode_t` 设置为 `CUBLASLT_BATCH_MODE_GROUPED` 时，仅支持 `CUBLASLT_EPILOGUE_DEFAULT` 和 `CUBLASLT_EPILOGUE_BIAS`。

`cublasLtHandle_t` 类型是一个指向不透明结构的指针类型，该不透明结构保存了 cuBLASLt 库上下文。使用 `cublasLtCreate()` 初始化 cuBLASLt 库上下文并返回一个指向保存 cuBLASLt 库上下文的不透明结构的句柄，使用 `cublasLtDestroy()` 销毁先前创建的 cuBLASLt 库上下文描述符并释放相关资源。

> **注意**

注意
cuBLAS 句柄 (`cublasHandle_t`) 封装了一个 cuBLASLt 句柄。任何有效的 `cublasHandle_t` 都可以通过简单的类型转换来替代 `cublasLtHandle_t` 使用。但是，与 cuBLAS 句柄不同，cuBLASLt 句柄不与任何特定的 CUDA 上下文绑定，但与图形上下文绑定的 CUDA 上下文除外（从 CUDA 12.8 开始）。如果在当前 CUDA 上下文与图形上下文绑定时创建 cuBLASLt 句柄，则 cuBLASLt 会检测相应的共享内存限制并将其记录在句柄中。


Experimental: cublasLtIntegerWidth_t is an enumerated type used to indicate the width of integers in the dimensions arrays of a grouped matrix.


| Value | Description |
| --- | --- |
| CUBLASLT_INTEGER_WIDTH_32 | 32-bit integer width. |
| CUBLASLT_INTEGER_WIDTH_64 | 64-bit integer width. |




cublasLtMatmulAlgo_t 是一个不透明结构体，用于保存矩阵乘法算法的描述。该结构体可以被简单地序列化，并在后续使用相同版本的 cuBLAS 库时恢复使用，以节省再次选择正确配置的时间。


cublasLtMatmulAlgoCapAttributes_t enumerates matrix multiplication algorithm capability attributes that can be retrieved from an initialized cublasLtMatmulAlgo_t descriptor using cublasLtMatmulAlgoCapGetAttribute().


| Value | Description | Data Type |
| --- | --- | --- |
| CUBLASLT_ALGO_CAP_SPLITK_SUPPORT | Support for split-K. Boolean (0 or 1) to express if split-K implementation is supported. 0 means no support, and supported otherwise. See CUBLASLT_ALGO_CONFIG_SPLITK_NUM of cublasLtMatmulAlgoConfigAttributes_t. | int32_t |
| CUBLASLT_ALGO_CAP_REDUCTION_SCHEME_MASK | Mask to express the types of reduction schemes supported, see cublasLtReductionScheme_t. If the reduction scheme is not masked out then it is supported. For example: int isReductionSchemeComputeTypeSupported ? (reductionSchemeMask & CUBLASLT_REDUCTION_SCHEME_COMPUTE_TYPE) == CUBLASLT_REDUCTION_SCHEME_COMPUTE_TYPE ? 1 : 0; | uint32_t |
| CUBLASLT_ALGO_CAP_CTA_SWIZZLING_SUPPORT | Support for CTA-swizzling. Boolean (0 or 1) to express if CTA-swizzling implementation is supported. 0 means no support, and 1 means supported value of 1; other values are reserved. See also CUBLASLT_ALGO_CONFIG_CTA_SWIZZLING of cublasLtMatmulAlgoConfigAttributes_t. | uint32_t |
| CUBLASLT_ALGO_CAP_STRIDED_BATCH_SUPPORT | Support strided batch. 0 means no support, supported otherwise. | int32_t |
| CUBLASLT_ALGO_CAP_POINTER_ARRAY_BATCH_SUPPORT | Support pointer array batch. 0 means no support, supported otherwise. | int32_t |
| CUBLASLT_ALGO_CAP_POINTER_ARRAY_GROUPED_SUPPORT | Experimental: Support pointer array grouped batch. 0 means no support, supported otherwise. See CUBLASLT_BATCH_MODE_GROUPED of cublasLtBatchMode_t. | int32_t |
| CUBLASLT_ALGO_CAP_OUT_OF_PLACE_RESULT_SUPPORT | Support results out of place (D != C in D = alpha.A.B + beta.C). 0 means no support, supported otherwise. | int32_t |
| CUBLASLT_ALGO_CAP_UPLO_SUPPORT | Syrk (symmetric rank k update)/herk (Hermitian rank k update) support (on top of regular gemm). 0 means no support, supported otherwise. | int32_t |
| CUBLASLT_ALGO_CAP_TILE_IDS | The tile ids possible to use. See cublasLtMatmulTile_t. If no tile ids are supported then use CUBLASLT_MATMUL_TILE_UNDEFINED. Use cublasLtMatmulAlgoCapGetAttribute() with sizeInBytes = 0 to query the actual count. | uint32_t[] |
| CUBLASLT_ALGO_CAP_STAGES_IDS | The stages ids possible to use. See cublasLtMatmulStages_t. If no stages ids are supported then use CUBLASLT_MATMUL_STAGES_UNDEFINED. Use cublasLtMatmulAlgoCapGetAttribute() with sizeInBytes = 0 to query the actual count. | uint32_t[] |
| CUBLASLT_ALGO_CAP_CUSTOM_OPTION_MAX | Custom option range is from 0 to CUBLASLT_ALGO_CAP_CUSTOM_OPTION_MAX (inclusive). See CUBLASLT_ALGO_CONFIG_CUSTOM_OPTION of cublasLtMatmulAlgoConfigAttributes_t . | int32_t |
| CUBLASLT_ALGO_CAP_MATHMODE_IMPL | Indicates whether the algorithm is using regular compute or tensor operations. 0 means regular compute, 1 means tensor operations.
DEPRECATED | int32_t |
| CUBLASLT_ALGO_CAP_GAUSSIAN_IMPL | Indicate whether the algorithm implements the Gaussian optimization of complex matrix multiplication. 0 means regular compute; 1 means Gaussian. See cublasMath_t.
DEPRECATED | int32_t |
| CUBLASLT_ALGO_CAP_CUSTOM_MEMORY_ORDER | Indicates whether the algorithm supports custom (not COL or ROW memory order). 0 means only COL and ROW memory order is allowed, non-zero means that algo might have different requirements. See cublasLtOrder_t. | int32_t |
| CUBLASLT_ALGO_CAP_POINTER_MODE_MASK | Bitmask enumerating the pointer modes the algorithm supports. See cublasLtPointerModeMask_t. | uint32_t |
| CUBLASLT_ALGO_CAP_EPILOGUE_MASK | Bitmask enumerating the kinds of postprocessing algorithm supported in the epilogue. See cublasLtEpilogue_t. | uint32_t |
| CUBLASLT_ALGO_CAP_LD_NEGATIVE | Support for negative leading dimension for all of the matrices. 0 means no support, supported otherwise. | uint32_t |
| CUBLASLT_ALGO_CAP_NUMERICAL_IMPL_FLAGS | Details about algorithm’s implementation that affect it’s numerical behavior. See cublasLtNumericalImplFlags_t. | uint64_t |
| CUBLASLT_ALGO_CAP_MIN_ALIGNMENT_A_BYTES | Minimum alignment required for A matrix in bytes. | uint32_t |
| CUBLASLT_ALGO_CAP_MIN_ALIGNMENT_B_BYTES | Minimum alignment required for B matrix in bytes. | uint32_t |
| CUBLASLT_ALGO_CAP_MIN_ALIGNMENT_C_BYTES | Minimum alignment required for C matrix in bytes. | uint32_t |
| CUBLASLT_ALGO_CAP_MIN_ALIGNMENT_D_BYTES | Minimum alignment required for D matrix in bytes. | uint32_t |
| CUBLASLT_ALGO_CAP_FLOATING_POINT_EMULATION_SUPPORT | Support for for floating point emulation. See Floating Point Emulation. | int32_t |




`cublasLtMatmulAlgoConfigAttributes_t` 是一个枚举类型，包含 cuBLASLt 矩阵乘法算法的配置属性。配置属性是算法特定的，可以进行设置。给定算法的属性配置应与其能力属性一致。使用 `cublasLtMatmulAlgoConfigGetAttribute()` 和 `cublasLtMatmulAlgoConfigSetAttribute()` 获取和设置矩阵乘法算法描述符的属性值。

| 值 | 描述 | 数据类型 |
| --- | --- | --- |
| CUBLASLT_ALGO_CONFIG_ID | 只读属性。算法索引。参见 `cublasLtMatmulAlgoGetIds()`。由 `cublasLtMatmulAlgoInit()` 设置。 | int32_t |
| CUBLASLT_ALGO_CONFIG_TILE_ID | 瓦片ID。参见 `cublasLtMatmulTile_t`。默认值：CUBLASLT_MATMUL_TILE_UNDEFINED。 | uint32_t |
| CUBLASLT_ALGO_CONFIG_STAGES_ID | stages ID，参见 `cublasLtMatmulStages_t`。默认值：CUBLASLT_MATMUL_STAGES_UNDEFINED。 | uint32_t |
| CUBLASLT_ALGO_CONFIG_SPLITK_NUM | K 分割数量。如果 K 分割数量大于一，矩阵乘法的 SPLITK_NUM 部分将被并行计算。结果将根据 `CUBLASLT_ALGO_CONFIG_REDUCTION_SCHEME` 进行归约。 | uint32_t |
| CUBLASLT_ALGO_CONFIG_REDUCTION_SCHEME | 当 splitK 值 > 1 时使用的归约方案。默认值：CUBLASLT_REDUCTION_SCHEME_NONE。参见 `cublasLtReductionScheme_t`。 | uint32_t |
| CUBLASLT_ALGO_CONFIG_CTA_SWIZZLING | 启用/禁用 CTA 混洗。更改 CUDA 网格坐标到矩阵部分的映射。可能的值：0 和 1；其他值保留。 | uint32_t |
| CUBLASLT_ALGO_CONFIG_CUSTOM_OPTION | 自定义选项值。每个算法可以支持一些不适合其他配置属性描述的自定义选项。参见 `cublasLtMatmulAlgoCapAttributes_t` 的 `CUBLASLT_ALGO_CAP_CUSTOM_OPTION_MAX` 以获取特定情况下的可接受范围。 | uint32_t |
| CUBLASLT_ALGO_CONFIG_INNER_SHAPE_ID | 内部形状ID。参见 `cublasLtMatmulInnerShape_t`。默认值：CUBLASLT_MATMUL_INNER_SHAPE_UNDEFINED。 | uint16_t |
| CUBLASLT_ALGO_CONFIG_CLUSTER_SHAPE_ID | 簇形状ID。参见 `cublasLtClusterShape_t`。默认值：CUBLASLT_CLUSTER_SHAPE_AUTO。 | uint16_t |

`cublasLtMatmulDesc_t` 是指向一个不透明结构的指针，该结构保存了矩阵乘法运算 `cublasLtMatmul()` 的描述信息。可以通过调用 `cublasLtMatmulDescCreate()` 创建描述符，并通过调用 `cublasLtMatmulDescDestroy()` 进行销毁。


cublasLtMatmulDescAttributes_t is a descriptor structure containing the attributes that define the specifics of the matrix multiply operation. Use cublasLtMatmulDescGetAttribute() and cublasLtMatmulDescSetAttribute() to get and set the attribute value of a matmul descriptor.


| Value | Description | Data Type |
| --- | --- | --- |
| CUBLASLT_MATMUL_DESC_COMPUTE_TYPE | Compute type. Defines the data type used for multiply and accumulate operations, and the accumulator during the matrix multiplication. See cublasComputeType_t. | int32_t |
| CUBLASLT_MATMUL_DESC_SCALE_TYPE | Scale type. Defines the data type of the scaling factors alpha and beta. The accumulator value and the value from matrix C are typically converted to scale type before final scaling. The value is then converted from scale type to the type of matrix D before storing in memory. The default value depends on CUBLASLT_MATMUL_DESC_COMPUTE_TYPE. See cudaDataType_t. | int32_t |
| CUBLASLT_MATMUL_DESC_POINTER_MODE | Specifies alpha and beta are passed by reference, whether they are scalars on the host or on the device, or device vectors. Default value is: CUBLASLT_POINTER_MODE_HOST (i.e., on the host). See cublasLtPointerMode_t. | int32_t |
| CUBLASLT_MATMUL_DESC_TRANSA | Specifies the type of transformation operation that should be performed on matrix A. Default value is: CUBLAS_OP_N (i.e., non-transpose operation). See cublasOperation_t. | int32_t |
| CUBLASLT_MATMUL_DESC_TRANSB | Specifies the type of transformation operation that should be performed on matrix B. Default value is: CUBLAS_OP_N (i.e., non-transpose operation). See cublasOperation_t. | int32_t |
| CUBLASLT_MATMUL_DESC_TRANSC | Specifies the type of transformation operation that should be performed on matrix C. Currently only CUBLAS_OP_N is supported. Default value is: CUBLAS_OP_N (i.e., non-transpose operation). See cublasOperation_t. | int32_t |
| CUBLASLT_MATMUL_DESC_FILL_MODE | Indicates whether the lower or upper part of the dense matrix was filled, and consequently should be used by the function. Currently this flag is not supported for bfloat16 or FP8 data types and is not supported on the following GPUs: Hopper, Blackwell. Default value is: CUBLAS_FILL_MODE_FULL. See cublasFillMode_t. | int32_t |
| CUBLASLT_MATMUL_DESC_EPILOGUE | Epilogue function. See cublasLtEpilogue_t. Default value is: CUBLASLT_EPILOGUE_DEFAULT. | uint32_t |
| CUBLASLT_MATMUL_DESC_BIAS_POINTER | Bias or Bias gradient vector pointer in the device memory.

Input vector with length that matches the number of rows of matrix D when one of the following epilogues is used: CUBLASLT_EPILOGUE_BIAS, CUBLASLT_EPILOGUE_RELU_BIAS, CUBLASLT_EPILOGUE_RELU_AUX_BIAS, CUBLASLT_EPILOGUE_GELU_BIAS, CUBLASLT_EPILOGUE_GELU_AUX_BIAS.
Output vector with length that matches the number of rows of matrix D when one of the following epilogues is used: CUBLASLT_EPILOGUE_DRELU_BGRAD, CUBLASLT_EPILOGUE_DGELU_BGRAD, CUBLASLT_EPILOGUE_BGRADA.
Output vector with length that matches the number of columns of matrix D when one of the following epilogues is used: CUBLASLT_EPILOGUE_BGRADB.

Bias vector elements are the same type as alpha and beta (see CUBLASLT_MATMUL_DESC_SCALE_TYPE in this table) when matrix D datatype is CUDA_R_8I and same as matrix D datatype otherwise. See the datatypes table under cublasLtMatmul() for detailed mapping. Default value is: NULL. | void * / const void * |
| CUBLASLT_MATMUL_DESC_BIAS_BATCH_STRIDE | Stride (in elements) to the next bias or bias gradient vector for strided batch operations. If cublasLtBatchMode_t of any matrix is set to CUBLASLT_BATCH_MODE_GROUPED and CUBLASLT_MATMUL_DESC_EPILOGUE includes CUBLASLT_EPILOGUE_BIAS then CUBLASLT_MATMUL_DESC_BIAS_BATCH_STRIDE must be set to 1. The default value is 0. | int64_t |
| CUBLASLT_MATMUL_DESC_EPILOGUE_AUX_POINTER | Pointer for epilogue auxiliary buffer.

Output vector for ReLu bit-mask in forward pass when CUBLASLT_EPILOGUE_RELU_AUX or CUBLASLT_EPILOGUE_RELU_AUX_BIAS epilogue is used.
Input vector for ReLu bit-mask in backward pass when CUBLASLT_EPILOGUE_DRELU or CUBLASLT_EPILOGUE_DRELU_BGRAD epilogue is used.
Output of GELU input matrix in forward pass when CUBLASLT_EPILOGUE_GELU_AUX_BIAS epilogue is used.
Input of GELU input matrix for backward pass when CUBLASLT_EPILOGUE_DGELU or CUBLASLT_EPILOGUE_DGELU_BGRAD epilogue is used.

For aux data type, see CUBLASLT_MATMUL_DESC_EPILOGUE_AUX_DATA_TYPE. Routines that don’t dereference this pointer, like cublasLtMatmulAlgoGetHeuristic() depend on its value to determine expected pointer alignment. Requires setting the CUBLASLT_MATMUL_DESC_EPILOGUE_AUX_LD attribute. | void * / const void * |
| CUBLASLT_MATMUL_DESC_EPILOGUE_AUX_LD | Leading dimension for epilogue auxiliary buffer.

ReLu bit-mask matrix leading dimension in elements (i.e. bits) when CUBLASLT_EPILOGUE_RELU_AUX, CUBLASLT_EPILOGUE_RELU_AUX_BIAS, CUBLASLT_EPILOGUE_DRELU_BGRAD, or CUBLASLT_EPILOGUE_DRELU_BGRAD epilogue is used. Must be divisible by 128 and be no less than the number of rows in the output matrix.
GELU input matrix leading dimension in elements when CUBLASLT_EPILOGUE_GELU_AUX_BIAS, CUBLASLT_EPILOGUE_DGELU,  or CUBLASLT_EPILOGUE_DGELU_BGRAD epilogue used. Must be divisible by 8 and be no less than the number of rows in the output matrix. | int64_t |
| CUBLASLT_MATMUL_DESC_EPILOGUE_AUX_BATCH_STRIDE | Batch stride for epilogue auxiliary buffer.

ReLu bit-mask matrix batch stride in elements (i.e. bits) when CUBLASLT_EPILOGUE_RELU_AUX, CUBLASLT_EPILOGUE_RELU_AUX_BIAS or CUBLASLT_EPILOGUE_DRELU_BGRAD epilogue is used. Must be divisible by 128.
GELU input matrix batch stride in elements when CUBLASLT_EPILOGUE_GELU_AUX_BIAS, CUBLASLT_EPILOGUE_DRELU, or CUBLASLT_EPILOGUE_DGELU_BGRAD epilogue used. Must be divisible by 8.

Default value: 0. | int64_t |
| CUBLASLT_MATMUL_DESC_ALPHA_VECTOR_BATCH_STRIDE | Batch stride for alpha vector. Used together with CUBLASLT_POINTER_MODE_ALPHA_DEVICE_VECTOR_BETA_HOST when matrix D’s CUBLASLT_MATRIX_LAYOUT_BATCH_COUNT is greater than 1. If CUBLASLT_POINTER_MODE_ALPHA_DEVICE_VECTOR_BETA_ZERO is set then CUBLASLT_MATMUL_DESC_ALPHA_VECTOR_BATCH_STRIDE must be set to 0 as this mode doesn’t support batched alpha vector. If cublasLtBatchMode_t of any matrix is not set to CUBLASLT_BATCH_MODE_STRIDED then CUBLASLT_MATMUL_DESC_ALPHA_VECTOR_BATCH_STRIDE must be set to 0. Default value: 0. | int64_t |
| CUBLASLT_MATMUL_DESC_SM_COUNT_TARGET | Number of SMs to target for parallel execution. Optimizes heuristics for execution on a different number of SMs when user expects a concurrent stream to be using some of the device resources. Default value: 0. | int32_t |
| CUBLASLT_MATMUL_DESC_A_SCALE_POINTER | Device pointer to the scale factor value that converts data in matrix A to the compute data type range. The scaling factor must have the same type as the compute type. If not specified, or set to NULL, the scaling factor is assumed to be 1. If set for an unsupported matrix data, scale, and compute type combination, calling cublasLtMatmul() will return CUBLAS_INVALID_VALUE. Default value: NULL | const void * |
| CUBLASLT_MATMUL_DESC_B_SCALE_POINTER | Equivalent to CUBLASLT_MATMUL_DESC_A_SCALE_POINTER for matrix B. Default value: NULL | const void * |
| CUBLASLT_MATMUL_DESC_C_SCALE_POINTER | Equivalent to CUBLASLT_MATMUL_DESC_A_SCALE_POINTER for matrix C. Default value: NULL | const void * |
| CUBLASLT_MATMUL_DESC_D_SCALE_POINTER | Equivalent to CUBLASLT_MATMUL_DESC_A_SCALE_POINTER for matrix D. Default value: NULL | const void * |
| CUBLASLT_MATMUL_DESC_AMAX_D_POINTER | Device pointer to the memory location that on completion will be set to the maximum of absolute values in the output matrix. The computed value has the same type as the compute type. If not specified, or set to NULL, the maximum absolute value is not computed. If set for an unsupported matrix data, scale, and compute type combination, calling cublasLtMatmul() will return CUBLAS_INVALID_VALUE. Default value: NULL | void * |
| CUBLASLT_MATMUL_DESC_EPILOGUE_AUX_DATA_TYPE | The type of the data that will be stored in CUBLASLT_MATMUL_DESC_EPILOGUE_AUX_POINTER. If unset (or set to the default value of -1), the data type is set to be the output matrix element data type (DType) with some exceptions:

ReLu uses a bit-mask.
For FP8 kernels with an output type (DType) of CUDA_R_8F_E4M3, the data type can be set to a non-default value if:


AType and BType are CUDA_R_8F_E4M3.
Bias Type is CUDA_R_16F.
CType is CUDA_R_16BF or CUDA_R_16F
CUBLASLT_MATMUL_DESC_EPILOGUE is set to CUBLASLT_EPILOGUE_GELU_AUX

When CType is CUDA_R_16F, the data type may be set to CUDA_R_16F or CUDA_R_8F_E4M3. When CType is CUDA_R_16BF, the data type may be set to CUDA_R_16BF. Otherwise, the data type should be left unset or set to the default value of -1.
If set for an unsupported matrix data, scale, and compute type combination, calling cublasLtMatmul() will return CUBLAS_INVALID_VALUE. Default value: -1 | int32_t (cudaDataType_t) |
| CUBLASLT_MATMUL_DESC_EPILOGUE_AUX_SCALE_POINTER | Device pointer to the scaling factor value to convert results from compute type data range to storage data range in the auxiliary matrix that is set via CUBLASLT_MATMUL_DESC_EPILOGUE_AUX_POINTER. The scaling factor value must have the same type as the compute type. If not specified, or set to NULL, the scaling factor is assumed to be 1. If set for an unsupported matrix data, scale, and compute type combination, calling cublasLtMatmul() will return CUBLAS_INVALID_VALUE. Default value: NULL | void * |
| CUBLASLT_MATMUL_DESC_EPILOGUE_AUX_AMAX_POINTER | Device pointer to the memory location that on completion will be set to the maximum of absolute values in the buffer that is set via CUBLASLT_MATMUL_DESC_EPILOGUE_AUX_POINTER. The computed value has the same type as the compute type. If not specified, or set to NULL, the maximum absolute value is not computed. If set for an unsupported matrix data, scale, and compute type combination, calling cublasLtMatmul() will return CUBLAS_INVALID_VALUE. Default value: NULL | void * |
| CUBLASLT_MATMUL_DESC_FAST_ACCUM | Flag for managing FP8 fast accumulation mode. When enabled, on some GPUs problem execution might be faster but at the cost of lower accuracy because intermediate results will not periodically be promoted to a higher precision. Currently this flag has an effect on the following GPUs: Ada, Hopper. Default value: 0 - fast accumulation mode is disabled | int8_t |
| CUBLASLT_MATMUL_DESC_BIAS_DATA_TYPE | Type of the bias or bias gradient vector in the device memory. Bias case: see CUBLASLT_EPILOGUE_BIAS. If unset (or set to the default value of -1), the bias vector elements are the same type as the elements of the output matrix (Dtype) with the following exceptions:

IMMA kernels with computeType=CUDA_R_32I and Ctype=CUDA_R_8I where the bias vector elements are the same type as alpha, beta (CUBLASLT_MATMUL_DESC_SCALE_TYPE=CUDA_R_32F)
For FP8 kernels with an output type of CUDA_R_32F, CUDA_R_8F_E4M3 or CUDA_R_8F_E5M2. See cublasLtMatmul() for more details.

Default value: -1 | int32_t (cudaDataType_t) |
| CUBLASLT_MATMUL_DESC_A_SCALE_MODE | Scaling mode that defines how the matrix scaling factor for matrix A is interpreted. Default value: 0. See cublasLtMatmulMatrixScale_t. | int32_t |
| CUBLASLT_MATMUL_DESC_B_SCALE_MODE | Scaling mode that defines how the matrix scaling factor for matrix B is interpreted. Default value: 0. See cublasLtMatmulMatrixScale_t. | int32_t |
| CUBLASLT_MATMUL_DESC_C_SCALE_MODE | Scaling mode that defines how the matrix scaling factor for matrix C is interpreted. Default value: 0. See cublasLtMatmulMatrixScale_t. | int32_t |
| CUBLASLT_MATMUL_DESC_D_SCALE_MODE | Scaling mode that defines how the matrix scaling factor for matrix D is interpreted. Default value: 0. See cublasLtMatmulMatrixScale_t. | int32_t |
| CUBLASLT_MATMUL_DESC_EPILOGUE_AUX_SCALE_MODE | Scaling mode that defines how the matrix scaling factor for the auxiliary matrix is interpreted. Default value: 0. See cublasLtMatmulMatrixScale_t. | int32_t |
| CUBLASLT_MATMUL_DESC_D_OUT_SCALE_POINTER | Device pointer to the scale factors that are used to convert data in matrix D to the compute data type range. The scaling factor value type is defined by the scaling mode (see CUBLASLT_MATMUL_DESC_D_OUT_SCALE_MODE). If set for an unsupported matrix data, scale, scale mode, and compute type combination, or missing for a supported combination, then calling cublasLtMatmul() will return CUBLAS_INVALID_VALUE. Default value: NULL. | void * |
| CUBLASLT_MATMUL_DESC_D_OUT_SCALE_MODE | Scaling mode that defines how the output matrix scaling factor for matrix D is interpreted. Default value: 0. See cublasLtMatmulMatrixScale_t. | int32_t |
| CUBLASLT_MATMUL_DESC_EMULATION_DESCRIPTOR | Emulation descriptor to configure floating point emulation parameters. Default value: NULL. | int32_t |
| CUBLASLT_MATMUL_DESC_ALPHA_BATCH_STRIDE | Experimental: Batch stride for alpha. Applicable when matrix D’s CUBLASLT_MATRIX_LAYOUT_BATCH_COUNT is greater than 1. Supported values are 0 and 1. Default value is 0. When the value is set to 1, the parameter alpha of cublasLtMatmul() must contain a device array of pointers of length CUBLASLT_MATRIX_LAYOUT_BATCH_COUNT. This setting is currently only supported if cublasLtBatchMode_t of all matrices is set to CUBLASLT_BATCH_MODE_GROUPED and CUBLASLT_MATMUL_DESC_POINTER_MODE is set to CUBLASLT_POINTER_MODE_DEVICE. | int64_t |
| CUBLASLT_MATMUL_DESC_BETA_BATCH_STRIDE | Experimental: Batch stride for beta. Applicable when matrix D’s CUBLASLT_MATRIX_LAYOUT_BATCH_COUNT is greater than 1. Supported values are 0 and 1. Default value is 0. When the value is set to 1, the parameter beta of cublasLtMatmul() must contain a device array of pointers of length CUBLASLT_MATRIX_LAYOUT_BATCH_COUNT. This setting is currently only supported if cublasLtBatchMode_t of all matrices is set to CUBLASLT_BATCH_MODE_GROUPED and CUBLASLT_MATMUL_DESC_POINTER_MODE is set to CUBLASLT_POINTER_MODE_DEVICE. | int64_t |


> **Note**

Note
The batch mode of a matmul operation is inferred from the batch modes of matrix descriptors, which must all be the same. The following table describes rules for operands that do not have a descriptor, like scaling factors. The expected parameter value depends on the batch mode of the matmul operation and the operand stride configured via a CUBLASLT_MATMUL_DESC_{ATTR}_BATCH_STRIDE attribute.


| Matmul batch mode | Operand stride | Expected parameter value | Usage scenario |
| --- | --- | --- | --- |
| Strided | 0 | Pointer to a buffer for a single batch element | Reuse the value across the batch |
| Non-zero | Pointer to a buffer with distinct values for each batch element | Use distinct values for each batch element |
| Pointer array or grouped | 0 | Pointer to a for a single batch element | Reuse the value across the batch |
| 1 | Pointer to a device array of pointers to buffers, one for each batch element | Use distinct values for each batch element |
| Other values | Not supported | None |




`cublasLtMatmulHeuristicResult_t` 是一个描述符，用于保存配置好的矩阵乘法算法描述符及其运行时属性。

| 成员 | 描述 |
| --- | --- |
| `cublasLtMatmulAlgo_t algo` | 如果首选项 `CUBLASLT_MATMUL_PERF_SEARCH_MODE` 设置为 `CUBLASLT_SEARCH_LIMITED_BY_ALGO_ID`，则必须使用 `cublasLtMatmulAlgoInit()` 进行初始化。请参阅 `cublasLtMatmulSearch_t`。 |
| `size_t workspaceSize;` | 所需工作区内存的实际大小。 |
| `cublasStatus_t state;` | 结果状态。只有在调用 `cublasLtMatmulAlgoGetHeuristic()` 后此成员设置为 `CUBLAS_STATUS_SUCCESS` 时，其他字段才有效。 |
| `float wavesCount;` | Waves 计数是一个设备利用率指标。wavesCount 值为 1.0f 表示当内核启动时将完全占用 GPU。 |
| `int reserved[4];` | 保留字段。 |

cublasLtMatmulInnerShape_t 是一种枚举类型，用于配置内部核函数设计的各个方面。这不会影响 CUDA 网格大小。

| Value | Description |
| --- | --- |
| CUBLASLT_MATMUL_INNER_SHAPE_UNDEFINED | 内部形状未定义。 |
| CUBLASLT_MATMUL_INNER_SHAPE_MMA884 | 内部形状为 MMA884。 |
| CUBLASLT_MATMUL_INNER_SHAPE_MMA1684 | 内部形状为 MMA1684。 |
| CUBLASLT_MATMUL_INNER_SHAPE_MMA1688 | 内部形状为 MMA1688。 |
| CUBLASLT_MATMUL_INNER_SHAPE_MMA16816 | 内部形状为 MMA16816。 |

`cublasLtMatmulMatrixScale_t` 是一种枚举类型，用于指定缩放模式，该模式定义了如何解释缩放因子指针。

| Value | Description |
| --- | --- |
| CUBLASLT_MATMUL_MATRIX_SCALE_SCALAR_32F | 缩放因子是应用于整个张量的单精度标量（此模式是 fp8 的默认模式）。当 D 张量使用窄精度数据类型时，这是 CUBLASLT_MATMUL_DESC_D_SCALE_MODE 的唯一有效值。 |
| CUBLASLT_MATMUL_MATRIX_SCALE_VEC16_UE4M3 | 缩放因子是包含专用缩放因子的张量，作为 8 位 CUDA_R_8F_UE4M3 值存储在对应数据张量最内层维度的每个 16 元素块中。 |
| CUBLASLT_MATMUL_MATRIX_SCALE_VEC32_UE8M0 | 缩放因子是包含专用缩放因子的张量，作为 8 位 CUDA_R_8F_UE8M0 值存储在对应数据张量最内层维度的每个 32 元素块中。 |
| CUBLASLT_MATMUL_MATRIX_SCALE_OUTER_VEC_32F | 缩放因子是 CUDA_R_32F 值的向量。此模式仅适用于矩阵 A 和 B，在这种情况下，向量分别预期有 M 和 N 个元素，A 和 B 乘积的每个 (i, j) 元素分别乘以 A 缩放的第 i 个元素和 B 缩放的第 j 个元素。 |
| CUBLASLT_MATMUL_MATRIX_SCALE_VEC128_32F | 缩放因子是包含专用缩放因子的张量，作为 CUDA_R_32F 缩放因子存储在对应数据张量最内层维度的每个 128 元素块中。 |
| CUBLASLT_MATMUL_MATRIX_SCALE_BLK128x128_32F | 缩放因子是包含专用缩放因子的张量，作为 CUDA_R_32F 缩放因子存储在对应数据张量的每个 128x128 元素块中。 |
| CUBLASLT_MATMUL_MATRIX_SCALE_PER_BATCH_SCALAR_32F | 缩放因子是单精度标量，依次应用于批次中的每个矩阵。此模式仅适用于矩阵 A 和 B，在这种情况下，缩放因子预期有 BATCH_COUNT 个元素。 |

`cublasLtMatmulPreference_t` 是一个指向不透明结构体的指针，该结构体保存了 `cublasLtMatmulAlgoGetHeuristic()` 配置的偏好设置描述。使用 `cublasLtMatmulPreferenceCreate()` 创建描述符的一个实例，使用 `cublasLtMatmulPreferenceDestroy()` 销毁先前创建的描述符并释放资源。


cublasLtMatmulPreferenceAttributes_t is an enumerated type used to apply algorithm search preferences while fine-tuning the heuristic function. Use cublasLtMatmulPreferenceGetAttribute() and cublasLtMatmulPreferenceSetAttribute() to get and set the attribute value of a matmul preference descriptor.


| Value | Description | Data Type |
| --- | --- | --- |
| CUBLASLT_MATMUL_PREF_SEARCH_MODE | Search mode. See cublasLtMatmulSearch_t. Default is CUBLASLT_SEARCH_BEST_FIT. | uint32_t |
| CUBLASLT_MATMUL_PREF_MAX_WORKSPACE_BYTES | Maximum allowed workspace memory. Default is 0 (no workspace memory allowed). | uint64_t |
| CUBLASLT_MATMUL_PREF_REDUCTION_SCHEME_MASK | Reduction scheme mask. See cublasLtReductionScheme_t. Only algorithm configurations specifying CUBLASLT_ALGO_CONFIG_REDUCTION_SCHEME that is not masked out by this attribute are allowed. For example, a mask value of 0x03 will allow only INPLACE and COMPUTE_TYPE reduction schemes. Default is CUBLASLT_REDUCTION_SCHEME_MASK (i.e., allows all reduction schemes). | uint32_t |
| CUBLASLT_MATMUL_PREF_MIN_ALIGNMENT_A_BYTES | Minimum buffer alignment for matrix A (in bytes). Selecting a smaller value will exclude algorithms that can not work with matrix A, which is not as strictly aligned as the algorithms need. Default is 256 bytes. | uint32_t |
| CUBLASLT_MATMUL_PREF_MIN_ALIGNMENT_B_BYTES | Minimum buffer alignment for matrix B (in bytes). Selecting a smaller value will exclude algorithms that can not work with matrix B, which is not as strictly aligned as the algorithms need. Default is 256 bytes. | uint32_t |
| CUBLASLT_MATMUL_PREF_MIN_ALIGNMENT_C_BYTES | Minimum buffer alignment for matrix C (in bytes). Selecting a smaller value will exclude algorithms that can not work with matrix C, which is not as strictly aligned as the algorithms need. Default is 256 bytes. | uint32_t |
| CUBLASLT_MATMUL_PREF_MIN_ALIGNMENT_D_BYTES | Minimum buffer alignment for matrix D (in bytes). Selecting a smaller value will exclude algorithms that can not work with matrix D, which is not as strictly aligned as the algorithms need. Default is 256 bytes. | uint32_t |
| CUBLASLT_MATMUL_PREF_MAX_WAVES_COUNT | Maximum wave count. See cublasLtMatmulHeuristicResult_t::wavesCount. Selecting a non-zero value will exclude algorithms that report device utilization higher than specified. Default is 0.0f. | float |
| CUBLASLT_MATMUL_PREF_IMPL_MASK | Numerical implementation details mask. See cublasLtNumericalImplFlags_t. Filters heuristic result to only include algorithms that use the allowed implementations. default: uint64_t(-1) (allow everything) | uint64_t |
| CUBLASLT_MATMUL_PREF_GROUPED_AVERAGE_REDUCTION_DIM | Experimental: Average reduction dimension. This is only supported when all matrix descriptors have CUBLASLT_MATRIX_LAYOUT_BATCH_MODE set to CUBLASLT_BATCH_MODE_GROUPED. Default value is 0. | uint32_t |
| CUBLASLT_MATMUL_PREF_GROUPED_DESC_D_AVERAGE_ROWS | Experimental: Average rows of matrix D. This is only supported when all matrix descriptors have CUBLASLT_MATRIX_LAYOUT_BATCH_MODE set to CUBLASLT_BATCH_MODE_GROUPED. Default value is 0. | uint32_t |
| CUBLASLT_MATMUL_PREF_GROUPED_DESC_D_AVERAGE_COLS | Experimental: Average columns of matrix D. This is only supported when all matrix descriptors have CUBLASLT_MATRIX_LAYOUT_BATCH_MODE set to CUBLASLT_BATCH_MODE_GROUPED. Default value is 0. | uint32_t |




`cublasLtMatmulSearch_t` 是一个枚举类型，包含了启发式搜索类型的属性。

| Value | Description | Data Type |
| --- | --- | --- |
| CUBLASLT_SEARCH_BEST_FIT | 请求针对给定用例的最佳算法进行启发式搜索。 |  |
| CUBLASLT_SEARCH_LIMITED_BY_ALGO_ID | 仅请求针对预配置算法 ID 的启发式搜索。 |  |


cublasLtMatmulStages_t is an enumerated type used to configure the size and number of shared memory buffers where input elements are staged. Number of staging buffers defines kernel’s pipeline depth.


| Value | Description |
| --- | --- |
| CUBLASLT_MATMUL_STAGES_UNDEFINED | Stage size is undefined. |
| CUBLASLT_MATMUL_STAGES_16x1 | Stage size is 16, number of stages is 1. |
| CUBLASLT_MATMUL_STAGES_16x2 | Stage size is 16, number of stages is 2. |
| CUBLASLT_MATMUL_STAGES_16x3 | Stage size is 16, number of stages is 3. |
| CUBLASLT_MATMUL_STAGES_16x4 | Stage size is 16, number of stages is 4. |
| CUBLASLT_MATMUL_STAGES_16x5 | Stage size is 16, number of stages is 5. |
| CUBLASLT_MATMUL_STAGES_16x6 | Stage size is 16, number of stages is 6. |
| CUBLASLT_MATMUL_STAGES_32x1 | Stage size is 32, number of stages is 1. |
| CUBLASLT_MATMUL_STAGES_32x2 | Stage size is 32, number of stages is 2. |
| CUBLASLT_MATMUL_STAGES_32x3 | Stage size is 32, number of stages is 3. |
| CUBLASLT_MATMUL_STAGES_32x4 | Stage size is 32, number of stages is 4. |
| CUBLASLT_MATMUL_STAGES_32x5 | Stage size is 32, number of stages is 5. |
| CUBLASLT_MATMUL_STAGES_32x6 | Stage size is 32, number of stages is 6. |
| CUBLASLT_MATMUL_STAGES_64x1 | Stage size is 64, number of stages is 1. |
| CUBLASLT_MATMUL_STAGES_64x2 | Stage size is 64, number of stages is 2. |
| CUBLASLT_MATMUL_STAGES_64x3 | Stage size is 64, number of stages is 3. |
| CUBLASLT_MATMUL_STAGES_64x4 | Stage size is 64, number of stages is 4. |
| CUBLASLT_MATMUL_STAGES_64x5 | Stage size is 64, number of stages is 5. |
| CUBLASLT_MATMUL_STAGES_64x6 | Stage size is 64, number of stages is 6. |
| CUBLASLT_MATMUL_STAGES_128x1 | Stage size is 128, number of stages is 1. |
| CUBLASLT_MATMUL_STAGES_128x2 | Stage size is 128, number of stages is 2. |
| CUBLASLT_MATMUL_STAGES_128x3 | Stage size is 128, number of stages is 3. |
| CUBLASLT_MATMUL_STAGES_128x4 | Stage size is 128, number of stages is 4. |
| CUBLASLT_MATMUL_STAGES_128x5 | Stage size is 128, number of stages is 5. |
| CUBLASLT_MATMUL_STAGES_128x6 | Stage size is 128, number of stages is 6. |
| CUBLASLT_MATMUL_STAGES_32x10 | Stage size is 32, number of stages is 10. |
| CUBLASLT_MATMUL_STAGES_8x4 | Stage size is 8, number of stages is 4. |
| CUBLASLT_MATMUL_STAGES_16x10 | Stage size is 16, number of stages is 10. |
| CUBLASLT_MATMUL_STAGES_8x5 | Stage size is 8, number of stages is 5. |
| CUBLASLT_MATMUL_STAGES_8x3 | Stage size is 8, number of stages is 3. |
| CUBLASLT_MATMUL_STAGES_8xAUTO | Stage size is 8, number of stages is selected automatically. |
| CUBLASLT_MATMUL_STAGES_16xAUTO | Stage size is 16, number of stages is selected automatically. |
| CUBLASLT_MATMUL_STAGES_32xAUTO | Stage size is 32, number of stages is selected automatically. |
| CUBLASLT_MATMUL_STAGES_64xAUTO | Stage size is 64, number of stages is selected automatically. |
| CUBLASLT_MATMUL_STAGES_128xAUTO | Stage size is 128, number of stages is selected automatically. |
| CUBLASLT_MATMUL_STAGES_256xAUTO | Stage size is 256, number of stages is selected automatically. |
| CUBLASLT_MATMUL_STAGES_768xAUTO | Stage size is 768, number of stages is selected automatically. |





cublasLtMatmulTile_t is an enumerated type used to set the tile size in `rows x columns.` See also [CUTLASS: Fast Linear Algebra in CUDA C++](https://www.google.com/url?q=https://devblogs.nvidia.com/cutlass-linear-algebra-cuda/&sa=D&ust=1543610995532000&usg=AFQjCNE3tHlNsXDOnOhbVeeH1uXWQFLzLA).


| Value | Description |
| --- | --- |
| CUBLASLT_MATMUL_TILE_UNDEFINED | Tile size is undefined. |
| CUBLASLT_MATMUL_TILE_8x8 | Tile size is 8 rows x 8 columns. |
| CUBLASLT_MATMUL_TILE_8x16 | Tile size is 8 rows x 16 columns. |
| CUBLASLT_MATMUL_TILE_16x8 | Tile size is 16 rows x 8 columns. |
| CUBLASLT_MATMUL_TILE_8x32 | Tile size is 8 rows x 32 columns. |
| CUBLASLT_MATMUL_TILE_16x16 | Tile size is 16 rows x 16 columns. |
| CUBLASLT_MATMUL_TILE_32x8 | Tile size is 32 rows x 8 columns. |
| CUBLASLT_MATMUL_TILE_8x64 | Tile size is 8 rows x 64 columns. |
| CUBLASLT_MATMUL_TILE_16x32 | Tile size is 16 rows x 32 columns. |
| CUBLASLT_MATMUL_TILE_32x16 | Tile size is 32 rows x 16 columns. |
| CUBLASLT_MATMUL_TILE_64x8 | Tile size is 64 rows x 8 columns. |
| CUBLASLT_MATMUL_TILE_32x32 | Tile size is 32 rows x 32 columns. |
| CUBLASLT_MATMUL_TILE_32x64 | Tile size is 32 rows x 64 columns. |
| CUBLASLT_MATMUL_TILE_64x32 | Tile size is 64 rows x 32 columns. |
| CUBLASLT_MATMUL_TILE_32x128 | Tile size is 32 rows x 128 columns. |
| CUBLASLT_MATMUL_TILE_64x64 | Tile size is 64 rows x 64 columns. |
| CUBLASLT_MATMUL_TILE_128x32 | Tile size is 128 rows x 32 columns. |
| CUBLASLT_MATMUL_TILE_64x128 | Tile size is 64 rows x 128 columns. |
| CUBLASLT_MATMUL_TILE_128x64 | Tile size is 128 rows x 64 columns. |
| CUBLASLT_MATMUL_TILE_64x256 | Tile size is 64 rows x 256 columns. |
| CUBLASLT_MATMUL_TILE_128x128 | Tile size is 128 rows x 128 columns. |
| CUBLASLT_MATMUL_TILE_256x64 | Tile size is 256 rows x 64 columns. |
| CUBLASLT_MATMUL_TILE_64x512 | Tile size is 64 rows x 512 columns. |
| CUBLASLT_MATMUL_TILE_128x256 | Tile size is 128 rows x 256 columns. |
| CUBLASLT_MATMUL_TILE_256x128 | Tile size is 256 rows x 128 columns. |
| CUBLASLT_MATMUL_TILE_512x64 | Tile size is 512 rows x 64 columns. |
| CUBLASLT_MATMUL_TILE_64x96 | Tile size is 64 rows x 96 columns. |
| CUBLASLT_MATMUL_TILE_96x64 | Tile size is 96 rows x 64 columns. |
| CUBLASLT_MATMUL_TILE_96x128 | Tile size is 96 rows x 128 columns. |
| CUBLASLT_MATMUL_TILE_128x160 | Tile size is 128 rows x 160 columns. |
| CUBLASLT_MATMUL_TILE_160x128 | Tile size is 160 rows x 128 columns. |
| CUBLASLT_MATMUL_TILE_192x128 | Tile size is 192 rows x 128 columns. |
| CUBLASLT_MATMUL_TILE_128x192 | Tile size is 128 rows x 192 columns. |
| CUBLASLT_MATMUL_TILE_128x96 | Tile size is 128 rows x 96 columns. |




`cublasLtMatrixLayout_t` 是指向不透明结构的指针，该结构保存矩阵布局的描述信息。使用 `cublasLtMatrixLayoutCreate()` 或 `cublasLtGroupedMatrixLayoutCreate()` 创建描述符的实例，并使用 `cublasLtMatrixLayoutDestroy()` 销毁先前创建的描述符并释放资源。


cublasLtMatrixLayoutAttribute_t is a descriptor structure containing the attributes that define the details of the matrix operation. Use cublasLtMatrixLayoutGetAttribute() and cublasLtMatrixLayoutSetAttribute() to get and set the attribute value of a matrix layout descriptor.


| Value | Description | Data Type |
| --- | --- | --- |
| CUBLASLT_MATRIX_LAYOUT_TYPE | Specifies the data precision type. See cudaDataType_t. | uint32_t |
| CUBLASLT_MATRIX_LAYOUT_ORDER | Specifies the memory order of the data of the matrix. Default value is CUBLASLT_ORDER_COL. See cublasLtOrder_t . | int32_t |
| CUBLASLT_MATRIX_LAYOUT_ROWS | Describes the number of rows in the matrix. Normally only values that can be expressed as int32_t are supported. | uint64_t |
| CUBLASLT_MATRIX_LAYOUT_COLS | Describes the number of columns in the matrix. Normally only values that can be expressed as int32_t are supported. | uint64_t |
| CUBLASLT_MATRIX_LAYOUT_LD | The leading dimension of the matrix. For CUBLASLT_ORDER_COL this is the stride (in elements) of matrix column. See also cublasLtOrder_t.

Currently only non-negative values are supported.
Must be large enough so that matrix memory locations are not overlapping (e.g., greater or equal to CUBLASLT_MATRIX_LAYOUT_ROWS in case of CUBLASLT_ORDER_COL). | int64_t |
| CUBLASLT_MATRIX_LAYOUT_BATCH_COUNT | Number of matmul operations to perform in the batch. Default value is 1. See also CUBLASLT_ALGO_CAP_STRIDED_BATCH_SUPPORT, CUBLASLT_ALGO_CAP_POINTER_ARRAY_BATCH_SUPPORT and CUBLASLT_ALGO_CAP_POINTER_ARRAY_GROUPED_SUPPORT in cublasLtMatmulAlgoCapAttributes_t. | int32_t |
| CUBLASLT_MATRIX_LAYOUT_STRIDED_BATCH_OFFSET | Stride (in elements) to the next matrix for the strided batch operation. Default value is 0. When matrix type is planar-complex (CUBLASLT_MATRIX_LAYOUT_PLANE_OFFSET != 0), batch stride is interpreted by cublasLtMatmul() in number of real valued sub-elements. E.g. for data of type CUDA_C_16F, offset of 1024B is encoded as a stride of value 512 (since each element of the real and imaginary matrices is a 2B (16bit) floating point type). NOTE: A bug in cublasLtMatrixTransform() causes it to interpret the batch stride for a planar-complex matrix as if it was specified in number of complex elements. Therefore an offset of 1024B must be encoded as stride value 256 when calling cublasLtMatrixTransform() (each complex element is 4B with real and imaginary values 2B each). This behavior is expected to be corrected in the next major cuBLAS version. | int64_t |
| CUBLASLT_MATRIX_LAYOUT_PLANE_OFFSET | Stride (in bytes) to the imaginary plane for planar-complex layout. Default value is 0, indicating that the layout is regular (real and imaginary parts of complex numbers are interleaved in memory for each element). | int64_t |
| CUBLASLT_MATRIX_LAYOUT_BATCH_MODE | The batch mode of the matrix. Default value is CUBLASLT_BATCH_MODE_STRIDED. See cublasLtBatchMode_t . | int32_t |
| CUBLASLT_GROUPED_MATRIX_LAYOUT_ROWS_ARRAY | Experimental: a device pointer to the array of rows in a grouped matrix. The length of the array must be equal to CUBLASLT_MATRIX_LAYOUT_BATCH_COUNT. The width of each element in the array is determined by CUBLASLT_GROUPED_MATRIX_LAYOUT_ROWS_COLS_ARRAY_INTEGER_WIDTH. Default value is NULL. | void * |
| CUBLASLT_GROUPED_MATRIX_LAYOUT_COLS_ARRAY | Experimental: a device pointer to the array of columns in a grouped matrix. The length of the array must be equal to CUBLASLT_MATRIX_LAYOUT_BATCH_COUNT. The width of each element in the array is determined by CUBLASLT_GROUPED_MATRIX_LAYOUT_ROWS_COLS_ARRAY_INTEGER_WIDTH. Default value is NULL. | void * |
| CUBLASLT_GROUPED_MATRIX_LAYOUT_LD_ARRAY | Experimental: a device pointer to the array of leading dimensions in a grouped matrix. The length of the array must be equal to CUBLASLT_MATRIX_LAYOUT_BATCH_COUNT. The width of each element in the array is determined by CUBLASLT_GROUPED_MATRIX_LAYOUT_LD_ARRAY_INTEGER_WIDTH. Default value is NULL. | void * |
| CUBLASLT_GROUPED_MATRIX_LAYOUT_ROWS_COLS_ARRAY_INTEGER_WIDTH | Experimental: cublasLtIntegerWidth_t is an enumerated type used to indicate the width of integers in the rows and columns arrays of a grouped matrix. Default value is CUBLASLT_INTEGER_WIDTH_32. See cublasLtIntegerWidth_t . | int32_t |
| CUBLASLT_GROUPED_MATRIX_LAYOUT_LD_ARRAY_INTEGER_WIDTH | Experimental: cublasLtIntegerWidth_t is an enumerated type used to indicate the width of integers in the leading dimensions array of a grouped matrix. Default value is CUBLASLT_INTEGER_WIDTH_32. See cublasLtIntegerWidth_t . | int32_t |




`cublasLtMatrixTransformDesc_t` 是一个指向不透明结构体的指针，该结构体保存矩阵变换操作的描述信息。使用 `cublasLtMatrixTransformDescCreate()` 创建描述符的一个实例，并使用 `cublasLtMatrixTransformDescDestroy()` 销毁先前创建的描述符以及释放相关资源。

cublasLtMatrixTransformDescAttributes_t 是一个描述符结构，包含定义矩阵变换操作细节的属性。使用 cublasLtMatrixTransformDescGetAttribute() 和 cublasLtMatrixTransformDescSetAttribute() 来设置矩阵变换描述符的属性值。

| 值 | 描述 | 数据类型 |
| --- | --- | --- |
| CUBLASLT_MATRIX_TRANSFORM_DESC_SCALE_TYPE | 缩放类型。输入将转换为缩放类型以进行缩放和求和运算，然后结果将转换回输出类型以存储到内存中。支持的数据类型请参见 cudaDataType_t。 | int32_t |
| CUBLASLT_MATRIX_TRANSFORM_DESC_POINTER_MODE | 指定标量 alpha 和 beta 是通过引用传递的，无论在主机端还是设备端。默认值为：CUBLASLT_POINTER_MODE_HOST（即在主机端）。请参见 cublasLtPointerMode_t。 | int32_t |
| CUBLASLT_MATRIX_TRANSFORM_DESC_TRANSA | 指定对矩阵 A 执行的操作类型。默认值为：CUBLAS_OP_N（即非转置操作）。请参见 cublasOperation_t。 | int32_t |
| CUBLASLT_MATRIX_TRANSFORM_DESC_TRANSB | 指定对矩阵 B 执行的操作类型。默认值为：CUBLAS_OP_N（即非转置操作）。请参见 cublasOperation_t。 | int32_t |


cublasLtNumericalImplFlags_t: a set of bit-flags that can be specified to select implementation details that may affect numerical behavior of algorithms.


Flags below can be combined using the bit OR operator “|”.


| Value | Description |
| --- | --- |
| CUBLASLT_NUMERICAL_IMPL_FLAGS_FMA | Specify that the implementation is based on [H,F,D]FMA (fused multiply-add) family instructions. |
| CUBLASLT_NUMERICAL_IMPL_FLAGS_HMMA | Specify that the implementation is based on HMMA (tensor operation) family instructions. |
| CUBLASLT_NUMERICAL_IMPL_FLAGS_IMMA | Specify that the implementation is based on IMMA (integer tensor operation) family instructions. |
| CUBLASLT_NUMERICAL_IMPL_FLAGS_DMMA | Specify that the implementation is based on DMMA (double precision tensor operation) family instructions. |
| CUBLASLT_NUMERICAL_IMPL_FLAGS_TENSOR_OP_MASK | Mask to filter implementations using any of the above kinds of tensor operations. |
| CUBLASLT_NUMERICAL_IMPL_FLAGS_OP_TYPE_MASK | Mask to filter implementation details about multiply-accumulate instructions used. |
|  |  |
| CUBLASLT_NUMERICAL_IMPL_FLAGS_ACCUMULATOR_16F | Specify that the implementation’s inner dot product is using half precision accumulator. |
| CUBLASLT_NUMERICAL_IMPL_FLAGS_ACCUMULATOR_32F | Specify that the implementation’s inner dot product is using single precision accumulator. |
| CUBLASLT_NUMERICAL_IMPL_FLAGS_ACCUMULATOR_64F | Specify that the implementation’s inner dot product is using double precision accumulator. |
| CUBLASLT_NUMERICAL_IMPL_FLAGS_ACCUMULATOR_32I | Specify that the implementation’s inner dot product is using 32 bit signed integer precision accumulator. |
| CUBLASLT_NUMERICAL_IMPL_FLAGS_ACCUMULATOR_TYPE_MASK | Mask to filter implementation details about accumulator used. |
|  |  |
| CUBLASLT_NUMERICAL_IMPL_FLAGS_INPUT_16F | Specify that the implementation’s inner dot product multiply-accumulate instruction is using half-precision inputs. |
| CUBLASLT_NUMERICAL_IMPL_FLAGS_INPUT_16BF | Specify that the implementation’s inner dot product multiply-accumulate instruction is using bfloat16 inputs. |
| CUBLASLT_NUMERICAL_IMPL_FLAGS_INPUT_TF32 | Specify that the implementation’s inner dot product multiply-accumulate instruction is using TF32 inputs. |
| CUBLASLT_NUMERICAL_IMPL_FLAGS_INPUT_32F | Specify that the implementation’s inner dot product multiply-accumulate instruction is using single-precision inputs. |
| CUBLASLT_NUMERICAL_IMPL_FLAGS_INPUT_64F | Specify that the implementation’s inner dot product multiply-accumulate instruction is using double-precision inputs. |
| CUBLASLT_NUMERICAL_IMPL_FLAGS_INPUT_8I | Specify that the implementation’s inner dot product multiply-accumulate instruction is using 8-bit integer inputs. |
| CUBLASLT_NUMERICAL_IMPL_FLAGS_OP_INPUT_TYPE_MASK | Mask to filter implementation details about accumulator input used. |
|  |  |
| CUBLASLT_NUMERICAL_IMPL_FLAGS_GAUSSIAN | Specify that the implementation applies Gauss complexity reduction algorithm to reduce arithmetic complexity of the complex matrix multiplication problem |





cublasLtOrder_t is an enumerated type used to indicate the data ordering of the matrix.


| Value | Description |
| --- | --- |
| CUBLASLT_ORDER_COL | Data is ordered in column-major format. The leading dimension is the stride (in elements) to the beginning of next column in memory. |
| CUBLASLT_ORDER_ROW | Data is ordered in row-major format. The leading dimension is the stride (in elements) to the beginning of next row in memory. |
| CUBLASLT_ORDER_COL32 | Data is ordered in column-major ordered tiles of 32 columns. The leading dimension is the stride (in elements) to the beginning of next group of 32-columns.
For example, if the matrix has 33 columns and 2 rows, then the leading dimension must be at least 32 * 2 = 64. |
| CUBLASLT_ORDER_COL4_4R2_8C | Data is ordered in column-major ordered tiles of composite tiles with total 32 columns and 8 rows. A tile is composed of interleaved inner tiles of 4 columns within 4 even or odd rows in an alternating pattern.
The leading dimension is the stride (in elements) to the beginning of the first 32 column x 8 row tile for the next 32-wide group of columns. For example, if the matrix has 33 columns and 1 row,
the leading dimension must be at least (32 * 8) * 1 = 256. |
| CUBLASLT_ORDER_COL32_2R_4R4 | Data is ordered in column-major ordered tiles of composite tiles with total 32 columns ands 32 rows. Element offset within the tile is calculated as (((row % 8) / 2 * 4 + row / 8) * 2 + row % 2) * 32 + col.
Leading dimension is the stride (in elements) to the beginning of the first 32 column x 32 row tile for the next 32-wide group of columns. E.g. if matrix has 33 columns and 1 row, then its leading dimensions
must be at least (32 * 32) * 1 = 1024. |




cublasLtPointerMode_t 是一个枚举类型，用于设置缩放因子 `alpha` 和 `beta` 的指针模式。

| 值 | 描述 |
| --- | --- |
| CUBLASLT_POINTER_MODE_HOST = CUBLAS_POINTER_MODE_HOST | 与 CUBLAS_POINTER_MODE_HOST 匹配，指针指向主机内存中的单个值。 |
| CUBLASLT_POINTER_MODE_DEVICE = CUBLAS_POINTER_MODE_DEVICE | 与 CUBLAS_POINTER_MODE_DEVICE 匹配，指针指向设备内存中的单个值。 |
| CUBLASLT_POINTER_MODE_DEVICE_VECTOR = 2 | 指针指向设备内存向量，长度等于矩阵 D 的行数。 |
| CUBLASLT_POINTER_MODE_ALPHA_DEVICE_VECTOR_BETA_ZERO = 3 | alpha 指针指向设备内存向量，长度等于矩阵 D 的行数，beta 为零。 |
| CUBLASLT_POINTER_MODE_ALPHA_DEVICE_VECTOR_BETA_HOST = 4 | alpha 指针指向设备内存向量，长度等于矩阵 D 的行数，beta 为主机内存中的单个值。 |


> **注意**

注意
当任何矩阵的 cublasLtBatchMode_t 设置为 CUBLASLT_BATCH_MODE_POINTER_ARRAY 或 CUBLASLT_BATCH_MODE_GROUPED 时，仅支持 CUBLASLT_POINTER_MODE_HOST 和 CUBLASLT_POINTER_MODE_DEVICE 这两种指针模式。

`cublasLtPointerModeMask_t` 是一个枚举类型，用于定义和查询指针模式功能。

| 值 | 描述 |
| --- | --- |
| CUBLASLT_POINTER_MODE_MASK_HOST = 1 | 参见 cublasLtPointerMode_t 中的 CUBLASLT_POINTER_MODE_HOST。 |
| CUBLASLT_POINTER_MODE_MASK_DEVICE = 2 | 参见 cublasLtPointerMode_t 中的 CUBLASLT_POINTER_MODE_DEVICE。 |
| CUBLASLT_POINTER_MODE_MASK_DEVICE_VECTOR = 4 | 参见 cublasLtPointerMode_t 中的 CUBLASLT_POINTER_MODE_DEVICE_VECTOR |
| CUBLASLT_POINTER_MODE_MASK_ALPHA_DEVICE_VECTOR_BETA_ZERO = 8 | 参见 cublasLtPointerMode_t 中的 CUBLASLT_POINTER_MODE_ALPHA_DEVICE_VECTOR_BETA_ZERO |
| CUBLASLT_POINTER_MODE_MASK_ALPHA_DEVICE_VECTOR_BETA_HOST = 16 | 参见 cublasLtPointerMode_t 中的 CUBLASLT_POINTER_MODE_ALPHA_DEVICE_VECTOR_BETA_HOST |

cublasLtReductionScheme_t 是一个枚举类型，用于指定并行计算点积部分时的归约方案（即"Split-K"）。

| 值 | 描述 |
| --- | --- |
| CUBLASLT_REDUCTION_SCHEME_NONE | 不应用归约。点积将按一个序列执行。 |
| CUBLASLT_REDUCTION_SCHEME_INPLACE | 使用输出缓冲区"原地"执行归约，各部分以输出数据类型相加。仅使用工作区来存储确保顺序性的计数器。 |
| CUBLASLT_REDUCTION_SCHEME_COMPUTE_TYPE | 在用户提供的 workspace 中以计算数据类型存储中间结果，并在单独的步骤中进行归约。 |
| CUBLASLT_REDUCTION_SCHEME_OUTPUT_TYPE | 在用户提供的 workspace 中以输出数据类型存储中间结果，并在单独的步骤中进行归约。 |
| CUBLASLT_REDUCTION_SCHEME_MASK | 允许所有归约方案。 |
## 3.4. cuBLASLt API Reference




##### 3.4.1. cublasLtCreate()
##### 3.4.2. cublasLtDestroy()
##### 3.4.3. cublasLtDisableCpuInstructionsSetMask()
##### 3.4.4. cublasLtGetCudartVersion()
##### 3.4.5. cublasLtGetProperty()
##### 3.4.6. cublasLtGetStatusName()
##### 3.4.7. cublasLtGetStatusString()
##### 3.4.8. cublasLtHeuristicsCacheGetCapacity()
##### 3.4.9. cublasLtHeuristicsCacheSetCapacity()
##### 3.4.10. cublasLtGetVersion()
##### 3.4.11. cublasLtLoggerSetCallback()
##### 3.4.12. cublasLtLoggerSetFile()
##### 3.4.13. cublasLtLoggerOpenFile()
##### 3.4.14. cublasLtLoggerSetLevel()
##### 3.4.15. cublasLtLoggerSetMask()
##### 3.4.16. cublasLtLoggerForceDisable()
##### 3.4.17. cublasLtMatmul()
##### 3.4.18. cublasLtMatmulAlgoCapGetAttribute()
##### 3.4.19. cublasLtMatmulAlgoCheck()
##### 3.4.20. cublasLtMatmulAlgoConfigGetAttribute()
### 3.4.1. cublasLtCreate()



```c++

cublasStatus_t
      cublasLtCreate(cublasLtHandle_t *lighthandle)


```


This function initializes the cuBLASLt library and creates a handle to an opaque structure holding the cuBLASLt library context. It allocates light hardware resources on the host and device, and must be called prior to making any other cuBLASLt library calls.


The cuBLASLt library context is tied to the current CUDA device. To use the library on multiple devices, one cuBLASLt handle must be created for each device. Furthermore, the device must be set as the current before invoking cuBLASLt functions with a handle tied to that device.


See also: [cuBLAS Context](#cublas-context).


**Parameters:**


| Parameter | Memory | Input / Output | Description |
| --- | --- | --- | --- |
| lightHandle |  | Output | Pointer to the allocated cuBLASLt handle for the created cuBLASLt context. |


**Returns:**


| Return Value | Description |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | The allocation completed successfully. |
| CUBLAS_STATUS_NOT_INITIALIZED | The cuBLASLt library was not initialized. This usually happens:

when cublasLtCreate() is not called first
an error in the CUDA Runtime API called by the cuBLASLt routine, or
an error in the hardware setup. |
| CUBLAS_STATUS_ALLOC_FAILED | Resource allocation failed inside the cuBLASLt library. This is usually caused by a cudaMalloc() failure.
To correct: prior to the function call, deallocate the previously allocated memory as much as possible. |
| CUBLAS_STATUS_INVALID_VALUE | lighthandle is NULL |


See [cublasStatus_t](#cublasstatus-t) for a complete list of valid return codes.





### 3.4.2. cublasLtDestroy()



```c++

cublasStatus_t
      cublasLtDestroy(cublasLtHandle_t lightHandle)


```


This function releases hardware resources used by the cuBLASLt library. This function is usually the last call with a particular handle to the cuBLASLt library. Because [cublasLtCreate()](#cublasltcreate) allocates some internal resources and the release of those resources by calling [cublasLtDestroy()](#cublasltdestroy) will implicitly call `cudaDeviceSynchronize()`, it is recommended to minimize the number of times these functions are called.


**Parameters**:


| Parameter | Memory | Input / Output | Description |
| --- | --- | --- | --- |
| lightHandle |  | Input | Pointer to the cuBLASLt handle to be destroyed. |


**Returns**:


| Return Value | Meaning |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | The cuBLASLt context was successfully destroyed. |
| CUBLAS_STATUS_NOT_INITIALIZED | The cuBLASLt library was not initialized. |
| CUBLAS_STATUS_INVALID_VALUE | lightHandle is NULL |


See [cublasStatus_t](#cublasstatus-t) for a complete list of valid return codes.





### 3.4.3. cublasLtDisableCpuInstructionsSetMask()



```c++

unsigned cublasLtDisableCpuInstructionsSetMask(unsigned mask);


```


Instructs cuBLASLt library to not use [CPU instructions](#disabling-cpu-instructions) specified by the flags in the `mask`.
The function takes precedence over the `CUBLASLT_DISABLE_CPU_INSTRUCTIONS_MASK` environment variable.


**Parameters:** `mask` – the flags combined with bitwise `OR(|)` operator that specify which CPU instructions should not be used.


Supported flags:


| Value | Description |
| --- | --- |
| 0x1 | x86-64 AVX512 ISA. |


**Returns:** the previous value of the `mask`.





### 3.4.4. cublasLtGetCudartVersion()



```c++

size_t cublasLtGetCudartVersion(void);


```


This function returns the version number of the CUDA Runtime library.


**Parameters:** None.


**Returns:**`size_t` - The version number of the CUDA Runtime library.





### 3.4.5. cublasLtGetProperty()



```c++

cublasStatus_t cublasLtGetProperty(libraryPropertyType type, int *value);


```


This function returns the value of the requested property by writing it to the memory location pointed to by the value parameter.


**Parameters**:


| Parameter | Memory | Input / Output | Description |
| --- | --- | --- | --- |
| type |  | Input | Of the type libraryPropertyType, whose value is requested from the property. See libraryPropertyType_t. |
| value |  | Output | Pointer to the host memory location where the requested information should be written. |


**Returns**:


| Return Value | Meaning |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | The requested libraryPropertyType information is successfully written at the provided address. |
| CUBLAS_STATUS_INVALID_VALUE | If invalid value of the type input argument, or
if value is NULL |


See [cublasStatus_t](#cublasstatus-t) for a complete list of valid return codes.





### 3.4.6. cublasLtGetStatusName()



```c++

const char* cublasLtGetStatusName(cublasStatus_t status);


```


Returns the string representation of a given status.


**Parameters:** [cublasStatus_t](#cublasstatus-t) - the status.


**Returns:** `const char*` - the NULL-terminated string.





### 3.4.7. cublasLtGetStatusString()



```c++

const char* cublasLtGetStatusString(cublasStatus_t status);


```


Returns the description string for a given status.


**Parameters:** [cublasStatus_t](#cublasstatus-t) - the status.


**Returns:** `const char*` - the NULL-terminated string.





### 3.4.8. cublasLtHeuristicsCacheGetCapacity()



```c++

cublasStatus_t cublasLtHeuristicsCacheGetCapacity(size_t* capacity);


```


Returns the [Heuristics Cache](#heuristics-cache) capacity.


**Parameters:**


| Parameter | Description |
| --- | --- |
| capacity | The pointer to the returned capacity value. |


**Returns:**


| Return Value | Description |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | The capacity was successfully written. |
| CUBLAS_STATUS_INVALID_VALUE | The capacity was successfully set. |





### 3.4.9. cublasLtHeuristicsCacheSetCapacity()



```c++

cublasStatus_t cublasLtHeuristicsCacheSetCapacity(size_t capacity);


```


Sets the [Heuristics Cache](#heuristics-cache) capacity. Set the capacity to 0 to disable the heuristics cache.


This function takes precedence over `CUBLASLT_HEURISTICS_CACHE_CAPACITY` environment variable.


**Parameters:**


| Parameter | Description |
| --- | --- |
| capacity | The desirable heuristics cache capacity. |


**Returns:**


| Return Value | Description |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | The capacity was successfully set. |





### 3.4.10. cublasLtGetVersion()



```c++

size_t cublasLtGetVersion(void);


```


This function returns the version number of cuBLASLt library.


**Parameters:** None.


**Returns:**`size_t` - The version number of cuBLASLt library.





### 3.4.11. cublasLtLoggerSetCallback()



```c++

cublasStatus_t cublasLtLoggerSetCallback(cublasLtLoggerCallback_t callback);


```


Experimental: This function sets the logging callback function.


**Parameters**:


| Parameter | Memory | Input / Output | Description |
| --- | --- | --- | --- |
| callback |  | Input | Pointer to a callback function. See cublasLtLoggerCallback_t. |


**Returns**:


| Return Value | Description |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | If the callback function was successfully set. |


See cublasStatus_t for a complete list of valid return codes.





### 3.4.12. cublasLtLoggerSetFile()



```c++

cublasStatus_t cublasLtLoggerSetFile(FILE* file);


```


Experimental: This function sets the logging output file. Note: once registered using this function call, the provided file handle must not be closed unless the function is called again to switch to a different file handle.


**Parameters**:


| Parameter | Memory | Input / Output | Description |
| --- | --- | --- | --- |
| file |  | Input | Pointer to an open file. File should have write permission. |


**Returns**:


| Return Value | Description |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | If logging file was successfully set. |


See [cublasStatus_t](#cublasstatus-t) for a complete list of valid return codes.





### 3.4.13. cublasLtLoggerOpenFile()



```c++

cublasStatus_t cublasLtLoggerOpenFile(const char* logFile);


```


Experimental: This function opens and sets the logging output file in the given path.


**Parameters**:


| Parameter | Memory | Input / Output | Description |
| --- | --- | --- | --- |
| logFile |  | Input | Path of the logging output file. |


**Returns**:


| Return Value | Description |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | If the logging file was successfully opened. |


See [cublasStatus_t](#cublasstatus-t) for a complete list of valid return codes.





### 3.4.14. cublasLtLoggerSetLevel()



```c++

cublasStatus_t cublasLtLoggerSetLevel(int level);


```


Experimental: This function sets the value of the logging level.


**Parameters**:


| Parameter | Memory | Input / Output | Description |
| --- | --- | --- | --- |
| level |  | Input | Value of the logging level. See cuBLASLt Logging. |


**Returns**:


| Return Value | Description |
| --- | --- |
| CUBLAS_STATUS_INVALID_VALUE | If the value was not a valid logging level. See cuBLASLt Logging. |
| CUBLAS_STATUS_SUCCESS | If the logging level was successfully set. |


See [cublasStatus_t](#cublasstatus-t) for a complete list of valid return codes.





### 3.4.15. cublasLtLoggerSetMask()



```c++

cublasStatus_t cublasLtLoggerSetMask(int mask);


```


Experimental: This function sets the value of the logging mask.


**Parameters**:


| Parameter | Memory | Input / Output | Description |
| --- | --- | --- | --- |
| mask |  | Input | Value of the logging mask. See cuBLASLt Logging. |


**Returns**:


| Return Value | Description |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | If the logging mask was successfully set. |


See [cublasStatus_t](#cublasstatus-t) for a complete list of valid return codes.





### 3.4.16. cublasLtLoggerForceDisable()



```c++

cublasStatus_t cublasLtLoggerForceDisable();


```


Experimental: This function disables logging for the entire run.


**Returns**:


| Return Value | Description |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | If logging was successfully disabled. |


See [cublasStatus_t](#cublasstatus-t) for a complete list of valid return codes.





### 3.4.17. cublasLtMatmul()



```c++

cublasStatus_t cublasLtMatmul(
      cublasLtHandle_t               lightHandle,
      cublasLtMatmulDesc_t           computeDesc,
      const void                    *alpha,
      const void                    *A,
      cublasLtMatrixLayout_t         Adesc,
      const void                    *B,
      cublasLtMatrixLayout_t         Bdesc,
      const void                    *beta,
      const void                    *C,
      cublasLtMatrixLayout_t         Cdesc,
      void                          *D,
      cublasLtMatrixLayout_t         Ddesc,
      const cublasLtMatmulAlgo_t    *algo,
      void                          *workspace,
      size_t                         workspaceSizeInBytes,
      cudaStream_t                   stream);


```


This function computes the matrix multiplication of matrices A and B to produce the output matrix D, according to the following operation:


`D = alpha*(A*B) + beta*(C),`


where `A`, `B`, and `C` are input matrices, and `alpha` and `beta` are input scalars.


> **Note**

Note
This function supports both in-place matrix multiplication (C == D and Cdesc == Ddesc) and out-of-place matrix multiplication (C != D, both matrices must have the same data type, number of rows, number of columns, batch size, and memory order). In the out-of-place case, the leading dimension of C can be different from the leading dimension of D. Specifically the leading dimension of C can be 0 to achieve row or column broadcast. If Cdesc is omitted, this function assumes it to be equal to Ddesc.


The `workspace` pointer must be aligned to at least a multiple of 256 bytes.
The recommendations on `workspaceSizeInBytes` are the same as mentioned in the [cublasSetWorkspace()](#cublassetworkspace) section.


**Datatypes Supported:**


[cublasLtMatmul()](#cublasltmatmul) supports the following computeType, scaleType, Atype/Btype, and Ctype. Footnotes can be found at the end of this section.


| computeType | scaleType | Atype/Btype | Ctype | Bias Type 6 |
| --- | --- | --- | --- | --- |
| CUBLAS_COMPUTE_16F or
CUBLAS_COMPUTE_16F_PEDANTIC | CUDA_R_16F | CUDA_R_16F | CUDA_R_16F | CUDA_R_16F 6 |
| CUBLAS_COMPUTE_32I or
CUBLAS_COMPUTE_32I_PEDANTIC | CUDA_R_32I | CUDA_R_8I | CUDA_R_32I | Epilogue is not supported. |
| CUDA_R_32F | CUDA_R_8I | CUDA_R_8I | Epilogue is not supported. |
| CUBLAS_COMPUTE_32F or
CUBLAS_COMPUTE_32F_PEDANTIC | CUDA_R_32F | CUDA_R_16BF | CUDA_R_16BF | CUDA_R_16BF 6 |
| CUDA_R_16F | CUDA_R_16F | CUDA_R_16F 6 |
| CUDA_R_8I | CUDA_R_32F | Epilogue is not supported. |
| CUDA_R_16BF | CUDA_R_32F | CUDA_R_32F 6 |
| CUDA_R_16F | CUDA_R_32F | CUDA_R_32F 6 |
| CUDA_R_32F | CUDA_R_32F | CUDA_R_32F 6 |
| CUDA_C_32F 7 | CUDA_C_8I 7 | CUDA_C_32F 7 | Epilogue is not supported. |
| CUDA_C_32F 7 | CUDA_C_32F 7 |
| CUBLAS_COMPUTE_32F_FAST_16F or
CUBLAS_COMPUTE_32F_FAST_16BF or
CUBLAS_COMPUTE_32F_FAST_TF32 or
CUBLAS_COMPUTE_32F_EMULATED_16BFX9 | CUDA_R_32F | CUDA_R_32F | CUDA_R_32F | CUDA_R_32F 6 |
| CUDA_C_32F 7 | CUDA_C_32F 7 | CUDA_C_32F 7 | Epilogue is not supported. |
| CUBLAS_COMPUTE_64F or
CUBLAS_COMPUTE_64F_PEDANTIC or
CUBLAS_COMPUTE_64F_EMULATED_FIXEDPOINT | CUDA_R_64F | CUDA_R_64F | CUDA_R_64F | CUDA_R_64F 6 |
| CUDA_C_64F 7 | CUDA_C_64F 7 | CUDA_C_64F 7 | Epilogue is not supported. |


To use IMMA kernels, one of the following sets of requirements, with the first being the preferred one, must be met:


1. Using a regular data ordering:

All matrix pointers must be 4-byte aligned. For even better performance, this condition should hold with 16 instead of 4.
Leading dimensions of matrices A, B, C must be multiples of 4.
Only the “TN” format is supported - A must be transposed and B non-transposed.
Pointer mode can be CUBLASLT_POINTER_MODE_HOST, CUBLASLT_POINTER_MODE_DEVICE or CUBLASLT_POINTER_MODE_ALPHA_DEVICE_VECTOR_BETA_HOST. With the latter mode, the kernels support the CUBLASLT_MATMUL_DESC_ALPHA_VECTOR_BATCH_STRIDE attribute.
Dimensions m and k must be multiples of 4.
2. Using the IMMA-specific data ordering on Ampere (compute capability 8.0) or Turing (compute capability 7.5) (but not Hopper, compute capability 9.0, or later) architecture - CUBLASLT_ORDER_COL32` for matrices A, C, D, and CUBLASLT_ORDER_COL4_4R2_8C (on Turing or Ampere architecture) or CUBLASLT_ORDER_COL32_2R_4R4 (on Ampere architecture) for matrix B:

Leading dimensions of matrices A, B, C must fulfill conditions specific to the memory ordering (see cublasLtOrder_t).
Matmul descriptor must specify CUBLAS_OP_T on matrix B and CUBLAS_OP_N (default) on matrix A and C.
If scaleType CUDA_R_32I is used, the only supported values for alpha and beta are 0 or 1.
Pointer mode can be CUBLASLT_POINTER_MODE_HOST, CUBLASLT_POINTER_MODE_DEVICE, CUBLASLT_POINTER_MODE_DEVICE_VECTOR or CUBLASLT_POINTER_MODE_ALPHA_DEVICE_VECTOR_BETA_ZERO. These kernels do not support CUBLASLT_MATMUL_DESC_ALPHA_VECTOR_BATCH_STRIDE.
Only the “NT” format is supported - A must be non-transposed and B transposed.


| computeType | scaleType | Atype/Btype | Ctype | Bias Type |
| --- | --- | --- | --- | --- |
| CUBLAS_COMPUTE_32I or
CUBLAS_COMPUTE_32I_PEDANTIC | CUDA_R_32I | CUDA_R_8I | CUDA_R_32I | Non-default epilogue not supported. |
| CUDA_R_32F | CUDA_R_8I | CUDA_R_8I | CUDA_R_32F |


To use tensor- or block-scaled FP8 kernels, the following set of requirements must be satisfied:


- All matrix dimensions must meet the optimal requirements listed in Tensor Core Usage (i.e. pointers and matrix dimension must support 16-byte alignment).
- Scaling mode must meet the restrictions noted in the Scaling Mode Support Overview table.
- A must be transposed and B non-transposed (The “TN” format) on Ada (compute capability 8.9), Hopper (compute capability 9.0), and Blackwell GeForce (compute capability 12.x) GPUs.
- The compute type must be CUBLAS_COMPUTE_32F.
- The scale type must be CUDA_R_32F.


See the table below when using FP8 kernels:


| AType | BType | CType | DType | Bias Type |
| --- | --- | --- | --- | --- |
| CUDA_R_8F_E4M3 | CUDA_R_8F_E4M3 | CUDA_R_16BF | CUDA_R_16BF | CUDA_R_16BF 6 |
| CUDA_R_8F_E4M3 8 | CUDA_R_16BF 6 |
| CUDA_R_16F | CUDA_R_16F | CUDA_R_16F 6 |
| CUDA_R_8F_E4M3 8 | CUDA_R_16F 6 |
| CUDA_R_32F | CUDA_R_32F | CUDA_R_16BF 6 |
| CUDA_R_8F_E5M2 | CUDA_R_16BF | CUDA_R_16BF | CUDA_R_16BF 6 |
| CUDA_R_8F_E4M3 8 | CUDA_R_16BF 6 |
| CUDA_R_8F_E5M2 8 | CUDA_R_16BF 6 |
| CUDA_R_16F | CUDA_R_16F | CUDA_R_16F 6 |
| CUDA_R_8F_E4M3 8 | CUDA_R_16F 6 |
| CUDA_R_8F_E5M2 8 | CUDA_R_16F 6 |
| CUDA_R_32F | CUDA_R_32F | CUDA_R_16BF 6 |
| CUDA_R_8F_E5M2 | CUDA_R_8F_E4M3 | CUDA_R_16BF | CUDA_R_16BF | CUDA_R_16BF 6 |
| CUDA_R_8F_E4M3 8 | CUDA_R_16BF 6 |
| CUDA_R_8F_E5M2 8 | CUDA_R_16BF 6 |
| CUDA_R_16F | CUDA_R_16F | CUDA_R_16F 6 |
| CUDA_R_8F_E4M3 8 | CUDA_R_16F 6 |
| CUDA_R_8F_E5M2 8 | CUDA_R_16F 6 |
| CUDA_R_32F | CUDA_R_32F | CUDA_R_16BF 6 |


To use block-scaled FP4 kernels, the following set of requirements must be satisfied:


- All matrix dimensions must meet the optimal requirements listed in Tensor Core Usage (i.e. pointers and matrix dimension must support 16-byte alignment).
- Scaling mode must be CUBLASLT_MATMUL_MATRIX_SCALE_VEC16_UE4M3
- A must be transposed and B non-transposed (The “TN” format)
- The compute type must be CUBLAS_COMPUTE_32F.
- The scale type must be CUDA_R_32F.


| AType | BType | CType | DType | Bias Type |
| --- | --- | --- | --- | --- |
| CUDA_R_4F_E2M1 | CUDA_R_4F_E2M1 | CUDA_R_16BF | CUDA_R_16BF | CUDA_R_16BF 6 |
| CUDA_R_4F_E2M1 | CUDA_R_16BF 6 |
| CUDA_R_16F | CUDA_R_16F | CUDA_R_16F 6 |
| CUDA_R_4F_E2M1 | CUDA_R_16F 6 |
| CUDA_R_32F | CUDA_R_32F | CUDA_R_16BF 6 |


When A,B,C,D are planar-complex matrices (`CUBLASLT_MATRIX_LAYOUT_PLANE_OFFSET != 0`, see [cublasLtMatrixLayoutAttribute_t](#cublasltmatrixlayoutattribute-t)) to make use of mixed precision tensor core acceleration, the following set of requirements must be satisfied:


| computeType | scaleType | Atype/Btype | Ctype |
| --- | --- | --- | --- |
| CUBLAS_COMPUTE_32F | CUDA_C_32F | CUDA_C_16F 7 | CUDA_C_16F 7 |
| CUDA_C_32F 7 |
| CUDA_C_16BF 7 | CUDA_C_16BF 7 |
| CUDA_C_32F 7 |


Experimental: To use [cublasLtMatmul()](#cublasltmatmul)  with grouped matrices, the following set of requirements must be satisfied:


- All matrix dimensions must meet the optimal requirements listed in Tensor Core Usage (i.e. pointers and matrix dimension must support 16-byte alignment).
- GPU with one of the following compute capabilities: 9.0, 10.x, 11.0.
- The batch mode of all matrices must be CUBLASLT_BATCH_MODE_GROUPED.
- The order type of all matrices must be CUBLASLT_ORDER_COL.
- The pointer mode must be CUBLASLT_POINTER_MODE_HOST or CUBLASLT_POINTER_MODE_DEVICE.
- The scale mode of matrices C  and D must be CUBLASLT_MATMUL_MATRIX_SCALE_SCALAR_32F.
- On GPUs with compute capability 9.0:



The scale mode of matrices A, B must be CUBLASLT_MATMUL_MATRIX_SCALE_SCALAR_32F, CUBLASLT_MATMUL_MATRIX_SCALE_VEC128_32F, or CUBLASLT_MATMUL_MATRIX_SCALE_BLK128x128_32F (for FP8 tensors)
The epilogue must be CUBLASLT_EPILOGUE_DEFAULT
The attributes CUBLASLT_MATMUL_DESC_ALPHA_BATCH_STRIDE and CUBLASLT_MATMUL_DESC_BETA_BATCH_STRIDE must be 0
- On GPUs with compute capability 10.x and 11.0:



The scale mode of matrices A, B must be CUBLASLT_MATMUL_MATRIX_SCALE_SCALAR_32F, CUBLASLT_MATMUL_MATRIX_SCALE_VEC32_UE8M0, CUBLASLT_MATMUL_MATRIX_SCALE_PER_BATCH_SCALAR_32F (for FP8 tensors), or CUBLASLT_MATMUL_MATRIX_SCALE_VEC16_UE4M3 (for FP4 tensors)
The epilogue must be CUBLASLT_EPILOGUE_DEFAULT or CUBLASLT_EPILOGUE_BIAS


| AType | BType | CType | DType | Bias Type |
| --- | --- | --- | --- | --- |
| CUDA_R_8F_E4M3 | CUDA_R_8F_E4M3 | CUDA_R_16BF | CUDA_R_16BF | CUDA_R_16BF 6 |
| CUDA_R_16F | CUDA_R_16F | CUDA_R_16F 6 |
| CUDA_R_32F | CUDA_R_32F | CUDA_R_16BF 6 |
| CUDA_R_8F_E5M2 | CUDA_R_16BF | CUDA_R_16BF | CUDA_R_16BF 6 |
| CUDA_R_16F | CUDA_R_16F | CUDA_R_16F 6 |
| CUDA_R_32F | CUDA_R_32F | CUDA_R_16BF 6 |
| CUDA_R_8F_E5M2 | CUDA_R_8F_E4M3 | CUDA_R_16BF | CUDA_R_16BF | CUDA_R_16BF 6 |
| CUDA_R_16F | CUDA_R_16F | CUDA_R_16F 6 |
| CUDA_R_32F | CUDA_R_32F | CUDA_R_16BF 6 |
| CUDA_R_16BF | CUDA_R_16BF | CUDA_R_16BF | CUDA_R_16BF | CUDA_R_16BF 6 |
| CUDA_R_32F | CUDA_R_32F | CUDA_R_16BF 6 |
| CUDA_R_16F | CUDA_R_16F | CUDA_R_16F | CUDA_R_16F | CUDA_R_16F 6 |
| CUDA_R_32F | CUDA_R_32F | CUDA_R_16BF 6 |


> **Note**

Note
Because the shape information for the matrices is only available on the GPU (see CUBLASLT_GROUPED_MATRIX_LAYOUT_ROWS_ARRAY, CUBLASLT_GROUPED_MATRIX_LAYOUT_COLS_ARRAY, and CUBLASLT_GROUPED_MATRIX_LAYOUT_LD_ARRAY), the arguments validation is very limited. So it is possible that invalid arguments are not detected which will result in an undefined behavior.


**NOTES:**


**6(1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27,28,29,30,31,32,33,34,35,36,37,38,39,40,41,42,43,44,45,46)**
: Epilogue modes that combine ReLU, dReLu, GELU, or dGELU with Bias (see CUBLASLT_MATMUL_DESC_EPILOGUE in cublasLtMatmulDescAttributes_t) are not supported when D matrix memory order is defined as CUBLASLT_ORDER_ROW. For best performance when using the bias vector, specify zero beta and set pointer mode to CUBLASLT_POINTER_MODE_HOST.

**7(1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17)**
: Use of CUBLAS_ORDER_ROW together with CUBLAS_OP_C (Hermitian operator) is not supported unless all of A, B, C, and D matrices use the CUBLAS_ORDER_ROW ordering.

**8(1,2,3,4,5,6,7,8,9,10)**
: FP8 DType is not supported when scaling modes are one of CUBLASLT_MATMUL_MATRIX_SCALE_OUTER_VEC_32F, CUBLASLT_MATMUL_MATRIX_SCALE_VEC128_32F, and CUBLASLT_MATMUL_MATRIX_SCALE_BLK128x128_32F.



**Parameters:**


| Parameter | Memory | Input / Output | Description |
| --- | --- | --- | --- |
| lightHandle |  | Input | Pointer to the allocated cuBLASLt handle for the cuBLASLt context. See cublasLtHandle_t. |
| computeDesc |  | Input | Handle to a previously created matrix multiplication descriptor of type cublasLtMatmulDesc_t. |
| alpha, beta | Device or host | Input | Pointers to the scalars used in the multiplication. |
| A, B, and C | Device | Input | Pointers to the GPU memory associated with the corresponding descriptors Adesc, Bdesc and Cdesc. |
| Adesc, Bdesc and Cdesc |  | Input | Handles to the previous created descriptors of the type cublasLtMatrixLayout_t. |
| D | Device | Output | Pointer to the GPU memory associated with the descriptor Ddesc. |
| Ddesc |  | Input | Handle to the previous created descriptor of the type cublasLtMatrixLayout_t. |
| algo |  | Input | Handle for matrix multiplication algorithm to be used. See cublasLtMatmulAlgo_t. When NULL, an implicit heuristics query with default search preferences will be performed to determine actual algorithm to use. |
| workspace | Device |  | Pointer to the workspace buffer allocated in the GPU memory. Must be 256B aligned (i.e. lowest 8 bits of address must be 0). |
| workspaceSizeInBytes |  | Input | Size of the workspace. |
| stream | Host | Input | The CUDA stream where all the GPU work will be submitted. |


**Returns:**


| Return Value | Description |
| --- | --- |
| CUBLAS_STATUS_NOT_INITIALIZED | If cuBLASLt handle has not been initialized. |
| CUBLAS_STATUS_INVALID_VALUE | If the parameters are unexpectedly NULL, in conflict or in an impossible configuration. For example, when workspaceSizeInBytes is less than workspace required by the configured algo. |
| CUBLAS_STATUS_NOT_SUPPORTED | If the current implementation on the selected device doesn’t support the configured operation. |
| CUBLAS_STATUS_ARCH_MISMATCH | If the configured operation cannot be run using the selected device. |
| CUBLAS_STATUS_EXECUTION_FAILED | If CUDA reported an execution error from the device. |
| CUBLAS_STATUS_SUCCESS | If the operation completed successfully. |


See [cublasStatus_t](#cublasstatus-t) for a complete list of valid return codes.





### 3.4.18. cublasLtMatmulAlgoCapGetAttribute()



```c++

cublasStatus_t cublasLtMatmulAlgoCapGetAttribute(
      const cublasLtMatmulAlgo_t *algo,
      cublasLtMatmulAlgoCapAttributes_t attr,
      void *buf,
      size_t sizeInBytes,
      size_t *sizeWritten);


```


This function returns the value of the queried capability attribute for an initialized [cublasLtMatmulAlgo_t](#cublasltmatmulalgo-t) descriptor structure. The capability attribute value is retrieved from the enumerated type [cublasLtMatmulAlgoCapAttributes_t](#cublasltmatmulalgocapattributes-t).


For example, to get list of supported Tile IDs:



```c++

cublasLtMatmulTile_t tiles[CUBLASLT_MATMUL_TILE_END];
size_t num_tiles, size_written;
if (cublasLtMatmulAlgoCapGetAttribute(algo, CUBLASLT_ALGO_CAP_TILE_IDS, tiles, sizeof(tiles), &size_written) == CUBLAS_STATUS_SUCCESS) {
  num_tiles = size_written / sizeof(tiles[0]);}


```


**Parameters**:


| Parameter | Memory | Input / Output | Description |
| --- | --- | --- | --- |
| algo |  | Input | Pointer to the previously created opaque structure holding the matrix multiply algorithm descriptor. See cublasLtMatmulAlgo_t. |
| attr |  | Input | The capability attribute whose value will be retrieved by this function. See cublasLtMatmulAlgoCapAttributes_t. |
| buf |  | Output | The attribute value returned by this function. |
| sizeInBytes |  | Input | Size of buf buffer (in bytes) for verification. |
| sizeWritten |  | Output | Valid only when the return value is CUBLAS_STATUS_SUCCESS. If sizeInBytes is non-zero: then sizeWritten is the number of bytes actually written; if sizeInBytes is 0: then sizeWritten is the number of bytes needed to write full contents. |


**Returns**:


| Return Value | Description |
| --- | --- |
| CUBLAS_STATUS_INVALID_VALUE | If sizeInBytes is 0 and sizeWritten is NULL, or
if sizeInBytes is non-zero and buf is NULL, or
if sizeInBytes doesn’t match size of internal storage for the selected attribute |
| CUBLAS_STATUS_SUCCESS | If attribute’s value was successfully written to user memory. |


See [cublasStatus_t](#cublasstatus-t) for a complete list of valid return codes.





### 3.4.19. cublasLtMatmulAlgoCheck()



```c++

cublasStatus_t cublasLtMatmulAlgoCheck(
      cublasLtHandle_t lightHandle,
      cublasLtMatmulDesc_t operationDesc,
      cublasLtMatrixLayout_t Adesc,
      cublasLtMatrixLayout_t Bdesc,
      cublasLtMatrixLayout_t Cdesc,
      cublasLtMatrixLayout_t Ddesc,
      const cublasLtMatmulAlgo_t *algo,
      cublasLtMatmulHeuristicResult_t *result);


```


This function performs the correctness check on the matrix multiply algorithm descriptor for the matrix multiply operation [cublasLtMatmul()](#cublasltmatmul) function with the given input matrices A, B and C, and the output matrix D. It checks whether the descriptor is supported on the current device, and returns the result containing the required workspace and the calculated wave count.


> **Note**

Note
CUBLAS_STATUS_SUCCESS doesn’t fully guarantee that the algo will run. The algo will fail if, for example, the buffers are not correctly aligned. However, if cublasLtMatmulAlgoCheck() fails, the algo will not run.


**Parameters**:


| Parameter | Memory | Input / Output | Description |
| --- | --- | --- | --- |
| lightHandle |  | Input | Pointer to the allocated cuBLASLt handle for the cuBLASLt context. See cublasLtHandle_t. |
| operationDesc |  | Input | Handle to a previously created matrix multiplication descriptor of type cublasLtMatmulDesc_t. |
| Adesc, Bdesc, Cdesc, and Ddesc |  | Input | Handles to the previously created matrix layout descriptors of the type cublasLtMatrixLayout_t. |
| algo |  | Input | Descriptor which specifies which matrix multiplication algorithm should be used. See cublasLtMatmulAlgo_t. May point to result->algo. |
| result |  | Output | Pointer to the structure holding the results returned by this function. The results comprise of the required workspace and the calculated wave count. The algo field is never updated. See cublasLtMatmulHeuristicResult_t. |


**Returns**:


| Return Value | Description |
| --- | --- |
| CUBLAS_STATUS_INVALID_VALUE | If matrix layout descriptors or the operation descriptor do not match the algo descriptor. |
| CUBLAS_STATUS_NOT_SUPPORTED | If the algo configuration or data type combination is not currently supported on the given device. |
| CUBLAS_STATUS_ARCH_MISMATCH | If the algo configuration cannot be run using the selected device. |
| CUBLAS_STATUS_SUCCESS | If the check was successful. |


See [cublasStatus_t](#cublasstatus-t) for a complete list of valid return codes.





### 3.4.20. cublasLtMatmulAlgoConfigGetAttribute()



```c++

cublasStatus_t cublasLtMatmulAlgoConfigGetAttribute(
      const cublasLtMatmulAlgo_t *algo,
      cublasLtMatmulAlgoConfigAttributes_t attr,
      void *buf,
      size_t sizeInBytes,
      size_t *sizeWritten);


```


This function returns the value of the queried configuration attribute for an initialized [cublasLtMatmulAlgo_t](#cublasltmatmulalgo-t) descriptor. The configuration attribute value is retrieved from the enumerated type [cublasLtMatmulAlgoConfigAttributes_t](#cublasltmatmulalgoconfigattributes-t).


**Parameters**:


| Parameter | Memory | Input / Output | Description |
| --- | --- | --- | --- |
| algo |  | Input | Pointer to the previously created opaque structure holding the matrix multiply algorithm descriptor. See cublasLtMatmulAlgo_t. |
| attr |  | Input | The configuration attribute whose value will be retrieved by this function. See cublasLtMatmulAlgoConfigAttributes_t. |
| buf |  | Output | The attribute value returned by this function. |
| sizeInBytes |  | Input | Size of buf buffer (in bytes) for verification. |
| sizeWritten |  | Output | Valid only when the return value is CUBLAS_STATUS_SUCCESS. If sizeInBytes is non-zero: then sizeWritten is the number of bytes actually written; if sizeInBytes is 0: then sizeWritten is the number of bytes needed to write full contents. |


**Returns**:


| Return Value | Description |
| --- | --- |
| CUBLAS_STATUS_INVALID_VALUE | If sizeInBytes is 0 and sizeWritten is NULL, or
if sizeInBytes is non-zero and buf is NULL, or
if sizeInBytes doesn’t match size of internal storage for the selected attribute |
| CUBLAS_STATUS_SUCCESS | If attribute’s value was successfully written to user memory. |


See [cublasStatus_t](#cublasstatus-t) for a complete list of valid return codes.





### 3.4.21. cublasLtMatmulAlgoConfigSetAttribute()



```c++

cublasStatus_t cublasLtMatmulAlgoConfigSetAttribute(
      cublasLtMatmulAlgo_t *algo,
      cublasLtMatmulAlgoConfigAttributes_t attr,
      const void *buf,
      size_t sizeInBytes);


```


This function sets the value of the specified configuration attribute for an initialized [cublasLtMatmulAlgo_t](#cublasltmatmulalgo-t) descriptor. The configuration attribute is an enumerant of the type [cublasLtMatmulAlgoConfigAttributes_t](#cublasltmatmulalgoconfigattributes-t).


**Parameters**:


| Parameter | Memory | Input / Output | Description |
| --- | --- | --- | --- |
| algo |  | Input | Pointer to the previously created opaque structure holding the matrix multiply algorithm descriptor. See cublasLtMatmulAlgo_t. |
| attr |  | Input | The configuration attribute whose value will be set by this function. See cublasLtMatmulAlgoConfigAttributes_t. |
| buf |  | Input | The value to which the configuration attribute should be set. |
| sizeInBytes |  | Input | Size of buf buffer (in bytes) for verification. |


**Returns**:


| Return Value | Description |
| --- | --- |
| CUBLAS_STATUS_INVALID_VALUE | If buf is NULL or sizeInBytes doesn’t match the size of the internal storage for the selected attribute. |
| CUBLAS_STATUS_SUCCESS | If the attribute was set successfully. |


See [cublasStatus_t](#cublasstatus-t) for a complete list of valid return codes.





### 3.4.22. cublasLtMatmulAlgoGetHeuristic()



```c++

cublasStatus_t cublasLtMatmulAlgoGetHeuristic(
      cublasLtHandle_t lightHandle,
      cublasLtMatmulDesc_t operationDesc,
      cublasLtMatrixLayout_t Adesc,
      cublasLtMatrixLayout_t Bdesc,
      cublasLtMatrixLayout_t Cdesc,
      cublasLtMatrixLayout_t Ddesc,
      cublasLtMatmulPreference_t preference,
      int requestedAlgoCount,
      cublasLtMatmulHeuristicResult_t heuristicResultsArray[],
      int *returnAlgoCount);


```


This function retrieves the possible algorithms for the matrix multiply operation [cublasLtMatmul()](#cublasltmatmul) function with the given input matrices A, B and C, and the output matrix D. The output is placed in `heuristicResultsArray[]` in the order of increasing estimated compute time.


**Parameters**:


| Parameter | Memory | Input / Output | Description |
| --- | --- | --- | --- |
| lightHandle |  | Input | Pointer to the allocated cuBLASLt handle for the cuBLASLt context. See cublasLtHandle_t. |
| operationDesc |  | Input | Handle to a previously created matrix multiplication descriptor of type cublasLtMatmulDesc_t. |
| Adesc, Bdesc, Cdesc, and Ddesc |  | Input | Handles to the previously created matrix layout descriptors of the type cublasLtMatrixLayout_t. |
| preference |  | Input | Pointer to the structure holding the heuristic search preferences descriptor. See cublasLtMatmulPreference_t. |
| requestedAlgoCount |  | Input | Size of the heuristicResultsArray (in elements). This is the requested maximum number of algorithms to return. |
| heuristicResultsArray[] |  | Output | Array containing the algorithm heuristics and associated runtime characteristics, returned by this function, in the order of increasing estimated compute time. |
| returnAlgoCount |  | Output | Number of algorithms returned by this function. This is the number of heuristicResultsArray elements written. |


**Returns**:


| Return Value | Description |
| --- | --- |
| CUBLAS_STATUS_INVALID_VALUE | If requestedAlgoCount is less or equal to zero. |
| CUBLAS_STATUS_NOT_SUPPORTED | If no heuristic function available for current configuration. |
| CUBLAS_STATUS_SUCCESS | If query was successful. Inspect heuristicResultsArray[0 to (returnAlgoCount -1)].state for the status of the results. |


See [cublasStatus_t](#cublasstatus-t) for a complete list of valid return codes.


> **Note**

Note
This function may load some kernels using CUDA Driver API which may fail when there is no available GPU memory. Do not allocate the entire VRAM before running cublasLtMatmulAlgoGetHeuristic().





### 3.4.23. cublasLtMatmulAlgoGetIds()



```c++

cublasStatus_t cublasLtMatmulAlgoGetIds(
      cublasLtHandle_t lightHandle,
      cublasComputeType_t computeType,
      cudaDataType_t scaleType,
      cudaDataType_t Atype,
      cudaDataType_t Btype,
      cudaDataType_t Ctype,
      cudaDataType_t Dtype,
      int requestedAlgoCount,
      int algoIdsArray[],
      int *returnAlgoCount);


```


This function retrieves the IDs of all the matrix multiply algorithms that are valid, and can potentially be run by the [cublasLtMatmul()](#cublasltmatmul) function, for given types of the input matrices A, B and C, and of the output matrix D.


> **Note**

Note
The IDs are returned in no particular order. To make sure the best possible algo is contained in the list, make requestedAlgoCount large enough to receive the full list. The list is guaranteed to be full if returnAlgoCount < requestedAlgoCount.


**Parameters**:


| Parameter | Memory | Input / Output | Description |
| --- | --- | --- | --- |
| lightHandle |  | Input | Pointer to the allocated cuBLASLt handle for the cuBLASLt context. See cublasLtHandle_t. |
| computeType, scaleType, Atype, Btype, Ctype, and Dtype |  | Inputs | Data types of the computation type, scaling factors and of the operand matrices. See cudaDataType_t. |
| requestedAlgoCount |  | Input | Number of algorithms requested. Must be > 0. |
| algoIdsArray[] |  | Output | Array containing the algorithm IDs returned by this function. |
| returnAlgoCount |  | Output | Number of algorithms actually returned by this function. |


**Returns**:


| Return Value | Description |
| --- | --- |
| CUBLAS_STATUS_INVALID_VALUE | If requestedAlgoCount is less or equal to zero. |
| CUBLAS_STATUS_SUCCESS | If query was successful. Inspect returnAlgoCount to get actual number of IDs available. |


See [cublasStatus_t](#cublasstatus-t) for a complete list of valid return codes.





### 3.4.24. cublasLtMatmulAlgoInit()



```c++

cublasStatus_t cublasLtMatmulAlgoInit(
      cublasLtHandle_t lightHandle,
      cublasComputeType_t computeType,
      cudaDataType_t scaleType,
      cudaDataType_t Atype,
      cudaDataType_t Btype,
      cudaDataType_t Ctype,
      cudaDataType_t Dtype,
      int algoId,
      cublasLtMatmulAlgo_t *algo);


```


This function initializes the matrix multiply algorithm structure for the [cublasLtMatmul()](#cublasltmatmul) , for a specified matrix multiply algorithm and input matrices A, B and C, and the output matrix D.


**Parameters**:


| Parameter | Memory | Input / Output | Description |
| --- | --- | --- | --- |
| lightHandle |  | Input | Pointer to the allocated cuBLASLt handle for the cuBLASLt context. See cublasLtHandle_t. |
| computeType |  | Input | Compute type. See CUBLASLT_MATMUL_DESC_COMPUTE_TYPE of cublasLtMatmulDescAttributes_t. |
| scaleType |  | Input | Scale type. See CUBLASLT_MATMUL_DESC_SCALE_TYPEof cublasLtMatmulDescAttributes_t. Usually same as computeType. |
| Atype, Btype, Ctype, and Dtype |  | Input | Datatype precision for the input and output matrices. See cudaDataType_t . |
| algoId |  | Input | Specifies the algorithm being initialized. Should be a valid algoId returned by the cublasLtMatmulAlgoGetIds() function. |
| algo |  | Input | Pointer to the opaque structure to be initialized. See cublasLtMatmulAlgo_t. |


**Returns**:


| Return Value | Description |
| --- | --- |
| CUBLAS_STATUS_INVALID_VALUE | If algo is NULL or algoId is outside the recognized range. |
| CUBLAS_STATUS_NOT_SUPPORTED | If algoId is not supported for given combination of data types. |
| CUBLAS_STATUS_SUCCESS | If the structure was successfully initialized. |


See [cublasStatus_t](#cublasstatus-t) for a complete list of valid return codes.





### 3.4.25. cublasLtMatmulDescCreate()



```c++

cublasStatus_t cublasLtMatmulDescCreate( cublasLtMatmulDesc_t *matmulDesc,
                                         cublasComputeType_t computeType,
                                         cudaDataType_t scaleType);


```


This function creates a matrix multiply descriptor by allocating the memory needed to hold its opaque structure.


**Parameters**:


| Parameter | Memory | Input / Output | Description |
| --- | --- | --- | --- |
| matmulDesc |  | Output | Pointer to the structure holding the matrix multiply descriptor created by this function. See cublasLtMatmulDesc_t. |
| computeType |  | Input | Enumerant that specifies the data precision for the matrix multiply descriptor this function creates. See cublasComputeType_t. |
| scaleType |  | Input | Enumerant that specifies the data precision for the matrix transform descriptor this function creates. See cudaDataType_t. |


**Returns**:


| Return Value | Description |
| --- | --- |
| CUBLAS_STATUS_ALLOC_FAILED | If memory could not be allocated. |
| CUBLAS_STATUS_SUCCESS | If the descriptor was created successfully. |


See [cublasStatus_t](#cublasstatus-t) for a complete list of valid return codes.





### 3.4.26. cublasLtMatmulDescInit()



```c++

cublasStatus_t cublasLtMatmulDescInit( cublasLtMatmulDesc_t matmulDesc,
                                       cublasComputeType_t computeType,
                                       cudaDataType_t scaleType);


```


This function initializes a matrix multiply descriptor in a previously allocated one.


**Parameters**:


| Parameter | Memory | Input / Output | Description |
| --- | --- | --- | --- |
| matmulDesc |  | Output | Pointer to the structure holding the matrix multiply descriptor initialized by this function. See cublasLtMatmulDesc_t. |
| computeType |  | Input | Enumerant that specifies the data precision for the matrix multiply descriptor this function initializes. See cublasComputeType_t. |
| scaleType |  | Input | Enumerant that specifies the data precision for the matrix transform descriptor this function initializes. See cudaDataType_t. |


**Returns**:


| Return Value | Description |
| --- | --- |
| CUBLAS_STATUS_ALLOC_FAILED | If memory could not be allocated. |
| CUBLAS_STATUS_SUCCESS | If the descriptor was created successfully. |


See [cublasStatus_t](#cublasstatus-t) for a complete list of valid return codes.





### 3.4.27. cublasLtMatmulDescDestroy()



```c++

cublasStatus_t cublasLtMatmulDescDestroy(
      cublasLtMatmulDesc_t matmulDesc);


```


This function destroys a previously created matrix multiply descriptor object.


**Parameters**:


| Parameter | Memory | Input / Output | Description |
| --- | --- | --- | --- |
| matmulDesc |  | Input | Pointer to the structure holding the matrix multiply descriptor that should be destroyed by this function. See cublasLtMatmulDesc_t. |


**Returns**:


| Return Value | Description |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | If operation was successful. |


See [cublasStatus_t](#cublasstatus-t) for a complete list of valid return codes.





### 3.4.28. cublasLtMatmulDescGetAttribute()



```c++

cublasStatus_t cublasLtMatmulDescGetAttribute(
      cublasLtMatmulDesc_t matmulDesc,
      cublasLtMatmulDescAttributes_t attr,
      void *buf,
      size_t sizeInBytes,
      size_t *sizeWritten);


```


This function returns the value of the queried attribute belonging to a previously created matrix multiply descriptor.


**Parameters**:


| Parameter | Memory | Input / Output | Description |
| --- | --- | --- | --- |
| matmulDesc |  | Input | Pointer to the previously created structure holding the matrix multiply descriptor queried by this function. See cublasLtMatmulDesc_t. |
| attr |  | Input | The attribute that will be retrieved by this function. See cublasLtMatmulDescAttributes_t. |
| buf |  | Output | Memory address containing the attribute value retrieved by this function. |
| sizeInBytes |  | Input | Size of buf buffer (in bytes) for verification. |
| sizeWritten |  | Output | Valid only when the return value is CUBLAS_STATUS_SUCCESS. If sizeInBytes is non-zero: then sizeWritten is the number of bytes actually written; if sizeInBytes is 0: then sizeWritten is the number of bytes needed to write full contents. |


**Returns**:


| Return Value | Description |
| --- | --- |
| CUBLAS_STATUS_INVALID_VALUE | If sizeInBytes is 0 and sizeWritten is NULL, or
if sizeInBytes is non-zero and buf is NULL, or
sizeInBytes doesn’t match size of internal storage for the selected attribute |
| CUBLAS_STATUS_SUCCESS | If attribute’s value was successfully written to user memory. |


See [cublasStatus_t](#cublasstatus-t) for a complete list of valid return codes.





### 3.4.29. cublasLtMatmulDescSetAttribute()



```c++

cublasStatus_t cublasLtMatmulDescSetAttribute(
      cublasLtMatmulDesc_t matmulDesc,
      cublasLtMatmulDescAttributes_t attr,
      const void *buf,
      size_t sizeInBytes);


```


This function sets the value of the specified attribute belonging to a previously created matrix multiply descriptor.


**Parameters**:


| Parameter | Memory | Input / Output | Description |
| --- | --- | --- | --- |
| matmulDesc |  | Input | Pointer to the previously created structure holding the matrix multiply descriptor queried by this function. See cublasLtMatmulDesc_t. |
| attr |  | Input | The attribute that will be set by this function. See cublasLtMatmulDescAttributes_t. |
| buf |  | Input | The value to which the specified attribute should be set. |
| sizeInBytes |  | Input | Size of buf buffer (in bytes) for verification. |


**Returns**:


| Return Value | Description |
| --- | --- |
| CUBLAS_STATUS_INVALID_VALUE | If buf is NULL or sizeInBytes doesn’t match the size of the internal storage for the selected attribute. |
| CUBLAS_STATUS_SUCCESS | If the attribute was set successfully. |


See [cublasStatus_t](#cublasstatus-t) for a complete list of valid return codes.





### 3.4.30. cublasLtMatmulPreferenceCreate()



```c++

cublasStatus_t cublasLtMatmulPreferenceCreate(
      cublasLtMatmulPreference_t *pref);


```


This function creates a matrix multiply heuristic search preferences descriptor by allocating the memory needed to hold its opaque structure.


**Parameters**:


| Parameter | Memory | Input / Output | Description |
| --- | --- | --- | --- |
| pref |  | Output | Pointer to the structure holding the matrix multiply preferences descriptor created by this function. See cublasLtMatrixLayout_t. |


**Returns**:


| Return Value | Description |
| --- | --- |
| CUBLAS_STATUS_ALLOC_FAILED | If memory could not be allocated. |
| CUBLAS_STATUS_SUCCESS | If the descriptor was created successfully. |


See [cublasStatus_t](#cublasstatus-t) for a complete list of valid return codes.





### 3.4.31. cublasLtMatmulPreferenceInit()



```c++

cublasStatus_t cublasLtMatmulPreferenceInit(
      cublasLtMatmulPreference_t pref);


```


This function initializes a matrix multiply heuristic search preferences descriptor in a previously allocated one.


**Parameters**:


| Parameter | Memory | Input / Output | Description |
| --- | --- | --- | --- |
| pref |  | Output | Pointer to the structure holding the matrix multiply preferences descriptor created by this function. See cublasLtMatrixLayout_t. |


**Returns**:


| Return Value | Description |
| --- | --- |
| CUBLAS_STATUS_ALLOC_FAILED | If memory could not be allocated. |
| CUBLAS_STATUS_SUCCESS | If the descriptor was created successfully. |


See [cublasStatus_t](#cublasstatus-t) for a complete list of valid return codes.





### 3.4.32. cublasLtMatmulPreferenceDestroy()



```c++

cublasStatus_t cublasLtMatmulPreferenceDestroy(
      cublasLtMatmulPreference_t pref);


```


This function destroys a previously created matrix multiply preferences descriptor object.


**Parameters**:


| Parameter | Memory | Input / Output | Description |
| --- | --- | --- | --- |
| pref |  | Input | Pointer to the structure holding the matrix multiply preferences descriptor that should be destroyed by this function. See cublasLtMatmulPreference_t. |


**Returns**:


| Return Value | Description |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | If the operation was successful. |


See [cublasStatus_t](#cublasstatus-t) for a complete list of valid return codes.





### 3.4.33. cublasLtMatmulPreferenceGetAttribute()



```c++

cublasStatus_t cublasLtMatmulPreferenceGetAttribute(
      cublasLtMatmulPreference_t pref,
      cublasLtMatmulPreferenceAttributes_t attr,
      void *buf,
      size_t sizeInBytes,
      size_t *sizeWritten);


```


This function returns the value of the queried attribute belonging to a previously created matrix multiply heuristic search preferences descriptor.


**Parameters**:


| Parameter | Memory | Input / Output | Description |
| --- | --- | --- | --- |
| pref |  | Input | Pointer to the previously created structure holding the matrix multiply heuristic search preferences descriptor queried by this function. See cublasLtMatmulPreference_t. |
| attr |  | Input | The attribute that will be queried by this function. See cublasLtMatmulPreferenceAttributes_t. |
| buf |  | Output | Memory address containing the attribute value retrieved by this function. |
| sizeInBytes |  | Input | Size of buf buffer (in bytes) for verification. |
| sizeWritten |  | Output | Valid only when the return value is CUBLAS_STATUS_SUCCESS. If sizeInBytes is non-zero: then sizeWritten is the number of bytes actually written; if sizeInBytes is 0: then sizeWritten is the number of bytes needed to write full contents. |


**Returns**:


| Return Value | Description |
| --- | --- |
| CUBLAS_STATUS_INVALID_VALUE | If sizeInBytes is 0 and sizeWritten is NULL, or
if sizeInBytes is non-zero and buf is NULL, or
sizeInBytes doesn’t match size of internal storage for the selected attribute |
| CUBLAS_STATUS_SUCCESS | If attribute’s value was successfully written to user memory. |


See [cublasStatus_t](#cublasstatus-t) for a complete list of valid return codes.





### 3.4.34. cublasLtMatmulPreferenceSetAttribute()



```c++

cublasStatus_t cublasLtMatmulPreferenceSetAttribute(
      cublasLtMatmulPreference_t pref,
      cublasLtMatmulPreferenceAttributes_t attr,
      const void *buf,
      size_t sizeInBytes);


```


This function sets the value of the specified attribute belonging to a previously created matrix multiply preferences descriptor.


**Parameters**:


| Parameter | Memory | Input / Output | Description |
| --- | --- | --- | --- |
| pref |  | Input | Pointer to the previously created structure holding the matrix multiply preferences descriptor queried by this function. See cublasLtMatmulPreference_t. |
| attr |  | Input | The attribute that will be set by this function. See cublasLtMatmulPreferenceAttributes_t. |
| buf |  | Input | The value to which the specified attribute should be set. |
| sizeInBytes |  | Input | Size of buf buffer (in bytes) for verification. |


**Returns**:


| Return Value | Description |
| --- | --- |
| CUBLAS_STATUS_INVALID_VALUE | If buf is NULL or sizeInBytes doesn’t match the size of the internal storage for the selected attribute. |
| CUBLAS_STATUS_SUCCESS | If the attribute was set successfully. |


See [cublasStatus_t](#cublasstatus-t) for a complete list of valid return codes.





### 3.4.35. cublasLtMatrixLayoutCreate()



```c++

cublasStatus_t cublasLtMatrixLayoutCreate( cublasLtMatrixLayout_t *matLayout,
                                           cudaDataType type,
                                           uint64_t rows,
                                           uint64_t cols,
                                           int64_t ld);


```


This function creates a matrix layout descriptor by allocating the memory needed to hold its opaque structure.


**Parameters**:


| Parameter | Memory | Input / Output | Description |
| --- | --- | --- | --- |
| matLayout |  | Output | Pointer to the structure holding the matrix layout descriptor created by this function. See cublasLtMatrixLayout_t. |
| type |  | Input | Enumerant that specifies the data precision for the matrix layout descriptor this function creates. See cudaDataType_t. |
| rows, cols |  | Input | Number of rows and columns of the matrix. |
| ld |  | Input | The leading dimension of the matrix. In column major layout, this is the number of elements to jump to reach the next column. Thus ld >= m (number of rows). |


**Returns**:


| Return Value | Description |
| --- | --- |
| CUBLAS_STATUS_ALLOC_FAILED | If the memory could not be allocated. |
| CUBLAS_STATUS_SUCCESS | If the descriptor was created successfully. |


See [cublasStatus_t](#cublasstatus-t) for a complete list of valid return codes.





### 3.4.36. cublasLtMatrixLayoutInit()



```c++

cublasStatus_t cublasLtMatrixLayoutInit( cublasLtMatrixLayout_t matLayout,
                                         cudaDataType type,
                                         uint64_t rows,
                                         uint64_t cols,
                                         int64_t ld);


```


This function initializes a matrix layout descriptor in a previously allocated one.


**Parameters**:


| Parameter | Memory | Input / Output | Description |
| --- | --- | --- | --- |
| matLayout |  | Output | Pointer to the structure holding the matrix layout descriptor initialized by this function. See cublasLtMatrixLayout_t. |
| type |  | Input | Enumerant that specifies the data precision for the matrix layout descriptor this function initializes. See cudaDataType_t. |
| rows, cols |  | Input | Number of rows and columns of the matrix. |
| ld |  | Input | The leading dimension of the matrix. In column major layout, this is the number of elements to jump to reach the next column. Thus ld >= m (number of rows). |


**Returns**:


| Return Value | Description |
| --- | --- |
| CUBLAS_STATUS_ALLOC_FAILED | If the memory could not be allocated. |
| CUBLAS_STATUS_SUCCESS | If the descriptor was created successfully. |


See [cublasStatus_t](#cublasstatus-t) for a complete list of valid return codes.





### 3.4.37. cublasLtGroupedMatrixLayoutCreate()



```c++

cublasStatus_t cublasLtGroupedMatrixLayoutCreate( cublasLtMatrixLayout_t *matLayout,
                                           cudaDataType type,
                                           int groupCount,
                                           const void* rows_array,
                                           const void* cols_array,
                                           const void* ld_array);


```


Experimental: This function creates a grouped matrix layout descriptor by allocating the memory needed to hold its opaque structure.


**Parameters**:


| Parameter | Memory | Input / Output | Description |
| --- | --- | --- | --- |
| matLayout |  | Output | Pointer to the structure holding the matrix layout descriptor created by this function. See cublasLtMatrixLayout_t. |
| type |  | Input | Enumerant that specifies the data precision for the matrix layout descriptor this function creates. See cudaDataType_t. |
| groupCount |  | Input | Number of groups in the grouped matrix layout descriptor. |
| rows_array |  | Input | Pointer to a device array of rows of the grouped matrix layout descriptor. |
| cols_array |  | Input | Pointer to a device array of columns of the grouped matrix layout descriptor. |
| ld_array |  | Input | Pointer to a device array of leading dimensions of the grouped matrix layout descriptor. |


**Returns**:


| Return Value | Description |
| --- | --- |
| CUBLAS_STATUS_ALLOC_FAILED | If the memory could not be allocated. |
| CUBLAS_STATUS_SUCCESS | If the descriptor was created successfully. |


See [cublasStatus_t](#cublasstatus-t) for a complete list of valid return codes.





### 3.4.38. cublasLtGroupedMatrixLayoutInit()



```c++

cublasStatus_t cublasLtGroupedMatrixLayoutInit( cublasLtMatrixLayout_t matLayout,
                                         cudaDataType type,
                                         int groupCount,
                                         const void* rows_array,
                                         const void* cols_array,
                                         const void* ld_array);


```


Experimental: This function initializes a grouped matrix layout descriptor in a previously allocated one.


**Parameters**:


| Parameter | Memory | Input / Output | Description |
| --- | --- | --- | --- |
| matLayout |  | Output | Pointer to the structure holding the matrix layout descriptor initialized by this function. See cublasLtMatrixLayout_t. |
| type |  | Input | Enumerant that specifies the data precision for the matrix layout descriptor this function initializes. See cudaDataType_t. |
| groupCount |  | Input | Number of groups in the grouped matrix layout descriptor. |
| rows_array |  | Input | Pointer to a device array of rows of the grouped matrix layout descriptor. |
| cols_array |  | Input | Pointer to a device array of columns of the grouped matrix layout descriptor. |
| ld_array |  | Input | Pointer to a device array of leading dimensions of the grouped matrix layout descriptor. |


**Returns**:


| Return Value | Description |
| --- | --- |
| CUBLAS_STATUS_ALLOC_FAILED | If the memory could not be allocated. |
| CUBLAS_STATUS_SUCCESS | If the descriptor was created successfully. |


See [cublasStatus_t](#cublasstatus-t) for a complete list of valid return codes.





### 3.4.39. cublasLtMatrixLayoutDestroy()



```c++

cublasStatus_t cublasLtMatrixLayoutDestroy(
      cublasLtMatrixLayout_t matLayout);


```


This function destroys a previously created matrix layout descriptor object.


**Parameters**:


| Parameter | Memory | Input / Output | Description |
| --- | --- | --- | --- |
| matLayout |  | Input | Pointer to the structure holding the matrix layout descriptor that should be destroyed by this function. See cublasLtMatrixLayout_t. |


**Returns**:


| Return Value | Description |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | If the operation was successful. |


See [cublasStatus_t](#cublasstatus-t) for a complete list of valid return codes.





### 3.4.40. cublasLtMatrixLayoutGetAttribute()



```c++

cublasStatus_t cublasLtMatrixLayoutGetAttribute(
      cublasLtMatrixLayout_t matLayout,
      cublasLtMatrixLayoutAttribute_t attr,
      void *buf,
      size_t sizeInBytes,
      size_t *sizeWritten);


```


This function returns the value of the queried attribute belonging to the specified matrix layout descriptor.


**Parameters**:


| Parameter | Memory | Input / Output | Description |
| --- | --- | --- | --- |
| matLayout |  | Input | Pointer to the previously created structure holding the matrix layout descriptor queried by this function. See cublasLtMatrixLayout_t. |
| attr |  | Input | The attribute being queried for. See cublasLtMatrixLayoutAttribute_t. |
| buf |  | Output | The attribute value returned by this function. |
| sizeInBytes |  | Input | Size of buf buffer (in bytes) for verification. |
| sizeWritten |  | Output | Valid only when the return value is CUBLAS_STATUS_SUCCESS. If sizeInBytes is non-zero: then sizeWritten is the number of bytes actually written; if sizeInBytes is 0: then sizeWritten is the number of bytes needed to write full contents. |


**Returns**:


| Return Value | Description |
| --- | --- |
| CUBLAS_STATUS_INVALID_VALUE | If sizeInBytes is 0 and sizeWritten is NULL, or
if sizeInBytes is non-zero and buf is NULL, or
sizeInBytes doesn’t match size of internal storage for the selected attribute |
| CUBLAS_STATUS_SUCCESS | If attribute’s value was successfully written to user memory. |


See [cublasStatus_t](#cublasstatus-t) for a complete list of valid return codes.





### 3.4.41. cublasLtMatrixLayoutSetAttribute()



```c++

cublasStatus_t cublasLtMatrixLayoutSetAttribute(
      cublasLtMatrixLayout_t matLayout,
      cublasLtMatrixLayoutAttribute_t attr,
      const void *buf,
      size_t sizeInBytes);


```


This function sets the value of the specified attribute belonging to a previously created matrix layout descriptor.


**Parameters**:


| Parameter | Memory | Input / Output | Description |
| --- | --- | --- | --- |
| matLayout |  | Input | Pointer to the previously created structure holding the matrix layout descriptor queried by this function. See cublasLtMatrixLayout_t. |
| attr |  | Input | The attribute that will be set by this function. See cublasLtMatrixLayoutAttribute_t. |
| buf |  | Input | The value to which the specified attribute should be set. |
| sizeInBytes |  | Input | Size of buf, the attribute buffer. |


**Returns**:


| Return Value | Description |
| --- | --- |
| CUBLAS_STATUS_INVALID_VALUE | If buf is NULL or sizeInBytes doesn’t match size of internal storage for the selected attribute. |
| CUBLAS_STATUS_SUCCESS | If attribute was set successfully. |


See [cublasStatus_t](#cublasstatus-t) for a complete list of valid return codes.





### 3.4.42. cublasLtMatrixTransform()



```c++

cublasStatus_t cublasLtMatrixTransform(
      cublasLtHandle_t lightHandle,
      cublasLtMatrixTransformDesc_t transformDesc,
      const void *alpha,
      const void *A,
      cublasLtMatrixLayout_t Adesc,
      const void *beta,
      const void *B,
      cublasLtMatrixLayout_t Bdesc,
      void *C,
      cublasLtMatrixLayout_t Cdesc,
      cudaStream_t stream);


```


This function computes the matrix transformation operation on the input matrices A and B, to produce the output matrix C, according to the below operation:


`C = alpha*transformation(A) + beta*transformation(B),`


where `A`, `B` are input matrices, and `alpha` and `beta` are input scalars. The transformation operation is defined by the `transformDesc` pointer. This function can be used to change the memory order of data or to scale and shift the values.


**Parameters**:


| Parameter | Memory | Input / Output | Description |
| --- | --- | --- | --- |
| lightHandle |  | Input | Pointer to the allocated cuBLASLt handle for the cuBLASLt context. See cublasLtHandle_t. |
| transformDesc |  | Input | Pointer to the opaque descriptor holding the matrix transformation operation. See cublasLtMatrixTransformDesc_t. |
| alpha, beta | Device or host | Input | Pointers to the scalars used in the multiplication. |
| A, B | Device | Input | Pointers to the GPU memory associated with the corresponding descriptors Adesc and Bdesc. |
| C | Device | Output | Pointer to the GPU memory associated with the Cdesc descriptor. |
| Adesc, Bdesc and Cdesc |  | Input | Handles to the previous created descriptors of the type cublasLtMatrixLayout_t.
Adesc or Bdesc can be NULL if the corresponding pointer is NULL and the corresponding scalar is zero. |
| stream | Host | Input | The CUDA stream where all the GPU work will be submitted. |


**Returns**:


| Return Value | Description |
| --- | --- |
| CUBLAS_STATUS_NOT_INITIALIZED | If cuBLASLt handle has not been initialized. |
| CUBLAS_STATUS_INVALID_VALUE | If the parameters are in conflict or in an impossible configuration. For example, when A is not NULL, but Adesc is NULL. |
| CUBLAS_STATUS_NOT_SUPPORTED | If the current implementation on the selected device does not support the configured operation. |
| CUBLAS_STATUS_ARCH_MISMATCH | If the configured operation cannot be run using the selected device. |
| CUBLAS_STATUS_EXECUTION_FAILED | If CUDA reported an execution error from the device. |
| CUBLAS_STATUS_SUCCESS | If the operation completed successfully. |


See [cublasStatus_t](#cublasstatus-t) for a complete list of valid return codes.





### 3.4.43. cublasLtMatrixTransformDescCreate()



```c++

cublasStatus_t cublasLtMatrixTransformDescCreate(
      cublasLtMatrixTransformDesc_t *transformDesc,
      cudaDataType scaleType);


```


This function creates a matrix transform descriptor by allocating the memory needed to hold its opaque structure.


**Parameters**:


| Parameter | Memory | Input / Output | Description |
| --- | --- | --- | --- |
| transformDesc |  | Output | Pointer to the structure holding the matrix transform descriptor created by this function. See cublasLtMatrixTransformDesc_t. |
| scaleType |  | Input | Enumerant that specifies the data precision for the matrix transform descriptor this function creates. See cudaDataType_t. |


**Returns**:


| Return Value | Description |
| --- | --- |
| CUBLAS_STATUS_ALLOC_FAILED | If memory could not be allocated. |
| CUBLAS_STATUS_SUCCESS | If the descriptor was created successfully. |


See [cublasStatus_t](#cublasstatus-t) for a complete list of valid return codes.





### 3.4.44. cublasLtMatrixTransformDescInit()



```c++

cublasStatus_t cublasLtMatrixTransformDescInit(
      cublasLtMatrixTransformDesc_t transformDesc,
      cudaDataType scaleType);


```


This function initializes a matrix transform descriptor in a previously allocated one.


**Parameters**:


| Parameter | Memory | Input / Output | Description |
| --- | --- | --- | --- |
| transformDesc |  | Output | Pointer to the structure holding the matrix transform descriptor initialized by this function. See cublasLtMatrixTransformDesc_t. |
| scaleType |  | Input | Enumerant that specifies the data precision for the matrix transform descriptor this function initializes. See cudaDataType_t. |


**Returns**:


| Return Value | Description |
| --- | --- |
| CUBLAS_STATUS_ALLOC_FAILED | If memory could not be allocated. |
| CUBLAS_STATUS_SUCCESS | If the descriptor was created successfully. |


See [cublasStatus_t](#cublasstatus-t) for a complete list of valid return codes.





### 3.4.45. cublasLtMatrixTransformDescDestroy()



```c++

cublasStatus_t cublasLtMatrixTransformDescDestroy(
      cublasLtMatrixTransformDesc_t transformDesc);


```


This function destroys a previously created matrix transform descriptor object.


**Parameters**:


| Parameter | Memory | Input / Output | Description |
| --- | --- | --- | --- |
| transformDesc |  | Input | Pointer to the structure holding the matrix transform descriptor that should be destroyed by this function. See cublasLtMatrixTransformDesc_t. |


**Returns**:


| Return Value | Description |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | If the operation was successful. |


See [cublasStatus_t](#cublasstatus-t) for a complete list of valid return codes.





### 3.4.46. cublasLtMatrixTransformDescGetAttribute()



```c++

cublasStatus_t cublasLtMatrixTransformDescGetAttribute(
      cublasLtMatrixTransformDesc_t transformDesc,
      cublasLtMatrixTransformDescAttributes_t attr,
      void *buf,
      size_t sizeInBytes,
      size_t *sizeWritten);


```


This function returns the value of the queried attribute belonging to a previously created matrix transform descriptor.


**Parameters**:


| Parameter | Memory | Input / Output | Description |
| --- | --- | --- | --- |
| transformDesc |  | Input | Pointer to the previously created structure holding the matrix transform descriptor queried by this function. See cublasLtMatrixTransformDesc_t. |
| attr |  | Input | The attribute that will be retrieved by this function. See cublasLtMatrixTransformDescAttributes_t. |
| buf |  | Output | Memory address containing the attribute value retrieved by this function. |
| sizeInBytes |  | Input | Size of buf buffer (in bytes) for verification. |
| sizeWritten |  | Output | Valid only when the return value is CUBLAS_STATUS_SUCCESS. If sizeInBytes is non-zero: then sizeWritten is the number of bytes actually written; if sizeInBytes is 0: then sizeWritten is the number of bytes needed to write full contents. |


**Returns**:


| Return Value | Description |
| --- | --- |
| CUBLAS_STATUS_INVALID_VALUE | If sizeInBytes is zero and sizeWritten is NULL, or
if sizeInBytes is non-zero and buf is NULL, or
if sizeInBytes doesn’t match size of internal storage for the selected attribute |
| CUBLAS_STATUS_SUCCESS | If attribute’s value was successfully written to user memory. |


See [cublasStatus_t](#cublasstatus-t) for a complete list of valid return codes.





### 3.4.47. cublasLtMatrixTransformDescSetAttribute()



```c++

cublasStatus_t cublasLtMatrixTransformDescSetAttribute(
      cublasLtMatrixTransformDesc_t transformDesc,
      cublasLtMatrixTransformDescAttributes_t attr,
      const void *buf,
      size_t sizeInBytes);


```


This function sets the value of the specified attribute belonging to a previously created matrix transform descriptor.


**Parameters**:


| Parameter | Memory | Input / Output | Description |
| --- | --- | --- | --- |
| transformDesc |  | Input | Pointer to the previously created structure holding the matrix transform descriptor queried by this function. See cublasLtMatrixTransformDesc_t. |
| attr |  | Input | The attribute that will be set by this function. See cublasLtMatrixTransformDescAttributes_t. |
| buf |  | Input | The value to which the specified attribute should be set. |
| sizeInBytes |  | Input | Size of buf buffer (in bytes) for verification. |


**Returns**:


| Return Value | Description |
| --- | --- |
| CUBLAS_STATUS_INVALID_VALUE | If buf is NULL or sizeInBytes does not match size of the internal storage for the selected attribute. |
| CUBLAS_STATUS_SUCCESS | If the attribute was set successfully. |


See [cublasStatus_t](#cublasstatus-t) for a complete list of valid return codes.





### 3.4.48. cublasLtEmulationDescInit()



```c++

cublasStatus_t cublasLtEmulationDescInit(cublasLtEmulationDesc_t emulationDesc);


```


This function initializes a previously allocated emulation descriptor.


**Parameters**:


| Parameter | Memory | Input / Output | Description |
| --- | --- | --- | --- |
| emulationDesc |  | Input | Pointer to the previously created structure holding the emulation descriptor queried by this function. See cublasLtEmulationDesc_t. |


**Returns**:


| Return Value | Description |
| --- | --- |
| CUBLAS_STATUS_ALLOC_FAILED | If the size of the pre-allocated space is insufficient. |
| CUBLAS_STATUS_SUCCESS | If the descriptor was created successfully. |


See [cublasStatus_t](#cublasstatus-t) for a complete list of valid return codes.





### 3.4.49. cublasLtEmulationDescCreate()



```c++

cublasStatus_t cublasLtEmulationDescCreate(cublasLtEmulationDesc_t* emulationDesc);


```


This function creates a new emulation descriptor.


**Parameters**:


| Parameter | Memory | Input / Output | Description |
| --- | --- | --- | --- |
| emulationDesc |  | Input | Pointer to the previously created structure holding the emulation descriptor queried by this function. See cublasLtEmulationDesc_t. |


**Returns**:


| Return Value | Description |
| --- | --- |
| CUBLAS_STATUS_ALLOC_FAILED | If memory could not be allocated. |
| CUBLAS_STATUS_SUCCESS | If the descriptor was created successfully. |


See [cublasStatus_t](#cublasstatus-t) for a complete list of valid return codes.





### 3.4.50. cublasLtEmulationDescDestroy()



```c++

cublasStatus_t cublasLtEmulationDescDestroy(cublasLtEmulationDesc_t emulationDesc);


```


This function destroys a previously created emulation descriptor.


**Parameters**:


| Parameter | Memory | Input / Output | Description |
| --- | --- | --- | --- |
| emulationDesc |  | Input | Pointer to the previously created structure holding the emulation descriptor queried by this function. See cublasLtEmulationDesc_t. |


**Returns**:


| Return Value | Description |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | If the descriptor was destroyed successfully. |


See [cublasStatus_t](#cublasstatus-t) for a complete list of valid return codes.





### 3.4.51. cublasLtEmulationDescSetAttribute()



```c++

cublasStatus_t cublasLtEmulationDescSetAttribute(
      cublasLtEmulationDesc_t emulationDesc,
      cublasLtEmulationDescAttributes_t attr,
      const void *buf,
      size_t sizeInBytes);


```


This function sets the value of the specified attribute belonging to a previously created emulation descriptor.


**Parameters**:


| Parameter | Memory | Input / Output | Description |
| --- | --- | --- | --- |
| emulationDesc |  | Input | Pointer to the previously created structure holding the emulation descriptor queried by this function. See cublasLtEmulationDesc_t. |
| attr |  | Input | The attribute that will be set by this function. See cublasLtEmulationDescAttributes_t. |
| buf |  | Input | The value to which the specified attribute should be set. |
| sizeInBytes |  | Input | Size of buf buffer (in bytes) for verification. |


**Returns**:


| Return Value | Description |
| --- | --- |
| CUBLAS_STATUS_INVALID_VALUE | If buf is NULL or sizeInBytes does not match size of the internal storage for the selected attribute. |
| CUBLAS_STATUS_SUCCESS | If the attribute was set successfully. |


See [cublasStatus_t](#cublasstatus-t) for a complete list of valid return codes.





### 3.4.52. cublasLtEmulationDescGetAttribute()



```c++

cublasStatus_t cublasLtEmulationDescGetAttribute(
      cublasLtEmulationDesc_t emulationDesc,
      cublasLtEmulationDescAttributes_t attr,
      void *buf,
      size_t sizeInBytes,
      size_t *sizeWritten);


```


This function returns the value of the queried attribute belonging to a previously created emulation descriptor.


**Parameters**:


| Parameter | Memory | Input / Output | Description |
| --- | --- | --- | --- |
| emulationDesc |  | Input | Pointer to the previously created structure holding the emulation descriptor queried by this function. See cublasLtEmulationDesc_t. |
| attr |  | Input | The attribute that will be retrieved by this function. See cublasLtEmulationDescAttributes_t. |
| buf |  | Output | Memory address containing the attribute value retrieved by this function. |
| sizeInBytes |  | Input | Size of buf buffer (in bytes) for verification. |
| sizeWritten |  | Output | Valid only when the return value is CUBLAS_STATUS_SUCCESS.
If sizeInBytes is non-zero: then sizeWritten is the number of bytes actually written;
If sizeInBytes is 0: then sizeWritten is the number of bytes needed to write full contents. |


**Returns**:


| Return Value | Description |
| --- | --- |
| CUBLAS_STATUS_INVALID_VALUE | If sizeInBytes is zero and sizeWritten is NULL, or

if sizeInBytes is non-zero and buf is NULL, or
if sizeInBytes doesn’t match size of internal storage for the selected attribute |
| CUBLAS_STATUS_SUCCESS | If attribute’s value was successfully written to user memory. |








```c++
cublasStatus_t
      cublasLtCreate(cublasLtHandle_t *lighthandle)
```

此函数用于初始化 cuBLASLt 库并创建一个指向保存 cuBLASLt 库上下文的不透明结构体的句柄。它会在主机和设备上分配轻量级硬件资源，并且必须在调用任何其他 cuBLASLt 库函数之前调用。

cuBLASLt 库上下文与当前 CUDA 设备绑定。若要在多个设备上使用该库，必须为每个设备创建一个 cuBLASLt 句柄。此外，在使用与某个设备绑定的句柄调用 cuBLASLt 函数之前，必须先将该设备设置为当前设备。

另请参阅：cuBLAS Context。

**参数：**

| 参数 | 内存 | 输入/输出 | 描述 |
| --- | --- | --- | --- |
| lightHandle |  | Output | 指向所创建的 cuBLASLt 上下文的已分配 cuBLASLt 句柄的指针。 |

**返回值：**

| 返回值 | 描述 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 分配成功完成。 |
| CUBLAS_STATUS_NOT_INITIALIZED | cuBLASLt 库未初始化。发生此情况的原因通常是：

- 未首先调用 cublasLtCreate()
- cuBLASLt 例程调用的 CUDA Runtime API 发生错误，或
- 硬件设置错误。 |
| CUBLAS_STATUS_ALLOC_FAILED | cuBLASLt 库内部的资源分配失败。这通常是由 cudaMalloc() 失败导致的。
解决方法：在调用此函数之前，尽可能释放先前分配的内存。 |
| CUBLAS_STATUS_INVALID_VALUE | lighthandle 为 NULL |

有关有效返回码的完整列表，请参阅 cublasStatus_t。

```c++
cublasStatus_t
      cublasLtDestroy(cublasLtHandle_t lightHandle)
```

此函数释放 cuBLASLt 库使用的硬件资源。此函数通常是针对特定句柄调用 cuBLASLt 库的最后一次调用。由于 cublasLtCreate() 会分配一些内部资源，而调用 cublasLtDestroy() 释放这些资源时会隐式调用 `cudaDeviceSynchronize()`，因此建议尽量减少调用这些函数的次数。

**参数**：

| 参数 | 内存 | 输入/输出 | 描述 |
| --- | --- | --- | --- |
| lightHandle |  | 输入 | 指向要销毁的 cuBLASLt 句柄的指针。 |

**返回**：

| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | cuBLASLt 上下文已成功销毁。 |
| CUBLAS_STATUS_NOT_INITIALIZED | cuBLASLt 库尚未初始化。 |
| CUBLAS_STATUS_INVALID_VALUE | lightHandle 为 NULL |

有关有效返回代码的完整列表，请参阅 cublasStatus_t。

```c++

unsigned cublasLtDisableCpuInstructionsSetMask(unsigned mask);


```

指示 cuBLASLt 库不要使用 `mask` 中标志所指定的 CPU 指令。此函数的优先级高于 `CUBLASLT_DISABLE_CPU_INSTRUCTIONS_MASK` 环境变量。

**参数：** `mask` – 通过按位 OR(|) 运算符合并的标志，用于指定不应使用的 CPU 指令。

支持的标志：

| 值 | 描述 |
| --- | --- |
| 0x1 | x86-64 AVX512 ISA。 |

**返回值：** `mask` 的前一个值。



```c++

cublasStatus_t cublasLtEmulationDescCreate(cublasLtEmulationDesc_t* emulationDesc);


```


此函数用于创建新的仿真描述符。


**参数**：


| 参数 | 内存 | 输入 / 输出 | 描述 |
| --- | --- | --- | --- |
| emulationDesc |  | Input | 指向先前创建的结构体的指针，该结构体保存由此函数查询的仿真描述符。请参阅 cublasLtEmulationDesc_t。 |


**返回值**：


| 返回值 | 描述 |
| --- | --- |
| CUBLAS_STATUS_ALLOC_FAILED | 如果无法分配内存。 |
| CUBLAS_STATUS_SUCCESS | 如果描述符创建成功。 |


有关有效返回码的完整列表，请参阅 cublasStatus_t。

```c++
cublasStatus_t cublasLtEmulationDescDestroy(cublasLtEmulationDesc_t emulationDesc);
```

此函数销毁先前创建的仿真描述符。

**参数**：

| 参数 | 内存 | 输入 / 输出 | 描述 |
| --- | --- | --- | --- |
| emulationDesc |  | 输入 | 指向先前创建的结构体的指针，该结构体持有由此函数查询的仿真描述符。参见 cublasLtEmulationDesc_t。 |

**返回值**：

| 返回值 | 描述 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 如果描述符成功销毁。 |

有关有效返回码的完整列表，请参见 cublasStatus_t。



```c++

cublasStatus_t cublasLtEmulationDescGetAttribute(
      cublasLtEmulationDesc_t emulationDesc,
      cublasLtEmulationDescAttributes_t attr,
      void *buf,
      size_t sizeInBytes,
      size_t *sizeWritten);


```


此函数返回先前创建的仿真描述符所属的查询属性的值。


**参数**：


| 参数 | 内存 | 输入 / 输出 | 描述 |
| --- | --- | --- | --- |
| emulationDesc |  | 输入 | 指向先前创建的结构体的指针，该结构体保存了此函数查询的仿真描述符。请参见 cublasLtEmulationDesc_t。 |
| attr |  | 输入 | 此函数将检索的属性。请参见 cublasLtEmulationDescAttributes_t。 |
| buf |  | 输出 | 包含此函数检索到的属性值的内存地址。 |
| sizeInBytes |  | 输入 | 用于验证的 buf 缓冲区大小（以字节为单位）。 |
| sizeWritten |  | 输出 | 仅在返回值为 CUBLAS_STATUS_SUCCESS 时有效。
如果 sizeInBytes 非零：则 sizeWritten 为实际写入的字节数；
如果 sizeInBytes 为零：则 sizeWritten 为写入完整内容所需的字节数。 |


**返回值**：


| 返回值 | 描述 |
| --- | --- |
| CUBLAS_STATUS_INVALID_VALUE | 如果 sizeInBytes 为零且 sizeWritten 为 NULL，或

如果 sizeInBytes 非零且 buf 为 NULL，或
如果 sizeInBytes 与所选属性的内部存储大小不匹配 |
| CUBLAS_STATUS_SUCCESS | 如果属性值已成功写入用户内存。 |

```c++
cublasStatus_t cublasLtEmulationDescInit(cublasLtEmulationDesc_t emulationDesc);
```

此函数用于初始化一个先前分配的模拟描述符。

**参数**：

| 参数 | 内存 | 输入/输出 | 描述 |
| --- | --- | --- | --- |
| emulationDesc |  | 输入 | 指向先前创建的结构体的指针，该结构体保存由此函数查询的模拟描述符。参见 cublasLtEmulationDesc_t。 |

**返回值**：

| 返回值 | 描述 |
| --- | --- |
| CUBLAS_STATUS_ALLOC_FAILED | 如果预分配的空间大小不足。 |
| CUBLAS_STATUS_SUCCESS | 如果描述符创建成功。 |

有关有效的返回代码完整列表，请参见 cublasStatus_t。

```c++

cublasStatus_t cublasLtEmulationDescSetAttribute(
      cublasLtEmulationDesc_t emulationDesc,
      cublasLtEmulationDescAttributes_t attr,
      const void *buf,
      size_t sizeInBytes);


```

此函数用于设置先前创建的仿真描述符的指定属性值。

**参数**：

| 参数 | 内存 | 输入 / 输出 | 描述 |
| --- | --- | --- | --- |
| emulationDesc |  | 输入 | 指向先前创建的结构体的指针，该结构体保存由此函数查询的仿真描述符。参见 cublasLtEmulationDesc_t。 |
| attr |  | 输入 | 将由此函数设置的属性。参见 cublasLtEmulationDescAttributes_t。 |
| buf |  | 输入 | 应设置为指定属性的值。 |
| sizeInBytes |  | 输入 | buf 缓冲区的大小（以字节为单位），用于验证。 |

**返回值**：

| 返回值 | 描述 |
| --- | --- |
| CUBLAS_STATUS_INVALID_VALUE | 如果 buf 为 NULL 或 sizeInBytes 与所选属性的内部存储大小不匹配。 |
| CUBLAS_STATUS_SUCCESS | 如果属性设置成功。 |

有关有效的返回码完整列表，请参见 cublasStatus_t。

```c++
size_t cublasLtGetCudartVersion(void);
```

此函数返回 CUDA Runtime 库的版本号。

**参数：** 无。

**返回值：**`size_t` - CUDA Runtime 库的版本号。

```c++
cublasStatus_t cublasLtGetProperty(libraryPropertyType type, int *value);
```

此函数通过将请求的属性的值写入 `value` 参数所指向的内存位置来返回该属性的值。

**参数**：

| 参数 | 内存 | 输入/输出 | 描述 |
| --- | --- | --- | --- |
| type |  | 输入 | `libraryPropertyType` 类型的值，用于请求属性。请参阅 `libraryPropertyType_t`。 |
| value |  | 输出 | 指向主机内存位置的指针，请求的信息应写入该位置。 |

**返回**：

| 返回值 | 含义 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 请求的 `libraryPropertyType` 信息已成功写入指定地址。 |
| CUBLAS_STATUS_INVALID_VALUE | 如果 type 输入参数的值无效，或 `value` 为 NULL |

请参阅 `cublasStatus_t` 获取有效返回代码的完整列表。

```c++
const char* cublasLtGetStatusName(cublasStatus_t status);
// 返回给定状态的字符串表示
```

返回给定状态的字符串表示。

**参数：** `cublasStatus_t` - 状态。

**返回：** `const char*` - 空字符终止的字符串。

```c++

const char* cublasLtGetStatusString(cublasStatus_t status);


```

返回给定状态的描述字符串。

**参数：** cublasStatus_t - 状态。

**返回值：** `const char*` - 以 NULL 结尾的字符串。

```c++
size_t cublasLtGetVersion(void);
```

这个函数返回 cuBLASLt 库的版本号。

**参数：** 无。

**返回值：** `size_t` - cuBLASLt 库的版本号。

```c++
cublasStatus_t cublasLtGroupedMatrixLayoutCreate( cublasLtMatrixLayout_t *matLayout,
                                           cudaDataType type,
                                           int groupCount,
                                           const void* rows_array,
                                           const void* cols_array,
                                           const void* ld_array);
```

实验性：此函数通过分配存储其不透明结构所需的内存来创建分组矩阵布局描述符。

**参数**：

| 参数 | 内存 | 输入/输出 | 描述 |
| --- | --- | --- | --- |
| matLayout |  | 输出 | 指向此函数创建的矩阵布局描述符结构的指针。参见 cublasLtMatrixLayout_t。 |
| type |  | 输入 | 指定此函数创建的矩阵布局描述符数据精度的枚举值。参见 cudaDataType_t。 |
| groupCount |  | 输入 | 分组矩阵布局描述符中的组数量。 |
| rows_array |  | 输入 | 指向分组矩阵布局描述符行数组的设备指针。 |
| cols_array |  | 输入 | 指向分组矩阵布局描述符列数组的设备指针。 |
| ld_array |  | 输入 | 指向分组矩阵布局描述符主维（leading dimension）数组的设备指针。 |

**返回**：

| 返回值 | 描述 |
| --- | --- |
| CUBLAS_STATUS_ALLOC_FAILED | 如果无法分配内存。 |
| CUBLAS_STATUS_SUCCESS | 如果描述符创建成功。 |

有关有效返回码的完整列表，请参见 cublasStatus_t。

```c++

cublasStatus_t cublasLtGroupedMatrixLayoutInit( cublasLtMatrixLayout_t matLayout,
                                         cudaDataType type,
                                         int groupCount,
                                         const void* rows_array,
                                         const void* cols_array,
                                         const void* ld_array);


```

实验性：此函数初始化先前已分配的分组合矩阵布局描述符。

**参数**：

| 参数 | 内存 | 输入/输出 | 描述 |
| --- | --- | --- | --- |
| matLayout |  | 输出 | 指向由此函数初始化的矩阵布局描述符结构体的指针。请参阅 cublasLtMatrixLayout_t。 |
| type |  | 输入 | 指定此函数初始化的矩阵布局描述符数据精度的枚举值。请参阅 cudaDataType_t。 |
| groupCount |  | 输入 | 分组合矩阵布局描述符中的组数。 |
| rows_array |  | 输入 | 指向分组合矩阵布局描述符行数组的设备指针。 |
| cols_array |  | 输入 | 指向分组合矩阵布局描述符列数组的设备指针。 |
| ld_array |  | 输入 | 指向分组合矩阵布局描述符主维数组的设备指针。 |

**返回值**：

| 返回值 | 描述 |
| --- | --- |
| CUBLAS_STATUS_ALLOC_FAILED | 如果无法分配内存。 |
| CUBLAS_STATUS_SUCCESS | 如果描述符创建成功。 |

请参阅 cublasStatus_t 以获取有效返回代码的完整列表。

```c++
cublasStatus_t cublasLtHeuristicsCacheGetCapacity(size_t* capacity);
```

返回启发式缓存容量。

**参数：**

| 参数 | 描述 |
| --- | --- |
| capacity | 返回容量值的指针。 |

**返回值：**

| 返回值 | 描述 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 容量已成功写入。 |
| CUBLAS_STATUS_INVALID_VALUE | 容量已成功设置。 |

```c++
cublasStatus_t cublasLtHeuristicsCacheSetCapacity(size_t capacity);
```

设置启发式缓存的容量。将容量设置为0以禁用启发式缓存。

此函数的优先级高于 `CUBLASLT_HEURISTICS_CACHE_CAPACITY` 环境变量。

**参数：**

| 参数 | 描述 |
| --- | --- |
| capacity | 期望的启发式缓存容量。 |

**返回值：**

| 返回值 | 描述 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 容量设置成功。 |

```c++

cublasStatus_t cublasLtLoggerForceDisable();


```

实验性：此函数在整个运行期间禁用日志记录。

**返回值**：

| 返回值 | 说明 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 如果日志记录已成功禁用。 |

有关有效返回码的完整列表，请参见 cublasStatus_t。

```c++
cublasStatus_t cublasLtLoggerOpenFile(const char* logFile);
```

实验性：此函数打开并设置给定路径下的日志输出文件。

**参数**：

| 参数 | 内存 | 输入/输出 | 描述 |
| --- | --- | --- | --- |
| logFile |  | 输入 | 日志输出文件的路径。 |

**返回值**：

| 返回值 | 描述 |
| --- |
| CUBLAS_STATUS_SUCCESS | 日志文件已成功打开。 |

有关有效返回码的完整列表，请参阅 cublasStatus_t。



```c++

cublasStatus_t cublasLtLoggerSetFile(FILE* file);


```


Experimental: This function sets the logging output file. Note: once registered using this function call, the provided file handle must not be closed unless the function is called again to switch to a different file handle.


**Parameters**:


| Parameter | Memory | Input / Output | Description |
| --- | --- | --- | --- |
| file |  | Input | Pointer to an open file. File should have write permission. |


**Returns**:


| Return Value | Description |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | If logging file was successfully set. |


See cublasStatus_t for a complete list of valid return codes.




```c++
cublasStatus_t cublasLtLoggerSetLevel(int level);
```

实验性：此函数用于设置日志级别的值。

**参数**：

| 参数 | 内存 | 输入/输出 | 描述 |
| --- | --- | --- | --- |
| level |  | 输入 | 日志级别的值。参见 cuBLASLt 日志记录。 |

**返回值**：

| 返回值 | 描述 |
| --- | --- |
| CUBLAS_STATUS_INVALID_VALUE | 如果该值不是有效的日志级别。参见 cuBLASLt 日志记录。 |
| CUBLAS_STATUS_SUCCESS | 如果日志级别设置成功。 |

有关有效返回代码的完整列表，请参见 cublasStatus_t。

```c++

cublasStatus_t cublasLtLoggerSetMask(int mask);

```

试验性：此函数设置日志掩码的值。

**参数**：

| 参数 | 内存 | 输入/输出 | 描述 |
| --- | --- | --- | --- |
| mask |  | 输入 | 日志掩码的值。请参阅 cuBLASLt 日志记录。 |

**返回值**：

| 返回值 | 描述 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 如果日志掩码已成功设置。 |

有关有效的返回代码的完整列表，请参阅 cublasStatus_t。



```c++

cublasStatus_t cublasLtMatmul(
      cublasLtHandle_t               lightHandle,
      cublasLtMatmulDesc_t           computeDesc,
      const void                    *alpha,
      const void                    *A,
      cublasLtMatrixLayout_t         Adesc,
      const void                    *B,
      cublasLtMatrixLayout_t         Bdesc,
      const void                    *beta,
      const void                    *C,
      cublasLtMatrixLayout_t         Cdesc,
      void                          *D,
      cublasLtMatrixLayout_t         Ddesc,
      const cublasLtMatmulAlgo_t    *algo,
      void                          *workspace,
      size_t                         workspaceSizeInBytes,
      cudaStream_t                   stream);


```


This function computes the matrix multiplication of matrices A and B to produce the output matrix D, according to the following operation:


`D = alpha*(A*B) + beta*(C),`


where `A`, `B`, and `C` are input matrices, and `alpha` and `beta` are input scalars.


> **Note**

Note
This function supports both in-place matrix multiplication (C == D and Cdesc == Ddesc) and out-of-place matrix multiplication (C != D, both matrices must have the same data type, number of rows, number of columns, batch size, and memory order). In the out-of-place case, the leading dimension of C can be different from the leading dimension of D. Specifically the leading dimension of C can be 0 to achieve row or column broadcast. If Cdesc is omitted, this function assumes it to be equal to Ddesc.


The `workspace` pointer must be aligned to at least a multiple of 256 bytes.
The recommendations on `workspaceSizeInBytes` are the same as mentioned in the cublasSetWorkspace() section.


**Datatypes Supported:**


cublasLtMatmul() supports the following computeType, scaleType, Atype/Btype, and Ctype. Footnotes can be found at the end of this section.


| computeType | scaleType | Atype/Btype | Ctype | Bias Type 6 |
| --- | --- | --- | --- | --- |
| CUBLAS_COMPUTE_16F or
CUBLAS_COMPUTE_16F_PEDANTIC | CUDA_R_16F | CUDA_R_16F | CUDA_R_16F | CUDA_R_16F 6 |
| CUBLAS_COMPUTE_32I or
CUBLAS_COMPUTE_32I_PEDANTIC | CUDA_R_32I | CUDA_R_8I | CUDA_R_32I | Epilogue is not supported. |
| CUDA_R_32F | CUDA_R_8I | CUDA_R_8I | Epilogue is not supported. |
| CUBLAS_COMPUTE_32F or
CUBLAS_COMPUTE_32F_PEDANTIC | CUDA_R_32F | CUDA_R_16BF | CUDA_R_16BF | CUDA_R_16BF 6 |
| CUDA_R_16F | CUDA_R_16F | CUDA_R_16F 6 |
| CUDA_R_8I | CUDA_R_32F | Epilogue is not supported. |
| CUDA_R_16BF | CUDA_R_32F | CUDA_R_32F 6 |
| CUDA_R_16F | CUDA_R_32F | CUDA_R_32F 6 |
| CUDA_R_32F | CUDA_R_32F | CUDA_R_32F 6 |
| CUDA_C_32F 7 | CUDA_C_8I 7 | CUDA_C_32F 7 | Epilogue is not supported. |
| CUDA_C_32F 7 | CUDA_C_32F 7 |
| CUBLAS_COMPUTE_32F_FAST_16F or
CUBLAS_COMPUTE_32F_FAST_16BF or
CUBLAS_COMPUTE_32F_FAST_TF32 or
CUBLAS_COMPUTE_32F_EMULATED_16BFX9 | CUDA_R_32F | CUDA_R_32F | CUDA_R_32F | CUDA_R_32F 6 |
| CUDA_C_32F 7 | CUDA_C_32F 7 | CUDA_C_32F 7 | Epilogue is not supported. |
| CUBLAS_COMPUTE_64F or
CUBLAS_COMPUTE_64F_PEDANTIC or
CUBLAS_COMPUTE_64F_EMULATED_FIXEDPOINT | CUDA_R_64F | CUDA_R_64F | CUDA_R_64F | CUDA_R_64F 6 |
| CUDA_C_64F 7 | CUDA_C_64F 7 | CUDA_C_64F 7 | Epilogue is not supported. |


To use IMMA kernels, one of the following sets of requirements, with the first being the preferred one, must be met:


1. Using a regular data ordering:

All matrix pointers must be 4-byte aligned. For even better performance, this condition should hold with 16 instead of 4.
Leading dimensions of matrices A, B, C must be multiples of 4.
Only the “TN” format is supported - A must be transposed and B non-transposed.
Pointer mode can be CUBLASLT_POINTER_MODE_HOST, CUBLASLT_POINTER_MODE_DEVICE or CUBLASLT_POINTER_MODE_ALPHA_DEVICE_VECTOR_BETA_HOST. With the latter mode, the kernels support the CUBLASLT_MATMUL_DESC_ALPHA_VECTOR_BATCH_STRIDE attribute.
Dimensions m and k must be multiples of 4.
2. Using the IMMA-specific data ordering on Ampere (compute capability 8.0) or Turing (compute capability 7.5) (but not Hopper, compute capability 9.0, or later) architecture - CUBLASLT_ORDER_COL32` for matrices A, C, D, and CUBLASLT_ORDER_COL4_4R2_8C (on Turing or Ampere architecture) or CUBLASLT_ORDER_COL32_2R_4R4 (on Ampere architecture) for matrix B:

Leading dimensions of matrices A, B, C must fulfill conditions specific to the memory ordering (see cublasLtOrder_t).
Matmul descriptor must specify CUBLAS_OP_T on matrix B and CUBLAS_OP_N (default) on matrix A and C.
If scaleType CUDA_R_32I is used, the only supported values for alpha and beta are 0 or 1.
Pointer mode can be CUBLASLT_POINTER_MODE_HOST, CUBLASLT_POINTER_MODE_DEVICE, CUBLASLT_POINTER_MODE_DEVICE_VECTOR or CUBLASLT_POINTER_MODE_ALPHA_DEVICE_VECTOR_BETA_ZERO. These kernels do not support CUBLASLT_MATMUL_DESC_ALPHA_VECTOR_BATCH_STRIDE.
Only the “NT” format is supported - A must be non-transposed and B transposed.


| computeType | scaleType | Atype/Btype | Ctype | Bias Type |
| --- | --- | --- | --- | --- |
| CUBLAS_COMPUTE_32I or
CUBLAS_COMPUTE_32I_PEDANTIC | CUDA_R_32I | CUDA_R_8I | CUDA_R_32I | Non-default epilogue not supported. |
| CUDA_R_32F | CUDA_R_8I | CUDA_R_8I | CUDA_R_32F |


To use tensor- or block-scaled FP8 kernels, the following set of requirements must be satisfied:


- All matrix dimensions must meet the optimal requirements listed in Tensor Core Usage (i.e. pointers and matrix dimension must support 16-byte alignment).
- Scaling mode must meet the restrictions noted in the Scaling Mode Support Overview table.
- A must be transposed and B non-transposed (The “TN” format) on Ada (compute capability 8.9), Hopper (compute capability 9.0), and Blackwell GeForce (compute capability 12.x) GPUs.
- The compute type must be CUBLAS_COMPUTE_32F.
- The scale type must be CUDA_R_32F.


See the table below when using FP8 kernels:


| AType | BType | CType | DType | Bias Type |
| --- | --- | --- | --- | --- |
| CUDA_R_8F_E4M3 | CUDA_R_8F_E4M3 | CUDA_R_16BF | CUDA_R_16BF | CUDA_R_16BF 6 |
| CUDA_R_8F_E4M3 8 | CUDA_R_16BF 6 |
| CUDA_R_16F | CUDA_R_16F | CUDA_R_16F 6 |
| CUDA_R_8F_E4M3 8 | CUDA_R_16F 6 |
| CUDA_R_32F | CUDA_R_32F | CUDA_R_16BF 6 |
| CUDA_R_8F_E5M2 | CUDA_R_16BF | CUDA_R_16BF | CUDA_R_16BF 6 |
| CUDA_R_8F_E4M3 8 | CUDA_R_16BF 6 |
| CUDA_R_8F_E5M2 8 | CUDA_R_16BF 6 |
| CUDA_R_16F | CUDA_R_16F | CUDA_R_16F 6 |
| CUDA_R_8F_E4M3 8 | CUDA_R_16F 6 |
| CUDA_R_8F_E5M2 8 | CUDA_R_16F 6 |
| CUDA_R_32F | CUDA_R_32F | CUDA_R_16BF 6 |
| CUDA_R_8F_E5M2 | CUDA_R_8F_E4M3 | CUDA_R_16BF | CUDA_R_16BF | CUDA_R_16BF 6 |
| CUDA_R_8F_E4M3 8 | CUDA_R_16BF 6 |
| CUDA_R_8F_E5M2 8 | CUDA_R_16BF 6 |
| CUDA_R_16F | CUDA_R_16F | CUDA_R_16F 6 |
| CUDA_R_8F_E4M3 8 | CUDA_R_16F 6 |
| CUDA_R_8F_E5M2 8 | CUDA_R_16F 6 |
| CUDA_R_32F | CUDA_R_32F | CUDA_R_16BF 6 |


To use block-scaled FP4 kernels, the following set of requirements must be satisfied:


- All matrix dimensions must meet the optimal requirements listed in Tensor Core Usage (i.e. pointers and matrix dimension must support 16-byte alignment).
- Scaling mode must be CUBLASLT_MATMUL_MATRIX_SCALE_VEC16_UE4M3
- A must be transposed and B non-transposed (The “TN” format)
- The compute type must be CUBLAS_COMPUTE_32F.
- The scale type must be CUDA_R_32F.


| AType | BType | CType | DType | Bias Type |
| --- | --- | --- | --- | --- |
| CUDA_R_4F_E2M1 | CUDA_R_4F_E2M1 | CUDA_R_16BF | CUDA_R_16BF | CUDA_R_16BF 6 |
| CUDA_R_4F_E2M1 | CUDA_R_16BF 6 |
| CUDA_R_16F | CUDA_R_16F | CUDA_R_16F 6 |
| CUDA_R_4F_E2M1 | CUDA_R_16F 6 |
| CUDA_R_32F | CUDA_R_32F | CUDA_R_16BF 6 |


When A,B,C,D are planar-complex matrices (`CUBLASLT_MATRIX_LAYOUT_PLANE_OFFSET != 0`, see cublasLtMatrixLayoutAttribute_t) to make use of mixed precision tensor core acceleration, the following set of requirements must be satisfied:


| computeType | scaleType | Atype/Btype | Ctype |
| --- | --- | --- | --- |
| CUBLAS_COMPUTE_32F | CUDA_C_32F | CUDA_C_16F 7 | CUDA_C_16F 7 |
| CUDA_C_32F 7 |
| CUDA_C_16BF 7 | CUDA_C_16BF 7 |
| CUDA_C_32F 7 |


Experimental: To use cublasLtMatmul()  with grouped matrices, the following set of requirements must be satisfied:


- All matrix dimensions must meet the optimal requirements listed in Tensor Core Usage (i.e. pointers and matrix dimension must support 16-byte alignment).
- GPU with one of the following compute capabilities: 9.0, 10.x, 11.0.
- The batch mode of all matrices must be CUBLASLT_BATCH_MODE_GROUPED.
- The order type of all matrices must be CUBLASLT_ORDER_COL.
- The pointer mode must be CUBLASLT_POINTER_MODE_HOST or CUBLASLT_POINTER_MODE_DEVICE.
- The scale mode of matrices C  and D must be CUBLASLT_MATMUL_MATRIX_SCALE_SCALAR_32F.
- On GPUs with compute capability 9.0:



The scale mode of matrices A, B must be CUBLASLT_MATMUL_MATRIX_SCALE_SCALAR_32F, CUBLASLT_MATMUL_MATRIX_SCALE_VEC128_32F, or CUBLASLT_MATMUL_MATRIX_SCALE_BLK128x128_32F (for FP8 tensors)
The epilogue must be CUBLASLT_EPILOGUE_DEFAULT
The attributes CUBLASLT_MATMUL_DESC_ALPHA_BATCH_STRIDE and CUBLASLT_MATMUL_DESC_BETA_BATCH_STRIDE must be 0
- On GPUs with compute capability 10.x and 11.0:



The scale mode of matrices A, B must be CUBLASLT_MATMUL_MATRIX_SCALE_SCALAR_32F, CUBLASLT_MATMUL_MATRIX_SCALE_VEC32_UE8M0, CUBLASLT_MATMUL_MATRIX_SCALE_PER_BATCH_SCALAR_32F (for FP8 tensors), or CUBLASLT_MATMUL_MATRIX_SCALE_VEC16_UE4M3 (for FP4 tensors)
The epilogue must be CUBLASLT_EPILOGUE_DEFAULT or CUBLASLT_EPILOGUE_BIAS


| AType | BType | CType | DType | Bias Type |
| --- | --- | --- | --- | --- |
| CUDA_R_8F_E4M3 | CUDA_R_8F_E4M3 | CUDA_R_16BF | CUDA_R_16BF | CUDA_R_16BF 6 |
| CUDA_R_16F | CUDA_R_16F | CUDA_R_16F 6 |
| CUDA_R_32F | CUDA_R_32F | CUDA_R_16BF 6 |
| CUDA_R_8F_E5M2 | CUDA_R_16BF | CUDA_R_16BF | CUDA_R_16BF 6 |
| CUDA_R_16F | CUDA_R_16F | CUDA_R_16F 6 |
| CUDA_R_32F | CUDA_R_32F | CUDA_R_16BF 6 |
| CUDA_R_8F_E5M2 | CUDA_R_8F_E4M3 | CUDA_R_16BF | CUDA_R_16BF | CUDA_R_16BF 6 |
| CUDA_R_16F | CUDA_R_16F | CUDA_R_16F 6 |
| CUDA_R_32F | CUDA_R_32F | CUDA_R_16BF 6 |
| CUDA_R_16BF | CUDA_R_16BF | CUDA_R_16BF | CUDA_R_16BF | CUDA_R_16BF 6 |
| CUDA_R_32F | CUDA_R_32F | CUDA_R_16BF 6 |
| CUDA_R_16F | CUDA_R_16F | CUDA_R_16F | CUDA_R_16F | CUDA_R_16F 6 |
| CUDA_R_32F | CUDA_R_32F | CUDA_R_16BF 6 |


> **Note**

Note
Because the shape information for the matrices is only available on the GPU (see CUBLASLT_GROUPED_MATRIX_LAYOUT_ROWS_ARRAY, CUBLASLT_GROUPED_MATRIX_LAYOUT_COLS_ARRAY, and CUBLASLT_GROUPED_MATRIX_LAYOUT_LD_ARRAY), the arguments validation is very limited. So it is possible that invalid arguments are not detected which will result in an undefined behavior.


**NOTES:**


**6(1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27,28,29,30,31,32,33,34,35,36,37,38,39,40,41,42,43,44,45,46)**
: Epilogue modes that combine ReLU, dReLu, GELU, or dGELU with Bias (see CUBLASLT_MATMUL_DESC_EPILOGUE in cublasLtMatmulDescAttributes_t) are not supported when D matrix memory order is defined as CUBLASLT_ORDER_ROW. For best performance when using the bias vector, specify zero beta and set pointer mode to CUBLASLT_POINTER_MODE_HOST.

**7(1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17)**
: Use of CUBLAS_ORDER_ROW together with CUBLAS_OP_C (Hermitian operator) is not supported unless all of A, B, C, and D matrices use the CUBLAS_ORDER_ROW ordering.

**8(1,2,3,4,5,6,7,8,9,10)**
: FP8 DType is not supported when scaling modes are one of CUBLASLT_MATMUL_MATRIX_SCALE_OUTER_VEC_32F, CUBLASLT_MATMUL_MATRIX_SCALE_VEC128_32F, and CUBLASLT_MATMUL_MATRIX_SCALE_BLK128x128_32F.



**Parameters:**


| Parameter | Memory | Input / Output | Description |
| --- | --- | --- | --- |
| lightHandle |  | Input | Pointer to the allocated cuBLASLt handle for the cuBLASLt context. See cublasLtHandle_t. |
| computeDesc |  | Input | Handle to a previously created matrix multiplication descriptor of type cublasLtMatmulDesc_t. |
| alpha, beta | Device or host | Input | Pointers to the scalars used in the multiplication. |
| A, B, and C | Device | Input | Pointers to the GPU memory associated with the corresponding descriptors Adesc, Bdesc and Cdesc. |
| Adesc, Bdesc and Cdesc |  | Input | Handles to the previous created descriptors of the type cublasLtMatrixLayout_t. |
| D | Device | Output | Pointer to the GPU memory associated with the descriptor Ddesc. |
| Ddesc |  | Input | Handle to the previous created descriptor of the type cublasLtMatrixLayout_t. |
| algo |  | Input | Handle for matrix multiplication algorithm to be used. See cublasLtMatmulAlgo_t. When NULL, an implicit heuristics query with default search preferences will be performed to determine actual algorithm to use. |
| workspace | Device |  | Pointer to the workspace buffer allocated in the GPU memory. Must be 256B aligned (i.e. lowest 8 bits of address must be 0). |
| workspaceSizeInBytes |  | Input | Size of the workspace. |
| stream | Host | Input | The CUDA stream where all the GPU work will be submitted. |


**Returns:**


| Return Value | Description |
| --- | --- |
| CUBLAS_STATUS_NOT_INITIALIZED | If cuBLASLt handle has not been initialized. |
| CUBLAS_STATUS_INVALID_VALUE | If the parameters are unexpectedly NULL, in conflict or in an impossible configuration. For example, when workspaceSizeInBytes is less than workspace required by the configured algo. |
| CUBLAS_STATUS_NOT_SUPPORTED | If the current implementation on the selected device doesn’t support the configured operation. |
| CUBLAS_STATUS_ARCH_MISMATCH | If the configured operation cannot be run using the selected device. |
| CUBLAS_STATUS_EXECUTION_FAILED | If CUDA reported an execution error from the device. |
| CUBLAS_STATUS_SUCCESS | If the operation completed successfully. |


See cublasStatus_t for a complete list of valid return codes.




```c++

cublasStatus_t cublasLtMatmulAlgoCapGetAttribute(
      const cublasLtMatmulAlgo_t *algo,
      cublasLtMatmulAlgoCapAttributes_t attr,
      void *buf,
      size_t sizeInBytes,
      size_t *sizeWritten);


```

此函数返回已初始化的 `cublasLtMatmulAlgo_t` 描述符结构的查询能力属性的值。能力属性值从枚举类型 `cublasLtMatmulAlgoCapAttributes_t` 中获取。

例如，获取支持的磁贴ID列表：

```c++

cublasLtMatmulTile_t tiles[CUBLASLT_MATMUL_TILE_END];
size_t num_tiles, size_written;
if (cublasLtMatmulAlgoCapGetAttribute(algo, CUBLASLT_ALGO_CAP_TILE_IDS, tiles, sizeof(tiles), &size_written) == CUBLAS_STATUS_SUCCESS) {
  num_tiles = size_written / sizeof(tiles[0]);}


```

**参数**：

| 参数 | 内存 | 输入/输出 | 描述 |
| --- | --- | --- | --- |
| algo |  | 输入 | 指向先前创建的不透明结构的指针，该结构保存矩阵乘法算法描述符。请参阅 `cublasLtMatmulAlgo_t`。 |
| attr |  | 输入 | 将由此函数检索其值的能力属性。请参阅 `cublasLtMatmulAlgoCapAttributes_t`。 |
| buf |  | 输出 | 此函数返回的属性值。 |
| sizeInBytes |  | 输入 | buf 缓冲区的大小（以字节为单位），用于验证。 |
| sizeWritten |  | 输出 | 仅在返回值为 `CUBLAS_STATUS_SUCCESS` 时有效。如果 `sizeInBytes` 非零：则 `sizeWritten` 是实际写入的字节数；如果 `sizeInBytes` 为零：则 `sizeWritten` 是写入完整内容所需的字节数。 |

**返回值**：

| 返回值 | 描述 |
| --- | --- |
| CUBLAS_STATUS_INVALID_VALUE | 如果 `sizeInBytes` 为零且 `sizeWritten` 为 NULL，或如果 `sizeInBytes` 非零且 `buf` 为 NULL，或如果 `sizeInBytes` 与所选属性的内部存储大小不匹配 |
| CUBLAS_STATUS_SUCCESS | 如果属性值已成功写入用户内存。 |

有关有效返回码的完整列表，请参阅 `cublasStatus_t`。

```c++

cublasStatus_t cublasLtMatmulAlgoCheck(
      cublasLtHandle_t lightHandle,
      cublasLtMatmulDesc_t operationDesc,
      cublasLtMatrixLayout_t Adesc,
      cublasLtMatrixLayout_t Bdesc,
      cublasLtMatrixLayout_t Cdesc,
      cublasLtMatrixLayout_t Ddesc,
      const cublasLtMatmulAlgo_t *algo,
      cublasLtMatmulHeuristicResult_t *result);


```

此函数对矩阵乘法操作 `cublasLtMatmul()` 函数的矩阵乘法算法描述符进行正确性检查，输入矩阵为 A、B 和 C，输出矩阵为 D。它检查该描述符在当前设备上是否受支持，并返回包含所需工作区大小和计算波计数的结果。

> **注意**
>
> `CUBLAS_STATUS_SUCCESS` 并不能完全保证算法能够运行。例如，如果缓冲区未正确对齐，算法将失败。但是，如果 `cublasLtMatmulAlgoCheck()` 失败，算法将不会运行。

**参数**：

| 参数 | 内存 | 输入/输出 | 描述 |
| --- | --- | --- | --- |
| lightHandle |  | 输入 | 指向为 cuBLASLt 上下文分配的 cuBLASLt 句柄的指针。请参见 `cublasLtHandle_t`。 |
| operationDesc |  | 输入 | 指向先前创建的矩阵乘法描述符（类型为 `cublasLtMatmulDesc_t`）的句柄。 |
| Adesc、Bdesc、Cdesc 和 Ddesc |  | 输入 | 指向先前创建的矩阵布局描述符（类型为 `cublasLtMatrixLayout_t`）的句柄。 |
| algo |  | 输入 | 指定应使用哪种矩阵乘法算法的描述符。请参见 `cublasLtMatmulAlgo_t`。可以指向 `result->algo`。 |
| result |  | 输出 | 指向此函数返回结果结构的指针。结果包含所需的工作区大小和计算的波计数。`algo` 字段不会被更新。请参见 `cublasLtMatmulHeuristicResult_t`。 |

**返回**：

| 返回值 | 描述 |
| --- | --- |
| `CUBLAS_STATUS_INVALID_VALUE` | 如果矩阵布局描述符或操作描述符与算法描述符不匹配。 |
| `CUBLAS_STATUS_NOT_SUPPORTED` | 如果当前设备上不支持该算法配置或数据类型组合。 |
| `CUBLAS_STATUS_ARCH_MISMATCH` | 如果所选设备无法运行该算法配置。 |
| `CUBLAS_STATUS_SUCCESS` | 如果检查成功。 |

有关完整的有效返回代码列表，请参见 `cublasStatus_t`。



```c++

cublasStatus_t cublasLtMatmulAlgoConfigGetAttribute(
      const cublasLtMatmulAlgo_t *algo,
      cublasLtMatmulAlgoConfigAttributes_t attr,
      void *buf,
      size_t sizeInBytes,
      size_t *sizeWritten);


```


此函数返回针对已初始化的 `cublasLtMatmulAlgo_t` 描述符所查询的配置属性的值。配置属性值从枚举类型 `cublasLtMatmulAlgoConfigAttributes_t` 中检索。


**参数**：


| 参数 | 内存 | 输入/输出 | 描述 |
| --- | --- | --- | --- |
| algo |  | 输入 | 指向先前创建的不透明结构的指针，该结构保存矩阵乘法算法描述符。请参见 `cublasLtMatmulAlgo_t`。 |
| attr |  | 输入 | 此函数将检索其值的配置属性。请参见 `cublasLtMatmulAlgoConfigAttributes_t`。 |
| buf |  | 输出 | 此函数返回的属性值。 |
| sizeInBytes |  | 输入 | buf 缓冲区的大小（以字节为单位），用于验证。 |
| sizeWritten |  | 输出 | 仅在返回值为 `CUBLAS_STATUS_SUCCESS` 时有效。如果 sizeInBytes 非零：则 sizeWritten 为实际写入的字节数；如果 sizeInBytes 为零：则 sizeWritten 为写入完整内容所需的字节数。 |


**返回值**：


| 返回值 | 描述 |
| --- | --- |
| `CUBLAS_STATUS_INVALID_VALUE` | 如果 sizeInBytes 为零且 sizeWritten 为 NULL，或如果 sizeInBytes 非零且 buf 为 NULL，或如果 sizeInBytes 与所选属性的内部存储大小不匹配 |
| `CUBLAS_STATUS_SUCCESS` | 如果属性值已成功写入用户内存。 |


请参阅 `cublasStatus_t` 以获取有效返回代码的完整列表。

```c++

cublasStatus_t cublasLtMatmulAlgoConfigSetAttribute(
      cublasLtMatmulAlgo_t *algo,
      cublasLtMatmulAlgoConfigAttributes_t attr,
      const void *buf,
      size_t sizeInBytes);


```

此函数用于设置已初始化的 `cublasLtMatmulAlgo_t` 描述符的指定配置属性的值。配置属性是 `cublasLtMatmulAlgoConfigAttributes_t` 类型的枚举值。

**参数**：

| 参数 | 内存 | 输入 / 输出 | 描述 |
| --- | --- | --- | --- |
| algo |  | 输入 | 指向先前创建的不透明结构的指针，该结构保存矩阵乘法算法描述符。请参阅 `cublasLtMatmulAlgo_t`。 |
| attr |  | 输入 | 将由此函数设置其值的配置属性。请参阅 `cublasLtMatmulAlgoConfigAttributes_t`。 |
| buf |  | 输入 | 要设置给配置属性的值。 |
| sizeInBytes |  | 输入 | buf 缓冲区的大小（以字节为单位），用于验证。 |

**返回值**：

| 返回值 | 描述 |
| --- | --- |
| CUBLAS_STATUS_INVALID_VALUE | 如果 buf 为 NULL 或 sizeInBytes 与所选属性的内部存储大小不匹配。 |
| CUBLAS_STATUS_SUCCESS | 如果属性设置成功。 |

有关有效的返回代码完整列表，请参阅 `cublasStatus_t`。



```c++

cublasStatus_t cublasLtMatmulAlgoGetHeuristic(
      cublasLtHandle_t lightHandle,
      cublasLtMatmulDesc_t operationDesc,
      cublasLtMatrixLayout_t Adesc,
      cublasLtMatrixLayout_t Bdesc,
      cublasLtMatrixLayout_t Cdesc,
      cublasLtMatrixLayout_t Ddesc,
      cublasLtMatmulPreference_t preference,
      int requestedAlgoCount,
      cublasLtMatmulHeuristicResult_t heuristicResultsArray[],
      int *returnAlgoCount);


```


This function retrieves the possible algorithms for the matrix multiply operation cublasLtMatmul() function with the given input matrices A, B and C, and the output matrix D. The output is placed in `heuristicResultsArray[]` in the order of increasing estimated compute time.


**Parameters**:


| Parameter | Memory | Input / Output | Description |
| --- | --- | --- | --- |
| lightHandle |  | Input | Pointer to the allocated cuBLASLt handle for the cuBLASLt context. See cublasLtHandle_t. |
| operationDesc |  | Input | Handle to a previously created matrix multiplication descriptor of type cublasLtMatmulDesc_t. |
| Adesc, Bdesc, Cdesc, and Ddesc |  | Input | Handles to the previously created matrix layout descriptors of the type cublasLtMatrixLayout_t. |
| preference |  | Input | Pointer to the structure holding the heuristic search preferences descriptor. See cublasLtMatmulPreference_t. |
| requestedAlgoCount |  | Input | Size of the heuristicResultsArray (in elements). This is the requested maximum number of algorithms to return. |
| heuristicResultsArray[] |  | Output | Array containing the algorithm heuristics and associated runtime characteristics, returned by this function, in the order of increasing estimated compute time. |
| returnAlgoCount |  | Output | Number of algorithms returned by this function. This is the number of heuristicResultsArray elements written. |


**Returns**:


| Return Value | Description |
| --- | --- |
| CUBLAS_STATUS_INVALID_VALUE | If requestedAlgoCount is less or equal to zero. |
| CUBLAS_STATUS_NOT_SUPPORTED | If no heuristic function available for current configuration. |
| CUBLAS_STATUS_SUCCESS | If query was successful. Inspect heuristicResultsArray[0 to (returnAlgoCount -1)].state for the status of the results. |


See cublasStatus_t for a complete list of valid return codes.


> **Note**

Note
This function may load some kernels using CUDA Driver API which may fail when there is no available GPU memory. Do not allocate the entire VRAM before running cublasLtMatmulAlgoGetHeuristic().




```c++

cublasStatus_t cublasLtMatmulAlgoGetIds(
      cublasLtHandle_t lightHandle,
      cublasComputeType_t computeType,
      cudaDataType_t scaleType,
      cudaDataType_t Atype,
      cudaDataType_t Btype,
      cudaDataType_t Ctype,
      cudaDataType_t Dtype,
      int requestedAlgoCount,
      int algoIdsArray[],
      int *returnAlgoCount);


```

此函数检索对于给定输入矩阵 A、B、C 和输出矩阵 D 的数据类型，所有有效的矩阵乘法算法的 ID，这些算法可由 `cublasLtMatmul()` 函数潜在执行。

> **注意**
>
> 注意
> ID 的返回顺序不分先后。为确保最佳算法包含在列表中，请将 `requestedAlgoCount` 设置得足够大以接收完整列表。如果 `returnAlgoCount` < `requestedAlgoCount`，则列表保证是完整的。

**参数**：

| 参数 | 内存 | 输入 / 输出 | 描述 |
| --- | --- | --- | --- |
| lightHandle |  | 输入 | 指向为 cuBLASLt 上下文分配的 cuBLASLt 句柄的指针。请参见 `cublasLtHandle_t`。 |
| computeType、scaleType、Atype、Btype、Ctype 和 Dtype |  | 输入 | 计算类型、缩放因子和操作数矩阵的数据类型。请参见 `cudaDataType_t`。 |
| requestedAlgoCount |  | 输入 | 请求的算法数量。必须 > 0。 |
| algoIdsArray[] |  | 输出 | 包含此函数返回的算法 ID 的数组。 |
| returnAlgoCount |  | 输出 | 此函数实际返回的算法数量。 |

**返回值**：

| 返回值 | 描述 |
| --- | --- |
| CUBLAS_STATUS_INVALID_VALUE | 如果 requestedAlgoCount 小于或等于零。 |
| CUBLAS_STATUS_SUCCESS | 如果查询成功。检查 returnAlgoCount 以获取可用的实际 ID 数量。 |

有关有效返回代码的完整列表，请参见 `cublasStatus_t`。

```c++

cublasStatus_t cublasLtMatmulAlgoInit(
      cublasLtHandle_t lightHandle,
      cublasComputeType_t computeType,
      cudaDataType_t scaleType,
      cudaDataType_t Atype,
      cudaDataType_t Btype,
      cudaDataType_t Ctype,
      cudaDataType_t Dtype,
      int algoId,
      cublasLtMatmulAlgo_t *algo);


```

此函数为 cublasLtMatmul() 初始化矩阵乘法算法结构，针对指定的矩阵乘法算法以及输入矩阵 A、B 和 C，以及输出矩阵 D。

**参数**：

| 参数 | 内存 | 输入/输出 | 描述 |
| --- | --- | --- | --- |
| lightHandle |  | Input | 指向为 cuBLASLt 上下文分配的 cuBLASLt 句柄的指针。请参阅 cublasLtHandle_t。 |
| computeType |  | Input | 计算类型。请参阅 cublasLtMatmulDescAttributes_t 的 CUBLASLT_MATMUL_DESC_COMPUTE_TYPE。 |
| scaleType |  | Input | 缩放类型。请参阅 cublasLtMatmulDescAttributes_t 的 CUBLASLT_MATMUL_DESC_SCALE_TYPE。通常与 computeType 相同。 |
| Atype, Btype, Ctype, and Dtype |  | Input | 输入和输出矩阵的数据类型精度。请参阅 cudaDataType_t。 |
| algoId |  | Input | 指定正在初始化的算法。应为 cublasLtMatmulAlgoGetIds() 函数返回的有效 algoId。 |
| algo |  | Input | 指向要初始化的不透明结构的指针。请参阅 cublasLtMatmulAlgo_t。 |

**返回值**：

| 返回值 | 描述 |
| --- | --- |
| CUBLAS_STATUS_INVALID_VALUE | 如果 algo 为 NULL 或 algoId 超出可识别范围。 |
| CUBLAS_STATUS_NOT_SUPPORTED | 如果 algoId 对于给定的数据类型组合不支持。 |
| CUBLAS_STATUS_SUCCESS | 如果结构体已成功初始化。 |

有关有效返回码的完整列表，请参阅 cublasStatus_t。



```c++

cublasStatus_t cublasLtMatmulDescCreate( cublasLtMatmulDesc_t *matmulDesc,
                                         cublasComputeType_t computeType,
                                         cudaDataType_t scaleType);

```


此函数通过分配用于保存其不透明结构的内存来创建矩阵乘法描述符。


**参数**：


| 参数 | 内存 | 输入 / 输出 | 描述 |
| --- | --- | --- | --- |
| matmulDesc |  | 输出 | 指向由此函数创建的矩阵乘法描述符所保存结构的指针。参见 cublasLtMatmulDesc_t。 |
| computeType |  | 输入 | 枚举类型，指定此函数创建的矩阵乘法描述符的数据精度。参见 cublasComputeType_t。 |
| scaleType |  | 输入 | 枚举类型，指定此函数创建的矩阵变换描述符的数据精度。参见 cudaDataType_t。 |


**返回值**：


| 返回值 | 描述 |
| --- | --- |
| CUBLAS_STATUS_ALLOC_FAILED | 如果无法分配内存。 |
| CUBLAS_STATUS_SUCCESS | 如果描述符创建成功。 |


有关有效返回代码的完整列表，请参见 cublasStatus_t。

```c++
cublasStatus_t cublasLtMatmulDescDestroy(
      cublasLtMatmulDesc_t matmulDesc);
```

此函数销毁先前创建的矩阵乘法描述符对象。

**参数**：

| 参数 | 内存 | 输入/输出 | 描述 |
| --- | --- | --- | --- |
| matmulDesc |  | Input | 指向保存矩阵乘法描述符的结构的指针，该描述符应由此函数销毁。请参阅 cublasLtMatmulDesc_t。 |

**返回值**：

| 返回值 | 描述 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 如果操作成功。 |

有关有效返回代码的完整列表，请参阅 cublasStatus_t。

```c++
cublasStatus_t cublasLtMatmulDescGetAttribute(
      cublasLtMatmulDesc_t matmulDesc,
      cublasLtMatmulDescAttributes_t attr,
      void *buf,
      size_t sizeInBytes,
      size_t *sizeWritten);
```

此函数返回之前创建的矩阵乘法描述符的查询属性值。

**参数**：

| 参数 | 内存 | 输入/输出 | 描述 |
| --- | --- | --- | --- |
| matmulDesc |  | 输入 | 指向之前创建的结构体的指针，该结构体包含此函数查询的矩阵乘法描述符。请参阅 cublasLtMatmulDesc_t。 |
| attr |  | 输入 | 此函数将检索的属性。请参阅 cublasLtMatmulDescAttributes_t。 |
| buf |  | 输出 | 包含此函数检索到的属性值的内存地址。 |
| sizeInBytes |  | 输入 | buf 缓冲区的大小（以字节为单位），用于验证。 |
| sizeWritten |  | 输出 | 仅在返回值为 CUBLAS_STATUS_SUCCESS 时有效。如果 sizeInBytes 非零：则 sizeWritten 是实际写入的字节数；如果 sizeInBytes 为零：则 sizeWritten 是写入完整内容所需的字节数。 |

**返回值**：

| 返回值 | 描述 |
| --- | --- |
| CUBLAS_STATUS_INVALID_VALUE | 如果 sizeInBytes 为 0 且 sizeWritten 为 NULL，或 sizeInBytes 非零但 buf 为 NULL，或 sizeInBytes 与所选属性的内部存储大小不匹配 |
| CUBLAS_STATUS_SUCCESS | 如果属性值已成功写入用户内存。 |

有关有效返回代码的完整列表，请参阅 cublasStatus_t。

```c++

cublasStatus_t cublasLtMatmulDescInit( cublasLtMatmulDesc_t matmulDesc,
                                       cublasComputeType_t computeType,
                                       cudaDataType_t scaleType);


```


此函数初始化之前分配的矩阵乘法描述符。


**参数**：


| 参数 | 内存 | 输入 / 输出 | 描述 |
| --- | --- | --- | --- |
| matmulDesc |  | 输出 | 指向保存此函数初始化的矩阵乘法描述符的结构的指针。参见 cublasLtMatmulDesc_t。 |
| computeType |  | 输入 | 指定此函数初始化的矩阵乘法描述符的数据精度的枚举值。参见 cublasComputeType_t。 |
| scaleType |  | 输入 | 指定此函数初始化的矩阵变换描述符的数据精度的枚举值。参见 cudaDataType_t。 |


**返回值**：


| 返回值 | 描述 |
| --- | --- |
| CUBLAS_STATUS_ALLOC_FAILED | 如果无法分配内存。 |
| CUBLAS_STATUS_SUCCESS | 如果描述符创建成功。 |


有关有效返回码的完整列表，请参见 cublasStatus_t。



```c++

cublasStatus_t cublasLtMatmulDescSetAttribute(
      cublasLtMatmulDesc_t matmulDesc,
      cublasLtMatmulDescAttributes_t attr,
      const void *buf,
      size_t sizeInBytes);


```


此函数用于设置先前创建的矩阵乘法描述符的指定属性值。


**参数**：


| 参数 | 内存 | 输入/输出 | 描述 |
| --- | --- | --- | --- |
| matmulDesc |  | 输入 | 指向先前创建的结构体的指针，该结构体保存由此函数查询的矩阵乘法描述符。请参见 cublasLtMatmulDesc_t。 |
| attr |  | 输入 | 此函数将设置的属性。请参见 cublasLtMatmulDescAttributes_t。 |
| buf |  | 输入 | 应将指定属性设置到的值。 |
| sizeInBytes |  | 输入 | buf 缓冲区的大小（以字节为单位），用于验证。 |


**返回值**：


| 返回值 | 描述 |
| --- | --- |
| CUBLAS_STATUS_INVALID_VALUE | 如果 buf 为 NULL 或 sizeInBytes 与所选属性的内部存储大小不匹配。 |
| CUBLAS_STATUS_SUCCESS | 如果属性设置成功。 |


有关有效的返回码完整列表，请参见 cublasStatus_t。

```c++

cublasStatus_t cublasLtMatmulPreferenceCreate(
      cublasLtMatmulPreference_t *pref);


```


此函数通过分配用于保存其不透明结构的内存来创建矩阵乘法启发式搜索偏好描述符。

**参数**:


| 参数 | 内存 | 输入 / 输出 | 描述 |
| --- | --- | --- | --- |
| pref |  | 输出 | 指向由此函数创建的矩阵乘法偏好描述符结构的指针。请参阅 cublasLtMatrixLayout_t。 |


**返回值**:


| 返回值 | 描述 |
| --- | --- |
| CUBLAS_STATUS_ALLOC_FAILED | 如果无法分配内存。 |
| CUBLAS_STATUS_SUCCESS | 如果描述符创建成功。 |


请参阅 cublasStatus_t 获取有效返回码的完整列表。



```c++

cublasStatus_t cublasLtMatmulPreferenceDestroy(
      cublasLtMatmulPreference_t pref);


```


此函数用于销毁先前创建的矩阵乘法偏好描述符对象。

**参数**：


| 参数 | 内存 | 输入 / 输出 | 描述 |
| --- | --- | --- | --- |
| pref |  | 输入 | 指向保存矩阵乘法偏好描述符的结构体的指针，该描述符将由本函数销毁。请参阅 cublasLtMatmulPreference_t。 |


**返回值**：


| 返回值 | 描述 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 如果操作成功。 |


有关完整的有效返回代码列表，请参阅 cublasStatus_t。



```c++

cublasStatus_t cublasLtMatmulPreferenceGetAttribute(
      cublasLtMatmulPreference_t pref,
      cublasLtMatmulPreferenceAttributes_t attr,
      void *buf,
      size_t sizeInBytes,
      size_t *sizeWritten);


```


此函数返回先前创建的矩阵乘法启发式搜索偏好描述符中查询的属性的值。

**参数**：


| 参数 | 内存 | 输入 / 输出 | 描述 |
| --- | --- | --- | --- |
| pref |  | 输入 | 指向先前创建的结构体的指针，该结构体保存此函数查询的矩阵乘法启发式搜索偏好描述符。参见 cublasLtMatmulPreference_t。 |
| attr |  | 输入 | 此函数要查询的属性。参见 cublasLtMatmulPreferenceAttributes_t。 |
| buf |  | 输出 | 包含此函数检索的属性值的内存地址。 |
| sizeInBytes |  | 输入 | buf 缓冲区的大小（以字节为单位），用于验证。 |
| sizeWritten |  | 输出 | 仅在返回值为 CUBLAS_STATUS_SUCCESS 时有效。如果 sizeInBytes 非零：则 sizeWritten 是实际写入的字节数；如果 sizeInBytes 为零：则 sizeWritten 是写入完整内容所需的字节数。 |


**返回值**：


| 返回值 | 描述 |
| --- | --- |
| CUBLAS_STATUS_INVALID_VALUE | 如果 sizeInBytes 为零且 sizeWritten 为 NULL，或 sizeInBytes 非零且 buf 为 NULL，或 sizeInBytes 与所选属性的内部存储大小不匹配 |
| CUBLAS_STATUS_SUCCESS | 如果属性值已成功写入用户内存。 |


有关有效返回代码的完整列表，请参见 cublasStatus_t。



```c++

cublasStatus_t cublasLtMatmulPreferenceInit(
      cublasLtMatmulPreference_t pref);


```


This function initializes a matrix multiply heuristic search preferences descriptor in a previously allocated one.


**Parameters**:


| Parameter | Memory | Input / Output | Description |
| --- | --- | --- | --- |
| pref |  | Output | Pointer to the structure holding the matrix multiply preferences descriptor created by this function. See cublasLtMatrixLayout_t. |


**Returns**:


| Return Value | Description |
| --- | --- |
| CUBLAS_STATUS_ALLOC_FAILED | If memory could not be allocated. |
| CUBLAS_STATUS_SUCCESS | If the descriptor was created successfully. |


See cublasStatus_t for a complete list of valid return codes.




```c++

cublasStatus_t cublasLtMatmulPreferenceSetAttribute(
      cublasLtMatmulPreference_t pref,
      cublasLtMatmulPreferenceAttributes_t attr,
      const void *buf,
      size_t sizeInBytes);


```

此函数用于设置先前创建的矩阵乘法偏好设置描述符中指定属性的值。

**参数**：

| 参数 | 内存 | 输入 / 输出 | 描述 |
| --- | --- | --- | --- |
| pref |  | 输入 | 指向先前创建的结构体的指针，该结构体保存由此函数查询的矩阵乘法偏好设置描述符。请参阅 cublasLtMatmulPreference_t。 |
| attr |  | 输入 | 将由此函数设置的属性。请参阅 cublasLtMatmulPreferenceAttributes_t。 |
| buf |  | 输入 | 指定属性应设置到的值。 |
| sizeInBytes |  | 输入 | buf 缓冲区的大小（以字节为单位），用于验证。 |

**返回值**：

| 返回值 | 描述 |
| --- | --- |
| CUBLAS_STATUS_INVALID_VALUE | 如果 buf 为 NULL 或 sizeInBytes 与所选属性的内部存储大小不匹配。 |
| CUBLAS_STATUS_SUCCESS | 如果属性设置成功。 |

有关有效返回码的完整列表，请参阅 cublasStatus_t。



```c++

cublasStatus_t cublasLtMatrixLayoutCreate( cublasLtMatrixLayout_t *matLayout,
                                           cudaDataType type,
                                           uint64_t rows,
                                           uint64_t cols,
                                           int64_t ld);


```


此函数通过分配保存其不透明结构所需的内存来创建矩阵布局描述符。


**参数**：


| 参数 | 内存 | 输入 / 输出 | 描述 |
| --- | --- | --- | --- |
| matLayout |  | Output | 指向由此函数创建的矩阵布局描述符结构体的指针。请参见 cublasLtMatrixLayout_t。 |
| type |  | Input | 枚举类型，指定此函数创建的矩阵布局描述符的数据精度。请参见 cudaDataType_t。 |
| rows, cols |  | Input | 矩阵的行数和列数。 |
| ld |  | Input | 矩阵的主维度。在列优先布局中，这是跳转到下一列所需的元素个数。因此 ld >= m（行数）。 |


**返回值**：


| 返回值 | 描述 |
| --- | --- |
| CUBLAS_STATUS_ALLOC_FAILED | 如果无法分配内存。 |
| CUBLAS_STATUS_SUCCESS | 如果描述符创建成功。 |


有关有效返回码的完整列表，请参见 cublasStatus_t。



```c++

cublasStatus_t cublasLtMatrixLayoutDestroy(
      cublasLtMatrixLayout_t matLayout);


```


此函数销毁先前创建的矩阵布局描述符对象。

**参数**：


| 参数 | 内存 | 输入 / 输出 | 描述 |
| --- | --- | --- | --- |
| matLayout |  | Input | 指向矩阵布局描述符结构的指针，该结构由此函数销毁。请参阅 cublasLtMatrixLayout_t。 |


**返回值**：


| 返回值 | 描述 |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | 如果操作成功。 |


有关有效返回码的完整列表，请参阅 cublasStatus_t。

```c++

cublasStatus_t cublasLtMatrixLayoutGetAttribute(
      cublasLtMatrixLayout_t matLayout,
      cublasLtMatrixLayoutAttribute_t attr,
      void *buf,
      size_t sizeInBytes,
      size_t *sizeWritten);


```

此函数返回属于指定矩阵布局描述符的查询属性的值。

**参数**：

| 参数 | 内存 | 输入 / 输出 | 描述 |
| --- | --- | --- | --- |
| matLayout |  | 输入 | 指向先前创建的结构体的指针，该结构体保存由此函数查询的矩阵布局描述符。请参阅 cublasLtMatrixLayout_t。 |
| attr |  | 输入 | 要查询的属性。请参阅 cublasLtMatrixLayoutAttribute_t。 |
| buf |  | 输出 | 由此函数返回的属性值。 |
| sizeInBytes |  | 输入 | buf 缓冲区的大小（以字节为单位），用于验证。 |
| sizeWritten |  | 输出 | 仅在返回值为 CUBLAS_STATUS_SUCCESS 时有效。如果 sizeInBytes 非零：则 sizeWritten 为实际写入的字节数；如果 sizeInBytes 为零：则 sizeWritten 为写入完整内容所需的字节数。 |

**返回值**：

| 返回值 | 描述 |
| --- | --- |
| CUBLAS_STATUS_INVALID_VALUE | 如果 sizeInBytes 为零且 sizeWritten 为 NULL，或如果 sizeInBytes 非零且 buf 为 NULL，或 sizeInBytes 与所选属性的内部存储大小不匹配 |
| CUBLAS_STATUS_SUCCESS | 如果属性值已成功写入用户内存。 |

有关有效返回码的完整列表，请参阅 cublasStatus_t。



```c++

cublasStatus_t cublasLtMatrixLayoutInit( cublasLtMatrixLayout_t matLayout,
                                         cudaDataType type,
                                         uint64_t rows,
                                         uint64_t cols,
                                         int64_t ld);


```


This function initializes a matrix layout descriptor in a previously allocated one.


**Parameters**:


| Parameter | Memory | Input / Output | Description |
| --- | --- | --- | --- |
| matLayout |  | Output | Pointer to the structure holding the matrix layout descriptor initialized by this function. See cublasLtMatrixLayout_t. |
| type |  | Input | Enumerant that specifies the data precision for the matrix layout descriptor this function initializes. See cudaDataType_t. |
| rows, cols |  | Input | Number of rows and columns of the matrix. |
| ld |  | Input | The leading dimension of the matrix. In column major layout, this is the number of elements to jump to reach the next column. Thus ld >= m (number of rows). |


**Returns**:


| Return Value | Description |
| --- | --- |
| CUBLAS_STATUS_ALLOC_FAILED | If the memory could not be allocated. |
| CUBLAS_STATUS_SUCCESS | If the descriptor was created successfully. |


See cublasStatus_t for a complete list of valid return codes.






```c++

cublasStatus_t cublasLtMatrixLayoutSetAttribute(
      cublasLtMatrixLayout_t matLayout,
      cublasLtMatrixLayoutAttribute_t attr,
      const void *buf,
      size_t sizeInBytes);


```


此函数用于设置先前创建的矩阵布局描述符所属的指定属性的值。


**参数**：


| 参数 | 内存 | 输入 / 输出 | 描述 |
| --- | --- | --- | --- |
| matLayout |  | 输入 | 指向先前创建的结构体的指针，该结构体保存由此函数查询的矩阵布局描述符。请参见 cublasLtMatrixLayout_t。 |
| attr |  | 输入 | 将由此函数设置的属性。请参见 cublasLtMatrixLayoutAttribute_t。 |
| buf |  | 输入 | 指定属性应设置到的值。 |
| sizeInBytes |  | 输入 | buf 的大小，属性缓冲区的大小。 |


**返回**：


| 返回值 | 描述 |
| --- | --- |
| CUBLAS_STATUS_INVALID_VALUE | 如果 buf 为 NULL 或 sizeInBytes 与所选属性的内部存储大小不匹配。 |
| CUBLAS_STATUS_SUCCESS | 如果属性设置成功。 |


有关有效的返回码的完整列表，请参见 cublasStatus_t。



```c++

cublasStatus_t cublasLtMatrixTransform(
      cublasLtHandle_t lightHandle,
      cublasLtMatrixTransformDesc_t transformDesc,
      const void *alpha,
      const void *A,
      cublasLtMatrixLayout_t Adesc,
      const void *beta,
      const void *B,
      cublasLtMatrixLayout_t Bdesc,
      void *C,
      cublasLtMatrixLayout_t Cdesc,
      cudaStream_t stream);


```


This function computes the matrix transformation operation on the input matrices A and B, to produce the output matrix C, according to the below operation:


`C = alpha*transformation(A) + beta*transformation(B),`


where `A`, `B` are input matrices, and `alpha` and `beta` are input scalars. The transformation operation is defined by the `transformDesc` pointer. This function can be used to change the memory order of data or to scale and shift the values.


**Parameters**:


| Parameter | Memory | Input / Output | Description |
| --- | --- | --- | --- |
| lightHandle |  | Input | Pointer to the allocated cuBLASLt handle for the cuBLASLt context. See cublasLtHandle_t. |
| transformDesc |  | Input | Pointer to the opaque descriptor holding the matrix transformation operation. See cublasLtMatrixTransformDesc_t. |
| alpha, beta | Device or host | Input | Pointers to the scalars used in the multiplication. |
| A, B | Device | Input | Pointers to the GPU memory associated with the corresponding descriptors Adesc and Bdesc. |
| C | Device | Output | Pointer to the GPU memory associated with the Cdesc descriptor. |
| Adesc, Bdesc and Cdesc |  | Input | Handles to the previous created descriptors of the type cublasLtMatrixLayout_t.
Adesc or Bdesc can be NULL if the corresponding pointer is NULL and the corresponding scalar is zero. |
| stream | Host | Input | The CUDA stream where all the GPU work will be submitted. |


**Returns**:


| Return Value | Description |
| --- | --- |
| CUBLAS_STATUS_NOT_INITIALIZED | If cuBLASLt handle has not been initialized. |
| CUBLAS_STATUS_INVALID_VALUE | If the parameters are in conflict or in an impossible configuration. For example, when A is not NULL, but Adesc is NULL. |
| CUBLAS_STATUS_NOT_SUPPORTED | If the current implementation on the selected device does not support the configured operation. |
| CUBLAS_STATUS_ARCH_MISMATCH | If the configured operation cannot be run using the selected device. |
| CUBLAS_STATUS_EXECUTION_FAILED | If CUDA reported an execution error from the device. |
| CUBLAS_STATUS_SUCCESS | If the operation completed successfully. |


See cublasStatus_t for a complete list of valid return codes.




```c++

cublasStatus_t cublasLtMatrixTransformDescCreate(
      cublasLtMatrixTransformDesc_t *transformDesc,
      cudaDataType scaleType);


```

此函数通过分配保存其不透明结构所需的内存来创建矩阵变换描述符。

**参数**：

| 参数 | 内存 | 输入 / 输出 | 描述 |
| --- | --- | --- | --- |
| transformDesc |  | 输出 | 指向由此函数创建的矩阵变换描述符结构体的指针。请参阅 cublasLtMatrixTransformDesc_t。 |
| scaleType |  | 输入 | 指定此函数创建的矩阵变换描述符数据精度的枚举值。请参阅 cudaDataType_t。 |

**返回值**：

| 返回值 | 描述 |
| --- | --- |
| CUBLAS_STATUS_ALLOC_FAILED | 如果无法分配内存。 |
| CUBLAS_STATUS_SUCCESS | 如果描述符创建成功。 |

有关有效返回代码的完整列表，请参阅 cublasStatus_t。



```c++

cublasStatus_t cublasLtMatrixTransformDescDestroy(
      cublasLtMatrixTransformDesc_t transformDesc);


```


This function destroys a previously created matrix transform descriptor object.


**Parameters**:


| Parameter | Memory | Input / Output | Description |
| --- | --- | --- | --- |
| transformDesc |  | Input | Pointer to the structure holding the matrix transform descriptor that should be destroyed by this function. See cublasLtMatrixTransformDesc_t. |


**Returns**:


| Return Value | Description |
| --- | --- |
| CUBLAS_STATUS_SUCCESS | If the operation was successful. |


See cublasStatus_t for a complete list of valid return codes.




```c++
cublasStatus_t cublasLtMatrixTransformDescGetAttribute(
      cublasLtMatrixTransformDesc_t transformDesc,
      cublasLtMatrixTransformDescAttributes_t attr,
      void *buf,
      size_t sizeInBytes,
      size_t *sizeWritten);
```

此函数返回先前创建的矩阵变换描述符所属的查询属性的值。

**参数**：

| 参数 | 内存 | 输入/输出 | 描述 |
| --- | --- | --- | --- |
| transformDesc |  | 输入 | 指向先前创建的结构体的指针，该结构体保存由此函数查询的矩阵变换描述符。请参阅 `cublasLtMatrixTransformDesc_t`。 |
| attr |  | 输入 | 此函数将检索的属性。请参阅 `cublasLtMatrixTransformDescAttributes_t`。 |
| buf |  | 输出 | 包含此函数检索到的属性值的内存地址。 |
| sizeInBytes |  | 输入 | 用于验证的 buf 缓冲区大小（以字节为单位）。 |
| sizeWritten |  | 输出 | 仅在返回值为 `CUBLAS_STATUS_SUCCESS` 时有效。如果 `sizeInBytes` 非零：则 `sizeWritten` 为实际写入的字节数；如果 `sizeInBytes` 为零：则 `sizeWritten` 为写入完整内容所需的字节数。 |

**返回值**：

| 返回值 | 描述 |
| --- | --- |
| `CUBLAS_STATUS_INVALID_VALUE` | 如果 `sizeInBytes` 为零且 `sizeWritten` 为 NULL，或如果 `sizeInBytes` 非零且 `buf` 为 NULL，或如果 `sizeInBytes` 与所选属性的内部存储大小不匹配 |
| `CUBLAS_STATUS_SUCCESS` | 如果属性值已成功写入用户内存。 |

有关有效返回代码的完整列表，请参阅 `cublasStatus_t`。

```c++

cublasStatus_t cublasLtMatrixTransformDescInit(
      cublasLtMatrixTransformDesc_t transformDesc,
      cudaDataType scaleType);


```

此函数用于初始化先前已分配的矩阵变换描述符。

**参数**：

| 参数 | 内存 | 输入/输出 | 描述 |
| --- | --- | --- | --- |
| transformDesc |  | 输出 | 指向由此函数初始化的矩阵变换描述符结构体的指针。请参见 cublasLtMatrixTransformDesc_t。 |
| scaleType |  | 输入 | 指定此函数初始化的矩阵变换描述符数据精度的枚举值。请参见 cudaDataType_t。 |

**返回值**：

| 返回值 | 描述 |
| --- | --- |
| CUBLAS_STATUS_ALLOC_FAILED | 如果无法分配内存。 |
| CUBLAS_STATUS_SUCCESS | 如果描述符创建成功。 |

有关有效的返回码完整列表，请参见 cublasStatus_t。

```c++
cublasStatus_t cublasLtMatrixTransformDescSetAttribute(
      cublasLtMatrixTransformDesc_t transformDesc,
      cublasLtMatrixTransformDescAttributes_t attr,
      const void *buf,
      size_t sizeInBytes);
```

此函数用于设置先前创建的矩阵变换描述符的指定属性的值。

**参数**：

| 参数 | 内存 | 输入 / 输出 | 描述 |
| --- | --- | --- | --- |
| transformDesc |  | 输入 | 指向先前创建的结构体的指针，该结构体包含此函数查询的矩阵变换描述符。参见 `cublasLtMatrixTransformDesc_t`。 |
| attr |  | 输入 | 此函数将设置的属性。参见 `cublasLtMatrixTransformDescAttributes_t`。 |
| buf |  | 输入 | 指定属性将被设置的值。 |
| sizeInBytes |  | 输入 | buf 缓冲区的大小（以字节为单位），用于验证。 |

**返回值**：

| 返回值 | 描述 |
| --- | --- |
| CUBLAS_STATUS_INVALID_VALUE | 如果 buf 为 NULL 或 sizeInBytes 与所选属性的内部存储大小不匹配。 |
| CUBLAS_STATUS_SUCCESS | 如果属性设置成功。 |

有关有效的返回代码完整列表，请参见 `cublasStatus_t`。