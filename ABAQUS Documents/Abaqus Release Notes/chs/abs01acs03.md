# 15.3 Abaqus用户子程序的变更





本节总结了在对可用于Abaqus模型的用户子程序所做的更改和添加。

| **mod** | **(S)** | [`UCREEPNETWORK`](../sub/sub-link.md#sub-xsl-ucreepnetwork) |
| --- | --- | --- |
|  |  | 可以定义四个新变量：现在可以传入四个变量来获取信息： |
| **mod** | **(S)** | [`UEXTERNALDB`](../sub/sub-link.md#sub-xsl-uexternaldb) |
|  |  | 要传入获取信息的`LOP`变量可以采用新值。`LOP`=5表示用户子程序在步骤开始时被调用。`LOP`=6表示用户子程序在步骤结束时被调用。 |
| **mod** | **(S)** | [`UMAT`](../sub/sub-link.md#sub-xsl-umat) |
|  |  | 变量`JSTEP(1)`现在可以传入以标识步骤编号。 |
| **new** | **(S)** | [`UXFEMNONLOCALWEIGHT`](../sub/sub-link.md#sub-xsl-uxfemnonlocalweight) |
|  |  | 用户子程序，用于定义用于计算平均应力/应变以确定裂纹扩展方向的权函数。 |
| **new** | **(E)** | [`VEXTERNALDB`](../sub/sub-link.md#sub-xsl-vexternaldb) |
|  |  | 用户子程序，在分析的关键时刻将控制权交给用户，以便可以在Abaqus用户子程序和外部程序或文件之间动态交换数据。 |
| **new** | **(E)** | [`VUCHARLENGTH`](../sub/sub-link.md#sub-xsl-vucharlength) |
|  |  | 用户子程序，用于在材料点定义特征单元长度。 |




