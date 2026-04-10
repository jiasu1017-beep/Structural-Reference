# *STEP





### *STEP开始一个步。

此选项用于开始每个步定义。它必须后跟过程定义选项。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CFD  Abaqus/CAE

**类型：**历史数据

**级别：**模型

**Abaqus/CAE：**Step模块

##### **参考：**

- ["Defining an analysis," Section 6.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aover)
- ["Convergence criteria for nonlinear problems," Section 7.2.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aconvergcriteria)
- ["Design sensitivity analysis," Section 19.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-adsa)
- [*END STEP](ch05abk20.md)

### 在Abaqus/Standard分析中开始一个步

### **可选参数：**

AMPLITUDE

此参数定义步期间载荷幅值的默认幅值变化。

如果载荷要在步开始时立即应用并在整个步中保持恒定，则设置AMPLITUDE=STEP。

如果载荷幅值要在步中从上一步结束时的值（或分析开始时的零）线性变化到载荷选项给出的值，则设置AMPLITUDE=RAMP。

如果省略此参数，则默认幅值选择取决于所选过程，如["Defining an analysis," Section 6.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aover)所示。默认幅值变化可以通过在载荷选项上使用AMPLITUDE参数（["Amplitude curves," Section 34.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-pamplitude)）为各个载荷覆盖。

此参数很少需要，改变默认值可能导致问题。例如，没有实际时间尺度的过程（如[*STATIC](ch18abk31.md)选项）中的自动载荷增量方案通过增加归一化时间尺度来逐渐应用载荷。AMPLITUDE=STEP的使用指定整个载荷将立即应用，因此如果载荷导致强非线性响应，Abaqus/Standard可能无法选择合适的小增量。

CONVERT SDI

此参数决定如何在非线性分析期间考虑严重不连续性（如接触变化）。

设置CONVERT SDI=YES（默认）以使用局部收敛准则确定是否需要新迭代。Abaqus/Standard将确定与严重不连续性相关的最大穿透和估计力误差，并检查这些误差是否在容差范围内。因此，如果严重不连续性很小，解决方案可能会收敛。

设置CONVERT SDI=NO以在迭代期间发生严重不连续性时强制进行新迭代，无论穿透和力误差的大小如何。此选项还更改一些时间增量参数，并使用不同准则确定是进行另一次迭代还是以更小的增量大小进行新尝试。

如果省略CONVERT SDI参数，Abaqus/Standard将使用在前一个通用分析步中指定的值。重启分析的第一个新步除外，无论前一步中的设置如何，它都将默认使用CONVERT SDI=YES。

此参数与传热分析和线性扰动步无关，将被忽略。

DSA

此参数仅适用于Abaqus/Design。

设置DSA=YES以激活步的设计敏感性分析。一旦在通用步中激活DSA，它将保持活动状态在所有后续通用步中，直到在后续通用步中通过设置DSA=NO停用它。一旦在扰动步中激活DSA，它将保持活动状态在所有后续连续扰动步中，直到在后续连续扰动步中停用它。但是，如果在不支持DSA的过程中激活DSA，则DSA将被停用，直到通过设置DSA=YES再次激活。

EXTRAPOLATION

此参数仅对非线性分析有用。

设置EXTRAPOLATION=LINEAR（[*DYNAMIC](ch04abk43.md)，APPLICATION=TRANSIENT FIDELITY以外的过程的默认设置）以指示过程本质上是单调的，因此Abaqus/Standard应使用前一个增量解的100%线性外推（在时间上）来开始当前增量的非线性方程求解（Riks方法使用1%外推）。

设置EXTRAPOLATION=PARABOLIC以指示过程应使用前两个增量解的二次基于位移的外推（在时间上）来开始当前增量的非线性方程求解。

设置EXTRAPOLATION=VELOCITY PARABOLIC（仅适用于[*DYNAMIC](ch04abk43.md)过程，且是[*DYNAMIC](ch04abk43.md) APPLICATION=TRANSIENT FIDELITY过程的默认设置）以指示过程应使用前增量解的二次基于速度的外推（在时间上）来开始当前增量的非线性方程求解。

设置EXTRAPOLATION=NO以抑制任何外推。

INC

将此参数设置为步中的最大增量数（或对于直接循环分析，为单个载荷循环）。此值仅是上限。默认值为100。

INC参数在不能使用自动增量的过程中没有影响（例如[*BUCKLE](ch02abk16.md)、[*STEADY STATE DYNAMICS](ch18abk34.md)和[*MODAL DYNAMIC](ch13abk18.md)）。

NAME

将此参数设置为将用于在输出数据库中引用步的标签。同一输入文件中的步名称必须唯一。原始输入文件中的步名称可以在重启输入文件中重复使用。

NLGEOM

省略此参数或设置NLGEOM=NO以在当前步中执行几何线性分析。包含此参数或设置NLGEOM=YES以指示应在步期间考虑几何非线性（仅适用于应力分析、完全耦合热应力分析和耦合热电应力分析）。一旦NLGEOM选项被开启，它将在分析中所有后续步中保持活动状态。

PERTURBATION

包含此参数以指示这是一个线性扰动步。对于此类分析，Abaqus/Standard期望给出载荷、边界和温度变化，结果将是相对于前一步的变化。*在使用此选项之前，请阅读["General and linear perturbation procedures," Section 6.1.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-alinearnonlinear)、["Mesh-to-mesh solution mapping," Section 12.4.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-amapsolution)和["Applying loads: overview," Section 34.4.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-ploading)中的讨论。*

SOLVER

设置SOLVER=ITERATIVE以使用迭代线性方程求解器。*在使用此选项之前，请阅读["Iterative linear equation solver," Section 6.1.6 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aitrsolveroverview)中的讨论。*

如果省略此参数，则使用默认直接稀疏求解器。

UNSYMM

设置UNSYMM=YES以指示应使用非对称矩阵存储和求解。

设置UNSYMM=NO以指示应使用对称存储和求解。

此参数的默认值取决于所使用的模型和过程选项。用户仅在某些情况下允许更改默认值。如果在这种情况下未使用UNSYMM参数，Abaqus/Standard将使用在前一个通用分析步中指定的值。有关使用此参数的更详细讨论，请参见["Defining an analysis," Section 6.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aover)。

### **可选数据行：**

**第一行：**

副标题可以有多行，但只有第一行的前80个字符将被保存并打印为副标题。

### 在Abaqus/Explicit分析中开始一个步

### **可选参数：**

NAME

将此参数设置为用于在输出数据库中标识步的名称。同一输入文件中的步名称必须唯一。

NLGEOM

设置NLGEOM=YES（默认）以指示应在步期间考虑几何非线性（仅适用于应力分析和完全耦合热应力分析）。一旦NLGEOM选项被开启，它将在分析中所有后续步中保持活动状态。设置NLGEOM=NO以在当前步中执行几何线性分析。

在Abaqus/Explicit分析中，NLGEOM参数的默认值是YES，除非Abaqus/Explicit分析是导入分析，在这种情况下，NLGEOM参数的默认值与导入时参数的值相同。

### **可选数据行：**

**第一行：**

副标题可以有多行，但只有第一行的前80个字符将被保存并打印为副标题。

### 在Abaqus/CFD分析中开始一个步

### **可选参数：**

NAME

将此参数设置为用于在输出数据库中标识步的名称。同一输入文件中的步名称必须唯一。

### **可选数据行：**

**第一行：**

副标题可以有多行，但只有第一行的前80个字符将被保存并打印为副标题。




