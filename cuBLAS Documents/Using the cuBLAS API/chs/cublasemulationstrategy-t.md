### 2.2.12. cublasEmulationStrategy_t

`cublasEmulationStrategy_t` 枚举类型用于 `cublasSetEmulationStrategy()`，用于选择如何利用浮点模拟算法。

| 值 | 含义 |
| --- | --- |
| `CUBLAS_EMULATION_STRATEGY_DEFAULT` | 这是默认的模拟策略，等效于 `CUBLAS_EMULATION_STRATEGY_PERFORMANT`，除非设置了 `CUBLAS_EMULATION_STRATEGY` 环境变量。 |
| `CUBLAS_EMULATION_STRATEGY_PERFORMANT` | 一种只要能带来性能提升就使用模拟的策略。 |
| `CUBLAS_EMULATION_STRATEGY_EAGER` | 一种尽可能使用模拟的策略。 |

> **注意**

注意
一般来说，`cublasSetEmulationStrategy()` 函数优先于环境变量设置。
但是，将环境变量 `CUBLAS_EMULATION_STRATEGY` 设置为 performant 或 eager 将覆盖默认的模拟策略，即使默认策略是由函数调用设置的。