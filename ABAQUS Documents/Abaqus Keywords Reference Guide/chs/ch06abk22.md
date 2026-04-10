# *FLUID EXCHANGE ACTIVATION





### *FLUID EXCHANGE ACTIVATION激活流体交换定义。

此选项用于激活两个流体腔之间或流体腔与其环境之间的流体交换定义。

**产品：**Abaqus/Explicit   

**类型：**历史数据  

**级别：**步骤  

##### **参考：**

- ["流体腔定义，" Abaqus Analysis User's Guide第11.5.2节](../usb/usb-link.md#usb-anl-afluidcavities)
- ["流体交换定义，" Abaqus Analysis User's Guide第11.5.3节](../usb/usb-link.md#usb-anl-afluidcavityexchange)
- [*FLUID EXCHANGE](ch06abk21.md)

### **可选参数：**

AMPLITUDE

将此参数设置为定义流体交换幅值乘数的幅值曲线名称。参见["幅值曲线，" Abaqus Analysis User's Guide第34.1.2节](../usb/usb-link.md#usb-prc-pamplitude)。

BLOCKAGE

设置BLOCKAGE=YES以考虑接触表面造成的通风和泄漏面积阻塞。默认值为BLOCKAGE=NO。

DELTA LEAKAGE AREA

将此参数设置为实际表面积与您希望流体泄漏的初始表面积的比率。此实数值应为正数且大于或等于1。用于流体交换的有效表面积是表面实际面积与步骤开始时表面面积之间的差值。

OP

对于现有[*FLUID EXCHANGE ACTIVATION](ch06abk22.md)定义保持不变，将OP=MOD（默认）设置为此选项定义要添加或修改的流体交换激活。

如果应该删除所有当前生效的流体交换激活，则设置OP=NEW。要仅删除选定的流体交换激活，请使用OP=NEW并重新指定要保留的所有流体交换激活。

OUTFLOW ONLY

如果流动仅允许从[*FLUID EXCHANGE](ch06abk21.md)选项中定义的第一个流体腔流向第二个流体腔，则包含此参数。

如果省略此参数，则允许双向流动。[*FLUID EXCHANGE](ch06abk21.md)选项的数据行上定义的参考节点应按适当顺序排列，以获得所需的流动方向。

### **定义流体交换激活的数据行：**

**第一行：**

根据需要重复此数据行。每行最多允许8个条目。
