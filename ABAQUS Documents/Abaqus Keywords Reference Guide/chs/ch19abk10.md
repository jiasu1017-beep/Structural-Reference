# *TRACER PARTICLE





### *TRACER PARTICLE定义示踪粒子以在步中追踪材料点位置及结果。

此选项用于定义示踪粒子并将其分配给示踪集，以在步中追踪材料点位置及结果。示踪集名称与[*ELEMENT OUTPUT](ch05abk10.md)和/或[*NODE OUTPUT](ch14abk11.md)选项结合使用，以请求与示踪集名称关联的示踪粒子的输出。

**产品：**Abaqus/Explicit

**类型：**历史数据

**级别：**步

##### **参考：**

- ["输出到输出数据库," Section 4.1.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-out-odboutput)
- [*ELEMENT OUTPUT](ch05abk10.md)
- [*NODE OUTPUT](ch14abk11.md)

### **必需参数：**

TRACER SET

将此参数设置为此示踪粒子将被分配到的示踪集名称。

### **可选参数：**

PARTICLE BIRTH STAGES

将此参数设置为步内示踪粒子出生的数量。如果省略此参数，则在步开始时将发生单次粒子出生。如果此参数的值为*n*大于一，则示踪粒子将在步中以相等的时间间隔*n*次离开其父节点。

### **定义与示踪集关联的示踪粒子的数据行：**

**第一行：**

根据需要重复此数据行。每行最多允许16个条目。





