# *FLUID BEHAVIOR





### *FLUID BEHAVIOR定义流体腔的流体行为。

此选项用于为基于表面的流体腔定义流体行为。

**产品：**Abaqus/Standard   Abaqus/Explicit   Abaqus/CAE   

**类型：**模型数据  

**级别：**模型  

**Abaqus/CAE：**相互作用模块

##### **参考：**

- ["流体腔定义，" Abaqus Analysis User's Guide第11.5.2节](../usb/usb-link.md#usb-anl-afluidcavities)

### **必需参数：**

NAME

将此参数设置为用于引用流体行为的标签。

### **可选参数：**

USER

此参数仅适用于Abaqus/Standard分析。

包含此参数以指定流体，其中流体本构模型在用户子程序[`UFLUID`](../sub/sub-link.md#sub-xsl-ufluid)中定义。

**此选项没有关联的数据行。**
