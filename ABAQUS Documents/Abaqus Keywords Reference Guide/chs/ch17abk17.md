# *RETAINED NODAL DOFS







### *RETAINED NODAL DOFS指定要作为子结构外部保留的自由度。

此选项用于列出要作为子结构外部自由度保留的自由度。它只能用于[*SUBSTRUCTURE GENERATE](ch18abk42.md)分析。

**产品：**Abaqus/Standard  Abaqus/CAE  

**类型：**历史数据  

**级别：**步骤  

**Abaqus/CAE：**载荷模块

##### **参考：**

- ["定义子结构，" Abaqus Analysis User's Guide第10.1.2节](../usb/usb-link.md#usb-anl-asuperelementdef)

### **可选参数：**

SORTED

设置SORTED=NO以防止保留的节点被排序。当使用子结构时，节点的排序将与指定保留节点时使用的排序相同。默认为SORTED=YES，保留的节点按升序数字排序。

### **定义保留自由度的数据行：**

**第一行：**

如果仅给出节点编号或节点集标签，则将保留所有自由度。

根据需要重复此数据行，以列出所有要保留的自由度。
