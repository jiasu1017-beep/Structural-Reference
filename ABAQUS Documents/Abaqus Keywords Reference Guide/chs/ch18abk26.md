# *SOLUTION TECHNIQUE





### *SOLUTION TECHNIQUE指定替代求解方法。

此选项用于指定准牛顿方法代替标准牛顿方法求解非线性方程，或为耦合温度-位移和耦合热电过程指定分离求解方案。

**产品：**Abaqus/Standard  Abaqus/CAE

**类型：**历史数据

**级别：**步

**Abaqus/CAE：**Step模块

##### **参考：**

- ["Fully coupled thermal-stress analysis," Section 6.5.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-acouptempdisp)
- ["Coupled thermal-electrical analysis," Section 6.7.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-ajouleheating)
- ["Convergence criteria for nonlinear problems," Section 7.2.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aconvergcriteria)

### **必需参数：**

TYPE

设置TYPE=QUASI-NEWTON以指定准牛顿求解方法。

设置TYPE=SEPARATED以指定完全耦合过程中各个场的线性化方程将被解耦并分别求解每个场。此选项只能与[*COUPLED THERMAL-ELECTRICAL](ch03abk82.md)过程和没有ELECTRICAL参数的[*COUPLED TEMPERATURE-DISPLACEMENT](ch03abk81.md)过程一起指定。

### **可选参数：**

REFORM KERNEL

此参数只能与TYPE=QUASI-NEWTON一起使用。将此参数设置为在重新形成核矩阵之前允许的准牛顿迭代次数。默认值为REFORM KERNEL=8。

**此选项没有关联的数据行。**




