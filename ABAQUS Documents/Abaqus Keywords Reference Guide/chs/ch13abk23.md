# *MODEL CHANGE









### *MODEL CHANGE移除或重新激活单元和接触对。

此选项用于在分析期间移除或重新激活单元或接触对。

**产品：**Abaqus/Standard  Abaqus/CAE  

**类型：**历史数据  

**级别：**步骤

**Abaqus/CAE：**相互作用模块

##### **参考：**

- ["单元和接触对移除与重新激活，" Abaqus Analysis User's Guide第11.2.1节](../usb/usb-link.md#usb-anl-aelemremovrepl)
- ["在Abaqus/Standard中定义接触对时移除和重新激活接触对"部分，" Abaqus Analysis User's Guide第36.3.1节](../usb/usb-link.md#usb-cni-acontactmodelchange)

### **必需的互斥参数：**

ACTIVATE

在分析期间的任何步骤中包含此参数，以指示可能需要在后续重启分析中移除或添加单元或接触对。

ADD

包含此参数以指示所涉及的单元或接触对在此步骤期间正在被重新激活。

设置ADD=STRAIN FREE（或包含不带值的ADD参数）以为应力/位移单元指定无应变重新激活，或重新激活其他单元或接触对。

设置ADD=WITH STRAIN以指定应力/位移单元随应变重新激活。此选项不适用于接触对。

REMOVE

包含此参数以指示所涉及的单元或接触对在此步骤期间正在被移除。

### **可选参数：**

TYPE

此参数只能与ADD或REMOVE参数一起使用。

设置TYPE=ELEMENT（默认）以移除或重新激活单元。设置TYPE=CONTACT PAIR以移除或重新激活接触对。

### **移除/重新激活单元的数据行（TYPE=ELEMENT）：**

**第一行：**

根据需要重复此数据行。

### **移除/重新激活接触对的数据行（TYPE=CONTACT PAIR）：**

**第一行：**

根据需要重复此数据行。

### **当包含ACTIVATE参数时，此选项不使用数据行。**