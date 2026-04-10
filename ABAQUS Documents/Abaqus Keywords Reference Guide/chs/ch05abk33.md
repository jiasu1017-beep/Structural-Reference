# *EULERIAN SECTION









### *EULERIAN SECTION为欧拉单元指定元素属性。

此选项用于定义欧拉连续单元的属性，包括可能占据这些单元的材料列表。

**产品：**Abaqus/Explicit  Abaqus/CAE

**类型：**模型数据

**级别：**部件，部件实例

**Abaqus/CAE：**属性模块

##### **参考：**

- ["欧拉分析，" Abaqus分析用户指南第14.1.1节](../usb/usb-link.md#usb-anl-aeuleriananalysis)
- ["欧拉单元，" Abaqus分析用户指南第32.14.1节](../usb/usb-link.md#usb-elm-eeulerianelem)

### **必需参数：**

ELSET

将此参数设置为包含欧拉单元的单元集名称。

### **可选参数：**

ADVECTION

设置 ADVECTION=SECOND ORDER（默认）以在使用重新网格划分后使用二阶算法重新映射解变量。

设置 ADVECTION=FIRST ORDER 以在使用重新网格划分后使用一阶算法重新映射解变量。

CONTROLS

将此参数设置为截面控制定义的名称（请参见["截面控制，" Abaqus分析用户指南第27.1.4节](../usb/usb-link.md#usb-elm-esectioncontrol)），用于指定非默认沙漏控制公式选项或比例因子。[*SECTION CONTROLS](ch18abk01.md)选项可用于选择沙漏控制和公式的精度阶数。

FLUX LIMIT RATIO

将此参数设置为一个节点在一次增量中允许移动的最大距离与包含该节点的欧拉单元特征长度之间的比值。此参数的值必须为正。默认值为1.0，建议值范围在0.1到1.0之间。

### **定义欧拉单元的数据行：**

**第一行：**

根据需要重复此数据行，以定义可能出现在欧拉截面中的所有材料列表。




