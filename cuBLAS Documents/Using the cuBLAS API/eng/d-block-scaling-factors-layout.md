

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


