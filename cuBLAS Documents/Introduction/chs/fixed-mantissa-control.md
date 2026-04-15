#### 1.5.2.2. 固定尾数控制

固定尾数控制可用于进一步加速定点模拟。用户可以通过 `cublasSetFixedPointEmulationMaxMantissaBitCount()` 为定点表示提供尾数位数；然而，如果没有自动动态精度框架，则无法保证达到或优于FP64算术的精度。