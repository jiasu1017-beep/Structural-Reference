### 3.1.5. 禁用 CPU 指令

如"启发式缓存"部分所述，cuBLASLt 启发式算法在主机 CPU 上执行一些计算密集型操作。
为了加速这些操作，实现会检测 CPU 能力并可能使用特殊指令，例如 x86-64 CPU 上的高级矢量扩展 (AVX)。
然而，在某些极少数情况下，这可能并不可取。例如，使用高级指令可能导致 CPU 以更低的频率运行，从而影响其他主机代码的性能。

用户可以选择指示 cuBLASLt 库不使用某些 CPU 指令，可通过 `CUBLASLT_DISABLE_CPU_INSTRUCTIONS_MASK` 环境变量或 `cublasLtDisableCpuInstructionsSetMask()` 函数（后者具有更高优先级）来实现。
默认掩码为 0，意味着没有限制。

有关更多信息，请查阅 `cublasLtDisableCpuInstructionsSetMask()`。