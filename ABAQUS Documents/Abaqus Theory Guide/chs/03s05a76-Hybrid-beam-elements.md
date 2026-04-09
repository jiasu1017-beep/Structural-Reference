# 3.5.4 混合梁单元

### 3.5.4 混合梁单元

**产品：** Abaqus/Standard

Abaqus/Standard中的混合梁单元设计用于处理非常细长的情况，其中梁的轴向刚度相对于弯曲刚度非常大；因此需要混合方法，其中轴向力被视为独立未知量。对于剪切梁，提供了混合单元，其中横向剪切力也被视为独立未知量。本节讨论这些混合方法的基础。
### 轴向和弯曲行为

梁的内部虚功可以写成

![](../graphics/stm_eqn03898.gif)或者，我们可以引入独立的轴向力变量![](../graphics/stm_eqn03899.gif)，并写成

![](../graphics/stm_eqn03900.gif)其中![](../graphics/stm_eqn03901.gif)是引入的Lagrange乘子，用于强制执行约束![](../graphics/stm_eqn03902.gif)。这些表达式的线性组合为

![](../graphics/stm_eqn03903.gif)然后

![](../graphics/stm_eqn03904.gif)该项对牛顿方案的贡献为

![](../graphics/stm_eqn03905.gif)其中

![](../graphics/stm_eqn03906.gif)截面行为的切线刚度给出

![](../graphics/stm_eqn03907.gif)如果![](../graphics/stm_eqn03908.gif)（其中*L*是单元长度），则梁在轴向是柔性的，混合公式是不必要的。否则，我们假定上面第一个方程的逆定义![](../graphics/stm_eqn03909.gif)从![](../graphics/stm_eqn03910.gif)：

![](../graphics/stm_eqn03911.gif)所以

![](../graphics/stm_eqn03912.gif)

![](../graphics/stm_eqn03913.gif)现在使用乘以![](../graphics/stm_eqn00593.gif)的第一切线截面刚度和乘以![](../graphics/stm_eqn03914.gif)的第二切线截面刚度，单元的牛顿贡献变为

![](../graphics/stm_eqn03915.gif)其中![](../graphics/stm_eqn03916.gif)是

![](../graphics/stm_eqn03917.gif)变量![](../graphics/stm_eqn03899.gif)在单元中每个积分点处被作为独立值选取。我们选择![](../graphics/stm_eqn00593.gif)为![](../graphics/stm_eqn03918.gif)，其中![](../graphics/stm_eqn03919.gif)是一个小值。通过这样的选择，通过确保在每个单元的位移变量之后消除变量![](../graphics/stm_eqn03899.gif)，高斯消元方案在求解方程时没有困难。
### 横向剪切

在允许横向剪切的混合单元（B21H、B22H、B31H、B32H）中，通过将剪切力作为独立变量处理，使用以下公式来强制执行横向剪切约束。与横向剪切相关的内部虚功为

![](../graphics/stm_eqn03920.gif)其中![](../graphics/stm_eqn03921.gif)和![](../graphics/stm_eqn03922.gif)是截面上的剪切力，![](../graphics/stm_eqn03923.gif)和![](../graphics/stm_eqn03924.gif)是横向剪切应变的变分。虚功也可以通过引入独立剪切力变量![](../graphics/stm_eqn03925.gif)和![](../graphics/stm_eqn03926.gif)写成

![](../graphics/stm_eqn03927.gif)其中![](../graphics/stm_eqn03928.gif)是Lagrange乘子。与轴向情况一样，我们取这两种形式的线性组合，

![](../graphics/stm_eqn03929.gif)其中![](../graphics/stm_eqn00593.gif)稍后定义。这给出

![](../graphics/stm_eqn03930.gif)其中

![](../graphics/stm_eqn03931.gif)该项对牛顿方案的贡献为

![](../graphics/stm_eqn03932.gif)

![](../graphics/stm_eqn03933.gif)

Abaqus以弹性方式处理横向剪切，所以![](../graphics/stm_eqn03934.gif)，其中![](../graphics/stm_eqn03935.gif)是常数。然后牛顿贡献为

![](../graphics/stm_eqn03936.gif)

![](../graphics/stm_eqn03937.gif)

我们现在定义![](../graphics/stm_eqn03938.gif)并选择![](../graphics/stm_eqn03939.gif)，其中![](../graphics/stm_eqn01999.gif)是相对于![](../graphics/stm_eqn03935.gif)的一个小值，以给出

![](../graphics/stm_eqn03940.gif)

![](../graphics/stm_eqn03941.gif)
### 参考

### 参考

"Abaqus Analysis User's Guide"第29.3.3节"选择梁单元"
