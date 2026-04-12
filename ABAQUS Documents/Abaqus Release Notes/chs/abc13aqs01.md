# 13.1 VEXTERNALDB：在分析关键时刻将控制权交给用户的用户子程序





### 13.1 [`VEXTERNALDB`](../sub/sub-link.md#sub-xsl-vexternaldb)：在分析关键时刻将控制权交给用户的用户子程序

**产品：** Abaqus/Explicit

**优点：** 您现在可以使用用户子程序[`VEXTERNALDB`](../sub/sub-link.md#sub-xsl-vexternaldb)在Abaqus用户子程序和外部程序或文件之间动态交换数据。

**描述：** 用户子程序[`VEXTERNALDB`](../sub/sub-link.md#sub-xsl-vexternaldb)在分析开始时自动调用一次，在每个步骤开始时调用一次，在每个增量之前调用一次，在每个增量开始时调用一次，在每个增量结束时调用一次，在每个步骤结束时调用一次，最后在分析结束时调用一次；因此在关键时刻将控制权交给您。如果需要，您可以修改建议的时间增量并触发重新启动数据的输出。您还可以指示Abaus跳过当前步骤的其余部分或终止整个分析。您可以使用新的可分配局部数组实用程序来协调给定进程中各个用户子程序之间的数据。此外，您可以在[`VEXTERNALDB`](../sub/sub-link.md#sub-xsl-vexternaldb)中部署可分配全局数组和MPI机制，以在域并行分析中同步各进程之间的数据。
**参考：**

**Abaqus用户子程序参考指南**
- ["VEXTERNALDB，" 第1.2.3节](../sub/sub-link.md#sub-rtn-uexpexternaldb)
- ["获取并行进程信息，" 第2.1.4节](../sub/sub-link.md#sub-utl-ugetnumcpus)
- ["可分配数组，" 第2.1.23节](../sub/sub-link.md#sub-utl-localarrays)




