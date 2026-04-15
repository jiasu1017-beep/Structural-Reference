

3.1.4.4.1. 1D Block Quantization

Consider a single block of $k$ elements of $D$ in the $M$ dimension: $D^b_{fp32} = \left[d^i_{fp32}\right]_{i=1}^k$. Quantization of partial blocks is performed as if the missing values are zero. Let $Amax(DType)$ be the maximal value representable in the destination precision.


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


Here we assume that the algorithm is provided with a precomputed input tensorwide scaling factor $scale_D^{in}$ which in general case is computed as



```

\[scale_D^{in} = \frac{Amax(e2m1) \cdot Amax(e4m3)}{Amax(D_{temp})},\]
```


where $Amax(D_{temp})$ is a global absolute maximum of matmul results before quantization. Since computing this value requires knowing the result of the whole computation, an approximate value from e.g. the previous iteration is used in practice.


Computations consist of the following steps:


1. Compute the narrow precision value of the block scaling factor \(S^b_{e4m3} = e4m3(S^b_{fp32})\).
2. Compute the block conversion factor \(R^b_{fp32} = \frac{1}{fp32(S^b_{e4m3})}\).


**Applying conversion factors**


For each $i = 1 \ldots k$, compute $d^i = DType(d^i_{fp32} \cdot R^b_{fp32})$. The resulting quantized block is $\left(S^b, \left[d^i\right]_{i=1}^k\right)$, where $S^b$ is $S^b_{ue8m0}$ for FP8 with UE8M0 scaling factors, and $S^b_{ue4m3}$ for FP4 with UE4M3 scaling factors.


