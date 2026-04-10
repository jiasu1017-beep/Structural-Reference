# *ADAPTIVE MESH REFINEMENT





### *ADAPTIVE MESH REFINEMENT在Eulerian域中激活自适应网格细化。

此选项用于在Eulerian域中激活自适应网格细化，并指定该域中的细化标准。

**产品：**Abaqus/Explicit  

**类型：**模型数据

**级别：**模型

##### **参考：**

- ["Eulerian分析，" Abaqus Analysis User's Guide第14.1.1节](../usb/usb-link.md#usb-anl-aeuleriananalysis)
- ["在Eulerian域中定义自适应网格细化，" Abaqus Analysis User's Guide第14.1.4节](../usb/usb-link.md#usb-anl-aeulerianadaptivemeshrefinement)
- [*EULERIAN SECTION](ch05abk33.md)

### **必需参数：**

ELSET

将此参数设置为应用自适应网格细化的元素集名称。

### **可选参数：**

LEVEL

将此参数设置为细化的最大级别数。默认值为1。

COARSENING

设置COARSENING=YES（默认值）以指定一旦细化标准不再满足，可以移除细化。

设置COARSENING=NO以指定即使细化标准不再满足，也不能移除细化。

RATIO

将此参数设置为网格细化期间元素数量最大增加量与指定元素集中原始元素数量的比率。默认值为8.0。

### **定义网格细化中使用的标准的数据行：**

**第一行：**