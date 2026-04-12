# 13.3 用户子程序UMAT的增强





### 13.3 用户子程序[`UMAT`](../sub/sub-link.md#sub-xsl-umat)的增强

**产品：** Abaqus/Explicit

**优点：** 您现在可以使用用户子程序[`UMAT`](../sub/sub-link.md#sub-xsl-umat)来定义频域粘弹性材料行为的阻尼部分，使用总混合公式为混合单元定义几乎不可压缩的非线性弹性响应，以及为混合单元定义完全不可压缩的非线性弹性响应。

**描述：** 频域中的粘弹性行为需要指定存储模量（材料刚度）和损耗模量（材料阻尼）。[`UMAT`](../sub/sub-link.md#sub-xsl-umat)接口和实现已增强以支持材料刚度和材料阻尼的规范。此功能允许您定义具有复频依赖性的粘弹性响应，而Abaqus/Standard中不支持内置模型。

当用户材料用于定义混合单元响应时，Abaqus使用的默认公式适用于使用增量公式的材料模型（例如金属塑性），但与超弹性材料常用的总公式不一致。在后一种情况下，默认公式可能导致收敛问题。例如，当几乎不可压缩的非线性弹性用户材料受到大变形时，可能会观察到这种收敛问题。Abaqus/Standard现在为这种情况提供了替代的总公式。此公式与Abaqus用于超弹性材料的原生几乎不可压缩公式一致，在这些情况下比默认公式效果更好。Abaqus/Standard还首次提供了通过用户子程序[`UMAT`](../sub/sub-link.md#sub-xsl-umat)定义完全不可压缩响应（用于混合单元）的功能。总混合公式可以通过对现有[`UMAT`](../sub/sub-link.md#sub-xsl-umat)的最小更改来实现。对于完全不可压缩材料，[`UMAT`](../sub/sub-link.md#sub-xsl-umat)只需要定义材料响应的偏应力部分。
**参考：**

**Abaqus关键词参考指南**
- [*USER MATERIAL](../key/key-link.md#usb-kws-musermaterial)

**Abaqus用户子程序参考指南**
- ["UMAT，" 第1.1.41节](../sub/sub-link.md#sub-rtn-uumat)




