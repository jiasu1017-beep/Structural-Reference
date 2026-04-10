# *VISCO





### *VISCO具有时间相关材料响应（蠕变、膨胀和粘弹性）的瞬态静态应力/位移分析。

此选项用于在具有时间相关材料行为（蠕变、膨胀和粘弹性）的分析中获得瞬态静态响应。

**产品：**Abaqus/Standard  Abaqus/CAE

**类型：**历史数据

**级别：**步

**Abaqus/CAE：**Step模块

##### **参考：**

- ["准静态分析," Section 6.2.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-avisco)
- ["率相关塑性：蠕变和膨胀," Section 23.2.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cratedepcreep)

### **可选参数：**

ALLSDTOL

包含此参数以指示将在此步中激活自适应自动阻尼算法。将此参数设置为稳定能量与总应变能量的最大允许比值。初始阻尼因子通过STABILIZE参数或FACTOR参数指定。然后，该阻尼因子将根据收敛历史和ALLSDTOL值在步中调整。如果此参数设置为零，则自适应自动阻尼算法不被激活；整个步中将使用恒定阻尼因子。如果包含此参数但未指定值，则默认值为0.05。如果省略此参数但包含具有消散能量分数默认值的STABILIZE参数，则自适应自动阻尼算法将自动激活，ALLSDTOL=0.05。

此参数必须与STABILIZE参数一起使用（参见["求解非线性问题," Section 7.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-anonlineareqns)）。

CETOL

将此参数设置为基于增量开始时的条件和增量结束时的条件从蠕变应变率计算的蠕变应变增量之间的最大差异，从而控制蠕变积分的精度。通常，可以通过选择可接受的应力误差容差并除以典型弹性模量来计算容差。如果模型由通过[*VISCOELASTIC](ch21abk04.md)选项表征的线性粘弹性材料组成，则可以使用比弹性应变数量级更宽松的容差。如果省略CETOL，则使用固定时间增量。

CONTINUE

设置CONTINUE=NO（默认）以指定此步不会携带先前一般步骤结果的阻尼因子。在这种情况下，初始阻尼因子将根据声明的阻尼强度和步的第一个增量的解重新计算，或者可以直接指定。

设置CONTINUE=YES以指定此步将携带紧邻先前一般步骤结束时的阻尼因子。

此参数必须与ALLSDTOL和STABILIZE参数一起使用。

CREEP

设置CREEP=EXPLICIT以在整个步中使用显式积分进行蠕变行为，这有时可能计算成本较低。时间增量将受到精度容差（CETOL）和前向差分算子的稳定性限制的限制。有关积分方案的详细信息，请参见["率相关塑性：蠕变和膨胀," Section 23.2.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cratedepcreep)。

FACTOR

如果由于局部不稳定问题预计不稳定且Abaqus/Standard计算的阻尼因子不合适，请将此参数设置为自动阻尼算法中使用的阻尼因子（参见["求解非线性问题," Section 7.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-anonlineareqns)）。此参数必须与STABILIZE参数一起使用，并覆盖基于消散能量分数值计算的阻尼因子。

STABILIZE

如果由于局部不稳定问题预计不稳定，请包含此参数以使用自动稳定。将此参数设置为自动阻尼算法的消散能量分数（参见["求解非线性问题," Section 7.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-anonlineareqns)）。如果省略此参数，则稳定算法不被激活。如果包含此参数但未指定值，则消散能量分数的默认值为2×10^-4，并且自适应自动阻尼算法将默认在此步中激活，ALLSDTOL=0.05；设置ALLSDTOL=0以停用自适应自动阻尼算法。如果使用FACTOR参数，则任何消散能量分数的值都将被阻尼因子覆盖。

### **瞬态准静态分析的数据行：**

**第一行（也是唯一行）：**





