# *DISTRIBUTING





### *DISTRIBUTING定义分布式耦合约束。

此选项用于定义分布式耦合约束。它必须与 [*COUPLING](ch03abk83.md) 选项结合使用，以定义参考节点和耦合节点。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：**模型数据  

**级别：**部件、部件实例、装配  

**Abaqus/CAE：**相互作用模块

##### **参考：**

- ["耦合约束，" Abaqus分析用户指南第35.3.2节](../usb/usb-link.md#usb-cni-pcoupling)
- [*COUPLING](ch03abk83.md)

### **可选参数：**

COUPLING

将此参数设置为用于将参考节点的位移和旋转耦合到影响半径内表面节点平均运动的方法。

设置 COUPLING=CONTINUUM（默认）以将每个连接点的位移和旋转耦合到影响半径内表面节点的平均位移。

设置 COUPLING=STRUCTURAL 以将每个连接点的位移和旋转耦合到影响半径内表面节点的平均位移和旋转。此参数值仅在三维分析中可用。

WEIGHTING METHOD

定义可选的加权方法以修改耦合节点处的默认权重分布。

设置 WEIGHTING METHOD=UNIFORM 以选择等于1.0的均匀权重分布。这是默认值。

设置 WEIGHTING METHOD=LINEAR 以选择随距参考节点距离线性递减的权重分布。

设置 WEIGHTING METHOD=QUADRATIC 以选择随距参考节点距离二次多项式递减的权重分布。

设置 WEIGHTING METHOD=CUBIC 以选择随距参考节点距离三次多项式单调递减的权重分布。

### **指定要约束的自由度的数据行：**

**第一行：**

根据需要重复此数据行，以指定不同自由度的约束。当在相关的 [*COUPLING](ch03abk83.md) 选项上指定了 ORIENTATION 参数时，自由度位于初始配置中的引用局部系统中；否则，它们位于全局系统中。在这两种情况下，这些方向将在大位移分析中随参考节点旋转（当在 [*STEP](ch18abk36.md) 选项上包含 NLGEOM 参数时）。




