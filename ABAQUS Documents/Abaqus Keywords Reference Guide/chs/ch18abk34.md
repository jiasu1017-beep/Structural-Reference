# *STEADY STATE DETECTION





### *STEADY STATE DETECTION指定终止准静态单向模拟的稳态要求。

此选项用于定义必须满足的条件以确定已达到稳态。它必须与[*STEADY STATE CRITERIA](ch18abk32.md)选项配合使用。

**产品：**Abaqus/Explicit

**类型：**历史数据

**级别：**步

##### **参考：**

- ["Steady-state detection," Section 11.8.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-asteadystatedetection)
- ["Output to the output database," Section 4.1.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-out-odboutput)
- [*STEADY STATE CRITERIA](ch18abk32.md)

### **必需参数：**

ELSET

将此参数设置为正在应用此稳态检测定义的单元集名称。

SAMPLING

此参数用于指定用于对此选项关联的所有稳态范数进行采样的方法。有关稳态范数定义的更多信息，请参见["Steady-state detection," Section 11.8.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-asteadystatedetection)。

设置SAMPLING=PLANE BY PLANE以在每个单元平面穿过出口平面时计算稳态范数。此方法仅适用于具有均匀单元平面的非欧拉分析，单元平面依次通过出口平面。

设置SAMPLING=UNIFORM以在与材料流过一个平均长度单元所需时间定义的间隔计算稳态范数。此间隔在步开始时确定，并在整个步中保持恒定。此方法仅适用于在主要方向上材料流入和流出欧拉边界区域的分析。

### **定义主方向和切割平面位置的数据行：**

**第一行（也是唯一行）：**




