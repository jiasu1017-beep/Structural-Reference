# 3.4.2 桁架单元

### 3.4.2 桁架单元

![](../graphics/stm_eqn03460.gif)**产品：** Abaqus/Standard  Abaqus/Explicit

桁架单元是假设仅通过轴向拉伸变形的 一维杆或棒。它们在节点处是销接头，因此离散化中仅使用平移位移和每个节点的初始位置向量。当应变较大时，通过假定桁架由不可压缩材料制成来简化公式。

Abaqus中有两个桁架单元：一个2节点线性插值桁架和一个3节点二次插值桁架。二次插值版本在库中主要用于与其他类型的二次插值单元（如壳单元S8R5）兼容。笛卡尔位移分量和初始位置向量的笛卡尔分量使用相同的插值函数，因此这些单元是最简单形式的等参单元。

这些单元是一维的：沿着单元定义单个材料（等参）坐标*g*，单元中为![](../graphics/stm_eqn03446.gif)。在2节点单元中，节点1在![](../graphics/stm_eqn03447.gif)，节点2在![](../graphics/stm_eqn03448.gif)。在3节点版本中，节点1在![](../graphics/stm_eqn03447.gif)，节点2在![](../graphics/stm_eqn03449.gif)，节点3在![](../graphics/stm_eqn03450.gif)。
### 插值

2节点单元的插值为

![](../graphics/stm_eqn03451.gif)3节点单元为

![](../graphics/stm_eqn03452.gif)其中![](../graphics/stm_eqn01385.gif)、![](../graphics/stm_eqn01386.gif)和![](../graphics/stm_eqn03453.gif)是变量在节点处的值，![](../graphics/stm_eqn03454.gif是该变量的插值。
### 应变度量

这些是一维单元，唯一考虑的应变是沿单元轴线的应变。沿轴线的拉伸比为

![](../graphics/stm_eqn03455.gif)其中*l*测量当前配置中沿桁架轴线的长度：

![](../graphics/stm_eqn03456.gif)![](../graphics/stm_eqn03457.gif)测量原始配置中沿轴线的长度。

对于几何非线性分析，我们使用对数应变度量：

![](../graphics/stm_eqn03458.gif)
### 应变的一阶变分

应变的一阶变分为

![](../graphics/stm_eqn03459.gif)其中

![](../graphics/stm_eqn03460.gif)是沿桁架轴线的单位切线。
### 应变的二阶变分

应变的二阶变分为

![](../graphics/stm_eqn03461.gif)
### 积分

**刚度**

线性桁架是常应变单元，因此被精确积分。二次桁架使用两个Gauss点进行数值积分。

**质量和一致载荷**

线性桁架有两个Gauss点。二次桁架有三个Gauss点。
### 虚功贡献

桁架单元中应力的虚功贡献为

![](../graphics/stm_eqn03462.gif)其中*a*是桁架的当前横截面积，![](../graphics/stm_eqn01110.gif)是沿桁架的"真实"（柯西）应力，![](../graphics/stm_eqn00377.gif)是对数应变，*l*是单元的长度。

由于我们假定桁架是不可压缩的，![](../graphics/stm_eqn03463.gif)，其中*A*是原始面积，*L*是桁架的原始长度。因此，

![](../graphics/stm_eqn03464.gif)

这就是桁架单元内部虚功贡献使用的形式。
### 混合（混合）形式

"混合"桁架单元也可在Abaqus/Standard中使用。在这些单元中，积分点处的轴向力作为额外变量引入，引入兼容性条件来定义这些变量。该公式与混合梁单元使用的公式相同（"混合梁单元，" 第3.5.4节），没有弯曲项。
### 参考

### 参考

![](../graphics/stm_eqn03454.gif)![](../graphics/stm_eqn01386.gif)![](../graphics/stm_eqn03453.gif)![](../graphics/stm_eqn03452.gif)![](../graphics/stm_eqn01385.gif)"Abaqus Analysis User's Guide"第29.2.1节"桁架单元"
