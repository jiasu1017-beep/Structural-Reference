### 3.4.18. cublasLtMatmulAlgoCapGetAttribute()

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