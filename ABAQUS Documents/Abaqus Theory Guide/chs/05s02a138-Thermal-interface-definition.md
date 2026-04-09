# 5.2.4 热界面定义

### 5.2.4 热界面定义

**产品：** Abaqus/Standard  Abaqus/Explicit

Abaqus/Standard允许通过传导或辐射在界面上进行热传递。通常，这两种热传递模式都以某种程度存在。无论何种模式，跨界面的热传递假定仅发生在法向方向。

### 传导

跨界面的热传导假定定义为
![](../graphics/stm_eqn07777.gif)![](../graphics/stm_eqn02389.gif)![](../graphics/stm_eqn01047.gif)![](../graphics/stm_eqn07778.gif)![](../graphics/stm_eqn05050.gif)![](../graphics/stm_eqn02435.gif)![](../graphics/stm_eqn02390.gif)
其中是从一个表面上的点到另一个表面上的点的每单位面积热通量，和是两表面上点的温度，是间隙电导。
![](../graphics/stm_eqn02389.gif)
的导数为
![](../graphics/stm_eqn07779.gif)
其中
![](../graphics/stm_eqn07780.gif)
### 辐射
![](../graphics/stm_eqn07781.gif)
对应点之间的单位面积热流量假定为

其中是在使用的温标上绝对零温度的值；是从间隙中每单位表面面积穿过间隙的热通量，从表面到表面；和是两表面的温度；是从两个表面的发射率导出的间隙辐射常数。

![](../graphics/stm_eqn07782.gif)![](../graphics/stm_eqn02243.gif)![](../graphics/stm_eqn02389.gif)![](../graphics/stm_eqn01047.gif)![](../graphics/stm_eqn07778.gif)![](../graphics/stm_eqn05050.gif)![](../graphics/stm_eqn02435.gif)![](../graphics/stm_eqn07783.gif)的导数为

![](../graphics/stm_eqn02389.gif)### Jacobian矩阵

![](../graphics/stm_eqn07784.gif)热平衡变分陈述的贡献为

![](../graphics/stm_eqn07785.gif)其中是面积。牛顿求解器Jacobian矩阵的贡献为

其中

对于"粘结"热接触，点处的温度被约束为与点具有相同的温度。使用拉格朗日乘子方法通过以下方式增强热平衡陈述来施加约束：
![](../graphics/stm_eqn07786.gif)![](../graphics/stm_eqn01047.gif)
其中是拉格朗日乘子。牛顿求解器Jacobian矩阵的贡献为
![](../graphics/stm_eqn07787.gif)
### 参考
![](../graphics/stm_eqn07788.gif)
### 参考
![](../graphics/stm_eqn01047.gif)![](../graphics/stm_eqn07778.gif)
"Abaqus Analysis User's Guide"第37.2.1节"热接触属性"
![](../graphics/stm_eqn07789.gif)![](../graphics/stm_eqn00280.gif)