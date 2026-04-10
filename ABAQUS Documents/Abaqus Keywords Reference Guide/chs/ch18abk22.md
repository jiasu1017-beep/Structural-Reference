# *SOILS





### *SOILS充液多孔介质的有效应力分析。

此选项用于指定部分或完全饱和充液多孔介质的瞬态（固结）或稳态响应分析。

**产品：**Abaqus/Standard  Abaqus/CAE

**类型：**历史数据

**级别：**步

**Abaqus/CAE：**Step模块

##### **参考：**

- ["Coupled pore fluid diffusion and stress analysis," Section 6.8.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-acoupdiffstress)
- ["Rate-dependent plasticity: creep and swelling," Section 23.2.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cratedepcreep)

### **可选参数：**

ALLSDTOL

包含此参数以指示将在此步中激活自适应自动阻尼算法。将此参数设置为稳定能量与总应变能量的最大允许比值。初始阻尼因子通过STABILIZE参数或FACTOR参数指定。然后，该阻尼因子将基于收敛历史和ALLSDTOL值在步中调整。如果此参数设置为零，则不会激活自适应自动阻尼算法；将在整个步中使用恒定阻尼因子。如果此参数包含但未指定值，则默认值为0.05。如果省略此参数但包含具有耗散能量分数默认值的STABILIZE参数，则自适应自动阻尼算法将自动激活，ALLSDTOL=0.05。

此参数必须与STABILIZE参数配合使用（参见["Solving nonlinear problems," Section 7.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-anonlineareqns)）。

CETOL

此参数将调用自动时间增量。如果省略UTOL、DELTMX和CETOL参数，将使用固定时间增量。

此参数仅在材料响应包含时间相关蠕变行为时有意义；CETOL控制蠕变积分精度。将此参数设置为在增量开始和结束时从蠕变应变率计算的蠕变应变增量的最大允许差值（参见["Rate-dependent plasticity: creep and swelling," Section 23.2.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cratedepcreep)）。

容差可以通过选择可接受的应力误差容差并除以典型弹性模量来计算。

CONSOLIDATION

包含此参数以选择瞬态（固结）分析。省略此参数以选择稳态分析。

CONTINUE

设置CONTINUE=NO（默认）以指定此步不会从前一个通用步的结果中继承阻尼因子。在这种情况下，初始阻尼因子将基于声明的阻尼强度和步第一增量解重新计算，或可以直接指定。

设置CONTINUE=YES以指定此步将继承紧邻前一个通用步结束时的阻尼因子。

此参数必须与ALLSDTOL和STABILIZE参数配合使用。

DELTMX

此参数将调用自动时间增量。将此参数设置为在增量内允许的最大温度变化。Abaqus/Standard将限制时间步长以确保在步的任何增量内任何节点都不会超过此值。如果在瞬态分析中省略此参数、CETOL参数和UTOL参数，将使用固定时间增量，其时间增量等于初始时间增量。

END

此参数仅对瞬态分析有意义。设置END=PERIOD（默认）以分析指定时间段。设置END=SS以在达到稳态时结束步。

CREEP

设置CREEP=NONE以指定即使已定义蠕变或粘弹性材料属性，在此步中也不会发生蠕变或粘弹性响应。

FACTOR

如果由于局部不稳定预期问题可能不稳定，且Abaqus/Standard计算的阻尼因子不合适，则将此参数设置为自动阻尼算法（参见["Solving nonlinear problems," Section 7.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-anonlineareqns)）中使用的阻尼因子。此参数必须与STABILIZE和CONSOLIDATION参数配合使用，并覆盖基于耗散能量分数值对阻尼因子的自动计算。

HEAT

如果模型中有使用耦合温度-孔隙压力单元的区域，则此参数是相关的；它指定是否在这些区域中建立热传递效应模型。

如果模型中仅使用耦合孔隙压力-位移单元，则此参数不相关。

设置HEAT=YES（默认）以指定将在这些区域中建立热传递效应模型。在这种情况下，Abaqus/Standard将联立求解热传递方程、机械平衡方程和流体流动连续性方程。

设置HEAT=NO以指定不会在这些区域中建立热传递模型。

STABILIZE

如果由于局部不稳定预期问题可能不稳定，则包含此参数以使用自动稳定。将此参数设置为自动阻尼算法（参见["Solving nonlinear problems," Section 7.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-anonlineareqns)）的耗散能量分数。如果省略此参数，则不会激活稳定算法。如果此参数包含但未指定值，则耗散能量分数的默认值为2×10^-4，并且自适应自动阻尼算法将默认在此步中激活，ALLSDTOL=0.05；设置ALLSDTOL=0以停用自适应自动阻尼算法。如果使用FACTOR参数，则任何耗散能量分数值都将被阻尼因子覆盖。

此参数只能与CONSOLIDATION参数配合使用。

UTOL

此参数将调用自动时间增量。如果省略UTOL、DELTMX和CETOL参数，将使用固定时间增量。

将此参数设置为瞬态固结分析中任何增量允许的最大孔隙压力变化（以压力单位计）。Abaqus/Standard将限制时间步长以确保在分析的任何增量内任何节点（具有边界条件的节点除外）都不会超过此值。

在稳态分析中，将此值设置为任何非零值（以激活自动时间增量）。

### **定义土壤分析增量设置的数据行：**

**第一行（也是唯一行）：**




