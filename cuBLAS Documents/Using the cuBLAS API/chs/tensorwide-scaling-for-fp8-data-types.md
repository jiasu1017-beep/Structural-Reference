#### 3.1.4.1. FP8数据类型的逐张量缩放

当所有FP8精度张量的 `CUBLASLT_MATMUL_DESC_{X}_SCALE_MODE` 属性（此处 `X` 代表 `A`、`B`、`C`、`D` 或 `EPILOGUE_AUX`；参见 cublasLtMatmulDescAttributes_t）设置为 `CUBLASLT_MATMUL_MATRIX_SCALE_SCALAR_32F`（这是FP8张量的默认值）时，将启用逐张量缩放。在这种情况下，cuBLAS中的矩阵乘法运算定义如下（为便于说明，假设所有张量都使用FP8精度）：

```

\[D = scale_D \cdot (\alpha \cdot scale_A \cdot scale_B \cdot \text{op}(A) \text{op}(B) + \beta \cdot scale_C \cdot C).\]
```

此处 $A$、$B$ 和 $C$ 是输入张量，$scale_A$、$scale_B$、$scale_C$、$scale_D$、$\alpha$ 和 $\beta$ 是输入标量。这与其他矩阵乘法例程不同，因为增加了每个矩阵的缩放因子。$scale_A$、$scale_B$ 和 $scale_C$ 用于反量化，$scale_D$ 用于量化。请注意，所有缩放因子均以乘法方式应用。这意味着有时需要根据缩放因子应用的上下文使用该缩放因子或其倒数。有关FP8的更多信息，请参见 cublasLtMatmul() 和 cublasLtMatmulDescAttributes_t。

对于此类矩阵乘法，结尾程序和中间值绝对最大值按以下方式计算：

```

\[\begin{split}Aux_{temp} & = \alpha \cdot scale_A \cdot scale_B \cdot \text{op}(A) \text{op}(B) + \beta \cdot scale_C \cdot C + bias, \\
D_{temp} & = \mathop{Epilogue}(Aux_{temp}), \\
amax_{D} & = \mathop{absmax}(D_{temp}), \\
amax_{Aux} & = \mathop{absmax}(Aux_{temp}), \\
D & = scale_D * D_{temp}, \\
Aux & = scale_{Aux} * Aux_{temp}. \\\end{split}\]
```

此处 $Aux$ 是矩阵乘法的辅助输出，由传递给GELU等结尾函数的值组成，$scale_{Aux}$ 是可应用于 $Aux$ 的可选缩放因子，$amax_{Aux}$ 是缩放前 $Aux$ 中的最大绝对值。有关更多信息，请参见 cublasLtMatmulDescAttributes_t 中的 `CUBLASLT_MATMUL_DESC_AMAX_D_POINTER` 和 `CUBLASLT_MATMUL_DESC_EPILOGUE_AUX_AMAX_POINTER` 属性。

> **注意**

注意
如上方程式所示，偏置在计算 $Aux_{temp}$ 之前应用。