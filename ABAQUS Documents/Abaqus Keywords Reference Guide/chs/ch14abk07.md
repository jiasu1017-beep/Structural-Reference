# *NODAL ENERGY RATE









### *NODAL ENERGY RATE在节点处定义临界能量释放率。

此选项用于在节点基础上定义可变的临界能量释放率。除非在[*FRACTURE CRITERION](ch06abk33.md)、TYPE=VCCT选项或[*FRACTURE CRITERION](ch06abk33.md)、TYPE=FATIGUE选项上包含了NODAL ENERGY RATE参数，否则此选项定义的临界能量释放率数据将被忽略。

**产品：**Abaqus/Standard  Abaqus/Explicit  

**类型：**模型数据  

**级别：**部件、部件实例  

##### **参考：**

- ["裂纹扩展分析，" Abaqus Analysis User's Guide第11.4.3节](../usb/usb-link.md#usb-anl-acrackpropagation)
- [*FRACTURE CRITERION](ch06abk33.md)

### **可选参数：**

GENERATE

包含此参数以在两个边界节点或节点集之间插值临界能量释放率。边界节点或节点集的临界能量释放率必须先前已定义。如果节点集具有不同数量的节点，则忽略较长集合中的额外节点。

INPUT

将此参数设置为包含此选项数据行的备用输入文件名称。如果省略此参数，则假定数据在关键字行之后。

### **省略GENERATE参数时的数据行：**

**第一行：**

根据需要重复此数据行以定义临界能量释放率的变化。

### **包含GENERATE参数时的数据行：**

**第一行：**

根据需要重复此数据行以定义临界能量释放率的变化。