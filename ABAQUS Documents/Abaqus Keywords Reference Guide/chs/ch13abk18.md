# *MODAL DYNAMIC









### *MODAL DYNAMIC使用模态叠加的动态时间历程分析。

此选项用于使用模态叠加作为线性扰动程序提供动态时间历程响应。

**产品：**Abaqus/Standard  Abaqus/CAE  

**类型：**历史数据  

**级别：**步骤

**Abaqus/CAE：**步骤模块

##### **参考：**

- ["瞬态模态动力学分析，" Abaqus Analysis User's Guide第6.3.7节](../usb/usb-link.md#usb-anl-amodaldynamic)

### **可选参数：**

CONTINUE

设置CONTINUE=NO（默认）以指定此步骤不从前一步骤的结果继承初始条件。在这种情况下，初始位移为零，初始速度取自[*INITIAL CONDITIONS](ch09abk18.md)、TYPE=VELOCITY选项（如果使用了的话）；否则为零。步骤时间从零开始。

设置CONTINUE=YES以指定此步骤从前一个[*MODAL DYNAMIC](ch13abk18.md)步骤或静态扰动步骤结束继承初始条件。如果前一步是[*MODAL DYNAMIC](ch13abk18.md)步骤，则该步骤结束时的速度和位移将作为当前步骤的初始条件。如果前一步是静态扰动步骤，则该步骤的位移将作为当前步骤的初始位移，初始速度取自[*INITIAL CONDITIONS](ch09abk18.md)、TYPE=VELOCITY选项（如果使用了的话）；否则为零。步骤时间从前一个[*MODAL DYNAMIC](ch13abk18.md)或静态扰动步骤继续。

### **瞬态模态动力学分析的数据行：**

**第一行（也是唯一一行）：**