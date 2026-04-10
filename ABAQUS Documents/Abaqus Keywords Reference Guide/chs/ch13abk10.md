# *MATRIX CHECK









### *MATRIX CHECK检查生成的刚度矩阵和质量矩阵的质量。

此选项用于检查生成的刚度矩阵和质量矩阵的质量。它只能用于矩阵生成或子结构生成分析。

**产品：**Abaqus/Standard  

**类型：**历史数据  

**级别：**步骤

##### **参考：**

- ["生成矩阵，" Abaqus Analysis User's Guide第10.3.1节](../usb/usb-link.md#usb-anl-amtxgenerationperturbation)
- ["定义子结构，" Abaqus Analysis User's Guide第10.1.2节](../usb/usb-link.md#usb-anl-asuperelementdef)
- [*MATRIX GENERATE](ch13abk12.md)
- [*SUBSTRUCTURE GENERATE](ch18abk42.md)

### **可选参数：**

REFERENCE NODE

将此参数设置为一个现有的节点标签，以定义将用于矩阵检查的坐标系的原点。

**此选项没有关联的数据行。**