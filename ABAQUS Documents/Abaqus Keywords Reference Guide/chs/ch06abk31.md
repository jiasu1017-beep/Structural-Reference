# *FLUID SECTION





### *FLUID SECTION指定流体和多孔介质单元的单元属性。

此选项用于定义流体单元和多孔介质单元的属性。

**产品：**Abaqus/CFD   Abaqus/CAE   

**类型：**模型数据  

**级别：**部件，部件实例  

**Abaqus/CAE：**属性模块

##### **参考：**

- ["流体（连续体）单元，" Abaqus Analysis User's Guide第28.2.1节](../usb/usb-link.md#usb-elm-ecfdelem)
- ["流体单元库，" Abaqus Analysis User's Guide第28.2.2节](../usb/usb-link.md#usb-elm-ecfdelemlibrary)

### **必需参数：**

ELSET

将此参数设置为包含正为其定义材料行为的单元的单元集名称。

### **可选参数：**

TYPE

对于单相流体流动，设置TYPE=SINGLE FLUID（默认）。

对于涉及多孔介质的传热分析，设置TYPE=POROUS MEDIA。

### **定义单相流体流动的流体单元的数据行：**

**第一行（唯一行）：**

### **定义传热分析的多孔介质单元的数据行：**

**第一行：**

**第二行：**
